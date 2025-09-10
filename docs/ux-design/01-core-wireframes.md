# Core Wireframes - Main Application Interfaces

*Core user-facing interfaces for the primary Zestro workflow*

## A. Recipe Entry Interface - "Progressive Recipe Builder"

```
┌─────────────────────────────────────────────────────────────────┐
│ 🍳 Add New Recipe                                    [Save Draft] │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│ Progress: ●●●○○ (3/5 Complete)                                  │
│                                                                 │
│ ┌─ Basic Info ─────────────────────────────────────────────────┐ │
│ │ Recipe Name: [Grandma's Famous Meatloaf            ] ✓      │ │
│ │ Serves: [4] people    Prep: [15] min   Cook: [60] min      │ │
│ │ Description: [Optional - what makes this special...   ]     │ │
│ └─────────────────────────────────────────────────────────────┘ │
│                                                                 │
│ ┌─ Ingredients ─────────────────────────────────── [+ Add More] ┐ │
│ │ 1. [2] [lbs] [Ground Beef ▼] [🗑️]                           │ │
│ │     ↪️ Auto-suggest: "Ground Beef (85/15)", "Ground Turkey"   │ │
│ │ 2. [1] [large] [Onion ▼] [🗑️]                               │ │
│ │ 3. [2] [cups] [Breadcrumbs ▼] [🗑️]                          │ │
│ │ 4. [____] [___] [Type ingredient... ▼] [Add to Recipe]       │ │
│ │     ↪️ Recent: Eggs, Milk, Salt, Pepper                       │ │
│ └─────────────────────────────────────────────────────────────┘ │
│                                                                 │
│ ┌─ Directions ──────────────────────────────────── [+ Add Step] ┐ │
│ │ Step 1: [Mix ground beef, onion, and breadcrumbs...     ] ⇅  │ │
│ │ Step 2: [Form into loaf shape and place in pan...      ] ⇅  │ │
│ │ Step 3: [Type next step...                               ]    │ │
│ └─────────────────────────────────────────────────────────────┘ │
│                                                                 │
│ ┌─ Tags ────────────────────────────────────────────────────────┐ │
│ │ [Dinner] [American] [Comfort Food] [Family Favorite] [×]     │ │
│ │ Add tags: [mexican ▼] → Shows: Mexican (2,341 recipes)       │ │
│ │                      → Create "Mexican" as new tag           │ │
│ └─────────────────────────────────────────────────────────────┘ │
│                                                                 │
│ [Cancel] [Save as Draft] [🎯 Publish Recipe]                    │
└─────────────────────────────────────────────────────────────────┘
```

## B. Recipe Deck Interface - "Card-Based Selection"

