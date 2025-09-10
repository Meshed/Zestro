# Elm Component Specifications

*Detailed technical specifications for core Elm components with functional programming patterns*

## A. RecipeEntryForm Component

```elm
-- MODEL
type alias RecipeEntryModel =
    { recipeName : String
    , description : String
    , servings : Int
    , prepTime : Int
    , cookTime : Int
    , ingredients : List Ingredient
    , directions : List String
    , tags : List Tag
    , currentStep : RecipeStep
    , errors : List FormError
    , autoSaveTimer : Time.Posix
    , isDraft : Bool
    }

type alias Ingredient =
    { id : IngredientId
    , quantity : Float
    , unit : Unit
    , name : String
    , suggestions : List String
    }

type RecipeStep = BasicInfo | IngredientsStep | DirectionsStep | TagsStep | Review

-- MESSAGES
type RecipeEntryMsg
    = UpdateRecipeName String
    | UpdateServings String
    | AddIngredient
    | UpdateIngredient Int IngredientMsg
    | RemoveIngredient Int
    | AddDirection
    | UpdateDirection Int String
    | RemoveDirection Int
    | SearchTags String
    | AddTag Tag
    | RemoveTag TagId
    | NextStep
    | PreviousStep
    | AutoSave
    | SaveDraft
    | PublishRecipe
    | Cancel

type IngredientMsg
    = UpdateQuantity String
    | UpdateUnit String  
    | UpdateName String
    | SelectSuggestion String

-- UPDATE FUNCTION ARCHITECTURE
update : RecipeEntryMsg -> RecipeEntryModel -> ( RecipeEntryModel, Cmd RecipeEntryMsg )
update msg model =
    case msg of
        UpdateRecipeName name ->
            ( { model | recipeName = name }
            , Cmd.none
            )
        
        AddIngredient ->
            let
                newIngredient = 
                    { id = generateId ()
                    , quantity = 0
                    , unit = Cup
                    , name = ""
                    , suggestions = []
                    }
            in
            ( { model | ingredients = model.ingredients ++ [ newIngredient ] }
            , focusIngredientField (List.length model.ingredients)
            )
        
        SearchTags query ->
            ( model
            , searchGlobalTags query
            )
        
        AutoSave ->
            if isFormValid model then
                ( { model | autoSaveTimer = Time.now () }
                , saveDraftToServer model
                )
            else
                ( model, Cmd.none )

-- VIEW FUNCTION ARCHITECTURE  
view : RecipeEntryModel -> Html RecipeEntryMsg
view model =
    div [ class "recipe-entry-container" ]
        [ viewProgressIndicator model.currentStep
        , viewCurrentStep model
        , viewNavigationButtons model
        ]

viewCurrentStep : RecipeEntryModel -> Html RecipeEntryMsg
viewCurrentStep model =
    case model.currentStep of
        BasicInfo ->
            viewBasicInfoStep model
            
        IngredientsStep ->
            viewIngredientsStep model
            
        DirectionsStep ->
            viewDirectionsStep model
            
        TagsStep ->
            viewTagsStep model
            
        Review ->
            viewReviewStep model
```

## B. RecipeDeck Component

```elm
-- MODEL  
type alias RecipeDeckModel =
    { recipes : List Recipe
    , oneOffItems : List OneOffItem
    , filters : FilterState
    , selectedItems : List MealPlanItem
    , dragState : DragState
    , planningPeriod : PlanningPeriod
    , coverageTarget : Int
    }

type alias FilterState =
    { searchQuery : String
    , selectedTags : List Tag
    , mealTypes : List MealType
    , showOneOffItems : Bool
    }

type DragState
    = NotDragging
    | DraggingRecipe RecipeId DragPosition
    | DraggingOneOff OneOffId DragPosition

type alias PlanningPeriod =
    { duration : Duration
    , label : String
    , targetMeals : Int
    }

-- MESSAGES
type RecipeDeckMsg
    = UpdateSearch String
    = ToggleTag TagId
    = ToggleMealType MealType
    = StartDrag MealPlanItem DragPosition
    = DragMove DragPosition
    = Drop DropTarget
    = CancelDrag
    = ScaleItem MealPlanItemId Float
    = RemoveFromPlan MealPlanItemId
    = UpdatePlanningPeriod PlanningPeriod
    = GenerateShoppingList

-- UPDATE WITH DRAG & DROP LOGIC
update : RecipeDeckMsg -> RecipeDeckModel -> ( RecipeDeckModel, Cmd RecipeDeckMsg )
update msg model =
    case msg of
        StartDrag item position ->
            ( { model | dragState = DraggingRecipe item.id position }
            , Cmd.none
            )
            
        Drop MealPlanArea ->
            case model.dragState of
                DraggingRecipe recipeId _ ->
                    let
                        recipe = findRecipeById recipeId model.recipes
                        newPlanItem = createMealPlanItem recipe
                    in
                    ( { model 
                        | selectedItems = model.selectedItems ++ [ newPlanItem ]
                        , dragState = NotDragging
                      }
                    , Cmd.none
                    )
                    
                _ ->
                    ( { model | dragState = NotDragging }, Cmd.none )

-- VIEW WITH FUNCTIONAL COMPOSITION
view : RecipeDeckModel -> Html RecipeDeckMsg
view model =
    div [ class "recipe-deck-layout" ]
        [ viewFiltersPanel model.filters
        , viewRecipeCards model
        , viewMealPlanningWorkspace model
        ]

viewRecipeCards : RecipeDeckModel -> Html RecipeDeckMsg  
viewRecipeCards model =
    let
        filteredRecipes = 
            model.recipes
                |> filterBySearch model.filters.searchQuery
                |> filterByTags model.filters.selectedTags
                |> filterByMealTypes model.filters.mealTypes
    in
    div [ class "recipe-cards-grid" ]
        (List.map (viewRecipeCard model.dragState) filteredRecipes)

viewRecipeCard : DragState -> Recipe -> Html RecipeDeckMsg
viewRecipeCard dragState recipe =
    div 
        [ class "recipe-card"
        , classList [ ( "dragging", isDragging recipe.id dragState ) ]
        , draggable "true"
        , onDragStart (StartDrag (RecipeItem recipe) { x = 0, y = 0 })
        ]
        [ div [ class "recipe-card-image" ] [ img [ src recipe.imageUrl ] [] ]
        , div [ class "recipe-card-content" ]
            [ h3 [] [ text recipe.name ]
            , p [] [ text (String.fromInt recipe.servings ++ " servings") ]
            , p [] [ text (String.fromInt recipe.totalTime ++ " min") ]
            , viewScalingControl recipe.id
            ]
        , div [ class "recipe-card-tags" ]
            (List.map viewTag recipe.tags)
        ]
```

## C. ShoppingListMobile Component

```elm
-- MODEL
type alias ShoppingListModel =
    { categories : List ShoppingCategory
    , checkedItems : Set ItemId
    , expandedCategories : Set CategoryId
    , progress : Float
    , swipeState : SwipeState
    }

type alias ShoppingCategory =
    { id : CategoryId
    , name : String
    , icon : String
    , items : List ShoppingItem
    , completedCount : Int
    , totalCount : Int
    }

type SwipeState
    = NoSwipe
    | SwipingItem ItemId SwipeDirection Float

-- MESSAGES
type ShoppingListMsg
    = ToggleItem ItemId
    | SwipeStart ItemId Touch.Coordinates
    | SwipeMove ItemId Touch.Coordinates  
    | SwipeEnd ItemId
    | ToggleCategory CategoryId
    | AddCustomItem String
    | MarkAllDone CategoryId

-- UPDATE WITH SWIPE GESTURES
update : ShoppingListMsg -> ShoppingListModel -> ( ShoppingListModel, Cmd ShoppingListMsg )
update msg model =
    case msg of
        SwipeStart itemId startPos ->
            ( { model | swipeState = SwipingItem itemId SwipeRight 0.0 }
            , Cmd.none
            )
            
        SwipeMove itemId currentPos ->
            case model.swipeState of
                SwipingItem swipeItemId direction _ ->
                    if itemId == swipeItemId then
                        let
                            swipeDistance = calculateSwipeDistance startPos currentPos
                        in
                        if swipeDistance > 100 then
                            -- Complete the check-off action
                            ( { model 
                                | checkedItems = Set.insert itemId model.checkedItems
                                , swipeState = NoSwipe
                              }
                            , Cmd.none
                            )
                        else
                            ( { model | swipeState = SwipingItem itemId direction swipeDistance }
                            , Cmd.none
                            )
                    else
                        ( model, Cmd.none )
                        
                _ ->
                    ( model, Cmd.none )

-- VIEW WITH MOBILE-OPTIMIZED LAYOUT
view : ShoppingListModel -> Html ShoppingListMsg
view model =
    div [ class "shopping-list-mobile" ]
        [ viewHeader model
        , viewProgressBar model.progress
        , viewCategoriesList model
        , viewQuickActions
        ]

viewCategoriesList : ShoppingListModel -> Html ShoppingListMsg
viewCategoriesList model =
    div [ class "categories-list" ]
        (List.map (viewCategory model) model.categories)

viewCategory : ShoppingListModel -> ShoppingCategory -> Html ShoppingListMsg
viewCategory model category =
    div [ class "shopping-category" ]
        [ viewCategoryHeader category
        , if Set.member category.id model.expandedCategories then
            viewCategoryItems model category
          else
            text ""
        ]

viewShoppingItem : Set ItemId -> SwipeState -> ShoppingItem -> Html ShoppingListMsg
viewShoppingItem checkedItems swipeState item =
    let
        isChecked = Set.member item.id checkedItems
        swipeOffset = getSwipeOffset item.id swipeState
    in
    div 
        [ class "shopping-item"
        , classList 
            [ ( "checked", isChecked )
            , ( "swiping", swipeOffset > 0 )
            ]
        , style "transform" ("translateX(" ++ String.fromFloat swipeOffset ++ "px)")
        , onTouchStart (SwipeStart item.id)
        , onTouchMove (SwipeMove item.id) 
        , onTouchEnd (SwipeEnd item.id)
        , onClick (ToggleItem item.id)
        ]
        [ div [ class "item-checkbox" ] 
            [ input [ type_ "checkbox", checked isChecked ] [] ]
        , div [ class "item-content" ]
            [ span [ class "item-name" ] [ text item.name ]
            , span [ class "item-quantity" ] [ text item.quantity ]
            ]
        , div [ class "swipe-action" ] [ text "✓" ]
        ]
```