```
┌─────────────────────────────────────────────────────────────────────────────┐
│ 🍽️ Recipe Deck - Build Your Meal Plan                                       │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│ ┌─ Filters ──────────┐  ┌─ Recipe Cards ─────────────────────────────────┐  │
│ │ 🔍 Search...      │  │                                                 │  │
│ │                   │  │  ┌─────────┐  ┌─────────┐  ┌─────────┐        │  │
│ │ 📋 All Recipes    │  │  │ 🥩      │  │ 🍝      │  │ 🥗      │        │  │
│ │ 🏷️ Tags:          │  │  │Meatloaf │  │ Spaghetti│  │ Caesar │        │  │
│ │   ☑️ Dinner       │  │  │4 servings│  │6 servings│  │Salad  │        │  │
│ │   ☐ Quick        │  │  │60 min    │  │45 min    │  │15 min  │        │  │
│ │   ☐ Mexican      │  │  │[Scale ▼] │  │[Scale ▼] │  │[Scale ▼]│        │  │
│ │                  │  │  └─────────┘  └─────────┘  └─────────┘        │  │
│ │ 🎯 Meal Type:     │  │                                                 │  │
│ │   ☐ Breakfast    │  │  ┌─────────┐  ┌─────────┐  ┌─────────┐        │  │
│ │   ☑️ Lunch        │  │  │ 🍕      │  │ 🌮      │  │ 🍛      │        │  │
│ │   ☑️ Dinner       │  │  │ Pizza   │  │ Tacos   │  │ Stir Fry│        │  │
│ │                  │  │  │ Homemade│  │ Tuesday │  │ Veggie  │        │  │
│ │ 🍿 One-Off Items  │  │  │8 servings│  │4 servings│  │3 servings│       │  │
│ │   Snacks & Drinks│  │  │[Scale ▼] │  │[Scale ▼] │  │[Scale ▼]│        │  │
│ └───────────────────┘  │  └─────────┘  └─────────┘  └─────────┘        │  │
│                        └─────────────────────────────────────────────────┘  │
│                                                                             │
│ ┌─ Meal Planning Workspace ──────────────────────────────────────────────────┐ │
│ │ Planning for: [This Weekend ▼] (2 days, ~6 meals needed)               │ │
│ │                                                                         │ │
│ │ 📥 Drag recipes here to build your meal plan                            │ │
│ │                                                                         │ │
│ │ ┌─ Selected Meals ─────────────────────────────────────────────────────┐ │ │
│ │ │ • Meatloaf (4 servings) [×] [Scale ▼]                               │ │ │
│ │ │ • Spaghetti (6 servings) [×] [Scale ▼]                              │ │ │
│ │ │ • Chips & Salsa (one-off) [×]                                       │ │ │
│ │ └─────────────────────────────────────────────────────────────────────┘ │ │
│ │                                                                         │ │
│ │ Coverage: ████████░░ 80% (4/5 meals planned)                           │ │
│ │ [Add More Meals] [🛒 Generate Shopping List]                            │ │
│ └─────────────────────────────────────────────────────────────────────────┘ │
└─────────────────────────────────────────────────────────────────────────────┘
```

## C. Mobile Shopping List Interface

```
┌─────────────────────────────────┐
│ 🛒 Shopping List                │
│ Weekend Plan - Sept 9-10       │
├─────────────────────────────────┤
│                                 │
│ Progress: ████████░░ 8/10       │
│                                 │
│ 🥩 MEAT & DAIRY        [3/4] ✓  │
│ ☑️ Ground Beef - 3 lbs          │
│ ☑️ Eggs - 1 dozen               │
│ ☑️ Milk - 1 gallon              │
│ ☐ Parmesan Cheese - 8 oz       │
│                                 │
│ 🥬 PRODUCE             [1/2] ✓  │
│ ☑️ Onions - 2 large             │
│ ☐ Tomatoes - 4 medium           │
│                                 │
│ 🥫 PANTRY              [3/3] ✓  │
│ ☑️ Breadcrumbs - 1 container    │
│ ☑️ Pasta - 2 boxes              │
│ ☑️ Marinara Sauce - 2 jars      │
│                                 │
│ 🍿 SNACKS & OTHER      [1/1] ✓  │
│ ☑️ Tortilla Chips - 2 bags      │
│                                 │
│ [Mark All Done] [Add Item]      │
│                                 │
│ Swipe right to check off →     │
└─────────────────────────────────┘
```

---

## Design Notes

### Progressive Recipe Builder
- **Progress indicator** shows completion status to encourage finishing
- **Auto-suggestions** reduce typing friction for common ingredients
- **Drag handles (⇅)** allow reordering of steps
- **Tag system** supports both existing and new tags with usage statistics

### Recipe Deck Interface
- **Card metaphor** makes recipe selection feel like a game
- **Dual filtering system** (search + categorical filters) accommodates different browsing styles
- **Scalable servings** with dropdown for common portion adjustments
- **Drag & drop planning** creates tactile meal planning experience
- **Coverage visualization** shows progress toward complete meal planning

### Mobile Shopping List
- **Category grouping** matches typical store layout
- **Progress bars** provide clear completion feedback at category and overall levels
- **Swipe gestures** enable one-handed shopping
- **Large touch targets** work well in shopping environments (gloves, cart handling)
- **Clear visual hierarchy** separates completed from pending items

These core interfaces form the backbone of the Zestro user experience, designed for efficiency, delight, and practical real-world usage.