## D. Global Tag System Component

```elm
-- TAG AUTOCOMPLETE COMPONENT
type alias TagInputModel =
    { query : String
    , suggestions : List Tag
    , selectedTags : List Tag
    , isLoading : Bool
    , showDropdown : Bool
    , highlightedIndex : Int
    }

type TagInputMsg
    = UpdateQuery String
    | SelectTag Tag
    | CreateNewTag String
    | RemoveTag TagId
    = KeyDown KeyCode
    | FocusInput
    | BlurInput

-- TAG NORMALIZATION FUNCTIONS
normalizeTagName : String -> String
normalizeTagName tagName =
    tagName
        |> String.trim
        |> String.toLower
        |> String.split " "
        |> List.map capitalizeFirst
        |> String.join " "

capitalizeFirst : String -> String
capitalizeFirst str =
    case String.uncons str of
        Just ( first, rest ) ->
            String.fromChar (Char.toUpper first) ++ rest
        Nothing ->
            str

-- GLOBAL TAG SEARCH WITH FUZZY MATCHING
searchGlobalTags : String -> Cmd TagInputMsg
searchGlobalTags query =
    let
        normalizedQuery = String.toLower (String.trim query)
    in
    Http.get
        { url = "/api/tags/search?q=" ++ Url.percentEncode normalizedQuery
        , expect = Http.expectJson TagSearchResult (list tagDecoder)
        }

-- VIEW WITH AUTOCOMPLETE DROPDOWN
viewTagInput : TagInputModel -> Html TagInputMsg
viewTagInput model =
    div [ class "tag-input-container" ]
        [ div [ class "selected-tags" ]
            (List.map viewSelectedTag model.selectedTags)
        , div [ class "input-wrapper" ]
            [ input
                [ type_ "text"
                , placeholder "Add tags..."
                , value model.query
                , onInput UpdateQuery
                , onKeyDown KeyDown
                , onFocus FocusInput
                , onBlur BlurInput
                , class "tag-input"
                ]
                []
            , if model.showDropdown && not (List.isEmpty model.suggestions) then
                viewTagSuggestions model
              else
                text ""
            ]
        ]

viewTagSuggestions : TagInputModel -> Html TagInputMsg
viewTagSuggestions model =
    div [ class "tag-suggestions-dropdown" ]
        (List.indexedMap (viewTagSuggestion model.highlightedIndex) model.suggestions
         ++ [ viewCreateNewTagOption model.query ]
        )
```

---

## Implementation Notes

### Functional Programming Patterns
- **Pure Functions**: All view functions are pure, taking model state and returning virtual DOM
- **Immutable Updates**: State changes create new model instances rather than mutating existing ones
- **Composition**: Complex views built by composing smaller, focused view functions
- **Type Safety**: Union types for states (DragState, SwipeState) eliminate invalid state combinations

### Performance Considerations
- **Lazy Evaluation**: Use `Html.Lazy` for expensive view calculations
- **Efficient List Operations**: Prefer `List.map` and pipelines over manual iteration
- **Minimal Re-renders**: Structure models to minimize view update scope

### Mobile Optimizations
- **Touch Events**: Native swipe gesture support for shopping list interactions
- **Large Touch Targets**: Minimum 44px tap areas for mobile accessibility
- **Progressive Enhancement**: Core functionality works without advanced features

These components follow Elm's functional architecture while maintaining practical usability for the Zestro meal planning workflow.