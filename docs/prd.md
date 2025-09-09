# Zestro Product Requirements Document (PRD)

## Goals and Background Context

### Goals
- Transform tedious weekly grocery shopping planning into a streamlined, automated experience through intelligent shopping list generation
- Enable users to build personal recipe libraries with full ownership and easy scaling capabilities
- Provide flexible meal planning using "Recipe Deck + Meal Inventory" interface that focuses on coverage over rigid scheduling
- Automate ingredient aggregation across multiple recipes with accurate quantity calculations
- Integrate recipe ingredients with non-recipe items (snacks, drinks, frozen meals) in unified shopping lists
- Achieve >90% recipe entry completion rate with <5 minute entry time per recipe
- Establish foundation for future community-driven recipe sharing with one-way cloning capability

### Background Context

Weekly grocery shopping planning represents a universal pain point for home cooks, consuming 30-60 minutes weekly in a process fraught with errors and incomplete results. The typical workflow of finding recipes, extracting ingredients, manually combining quantities, and remembering non-recipe items leads to under-buying (requiring additional store trips), over-buying (food waste), and significant mental load.

Existing meal planning solutions focus on recipe discovery and meal suggestions rather than solving the core shopping list generation problem. They typically lack proper ingredient quantity aggregation, don't handle mixed recipe/non-recipe shopping needs, and force users into rigid calendar-based meal scheduling. Zestro addresses this gap by prioritizing shopping list accuracy and completeness while maintaining user control over their personal recipe collections through a coverage-based planning approach.

### Change Log
| Date | Version | Description | Author |
|------|---------|-------------|--------|
| 2025-09-09 | v1.0 | Initial PRD creation from Project Brief | John (PM Agent) |

## Requirements

### Functional Requirements

**FR1:** Users can create and edit personal recipes with complete metadata (name, ingredients with quantities and units, directions, serving size, prep/cook time, tags) through an intuitive web interface

**FR2:** The system provides a global shared tag library with autocomplete functionality, where all user-created tags become available to other users while preventing tag proliferation

**FR3:** Users can scale recipe ingredient quantities for different serving sizes (doubling, tripling, halving, custom scaling factors) during meal planning

**FR4:** The Recipe Deck interface allows users to select recipes for meal plans using a card-based metaphor without rigid calendar scheduling

**FR5:** The Meal Inventory interface displays planned meals with coverage view for any time period (weekend to monthly)

**FR6:** Users can add one-off non-recipe items (snacks, drinks, frozen meals) to meal plans with the same tagging system as recipes

**FR7:** The system automatically aggregates ingredients across multiple recipes with accurate quantity summing (e.g., 1 lb + 2 lbs ground beef = 3 lbs)

**FR8:** Generated shopping lists combine recipe ingredients and one-off items into a unified, mobile-friendly format

**FR9:** Users can search and filter their recipe library by tags, categories, and text content

**FR10:** The system supports secure user authentication with account management and data persistence

**FR11:** The system provides global shared ingredient and unit libraries with autocomplete functionality, where all user-created ingredients and units become available to other users

**FR12:** One-off items use identical card-based interface and interaction patterns as recipes while maintaining separate organizational collections

### Non-Functional Requirements

**NFR1:** Recipe entry must complete in under 5 minutes with >90% completion rate to ensure user adoption

**NFR2:** Application must load in under 3 seconds to maintain user engagement

**NFR3:** Shopping list generation must complete in under 10 seconds for typical meal plans containing up to 20 recipes

**NFR4:** Mobile shopping list view must function properly on standard smartphones with responsive design

**NFR5:** The system must maintain functional programming principles throughout the entire stack (Elm frontend, F# backend)

**NFR6:** Data must be encrypted at rest and in transit with secure password hashing and session management

**NFR7:** The platform must support PostgreSQL as the primary database with normalized relational structure

## User Interface Design Goals

### Overall UX Vision
Zestro embodies a friendly, helpful, and approachable design philosophy that makes meal planning feel effortless rather than overwhelming. The interface prioritizes task completion speed while maintaining visual appeal through Bulma's modern, playful, and colorful design system. Users should feel confident and in control throughout their workflow, from recipe entry through shopping list generation, with clear visual feedback and intuitive navigation patterns that reduce cognitive load.

### Key Interaction Paradigms
- **Recipe Deck Metaphor:** Card-based interface for recipe selection that feels familiar and tactile, similar to browsing through a personal recipe box
- **Drag-and-Drop Planning:** Intuitive recipe selection through dragging cards into meal planning areas
- **Progressive Disclosure:** Complex features revealed progressively to maintain simplicity while providing power when needed
- **Autocomplete-First:** Tag entry and ingredient input prioritize autocomplete suggestions to reduce typing and ensure consistency
- **Mobile-First Shopping:** Shopping lists optimized for one-handed mobile usage with large touch targets and clear visual hierarchy
- **Unified Card Metaphor:** Both recipes and one-off items represented as cards with identical interaction patterns (drag-and-drop, selection, scaling for recipes)
- **Visual Distinction Without Behavioral Change:** One-off items use subtle visual differentiation (background tint, border style, or icon) while maintaining identical drag-and-drop and selection behaviors
- **Consistent Tagging Experience:** Both recipes and one-off items use the same global tag system and autocomplete functionality
- **Dual Collection Management:** Users can browse, search, and organize both collections using identical interface patterns

### Core Screens and Views
- **Recipe Library Dashboard:** Main hub with two distinct sections: "My Recipes" collection and "One-Off Items" collection, both using identical card-based layouts
- **Recipe Entry Form:** Streamlined form for full recipes with ingredients, directions, and metadata
- **One-Off Item Entry Form:** Simplified form for standalone items (name, tags, notes, quantity) following same visual design patterns
- **Recipe Deck Planning Interface:** Unified card-based workspace where both recipes and one-off items appear as draggable cards with visual differentiation (e.g., subtle background color variation or border styling)
- **Meal Inventory View:** Coverage-focused display showing both recipes and one-off items in planned meals with consistent card representation
- **Shopping List Generator:** Treats ingredients from recipes and one-off items equivalently in the unified shopping list
- **Recipe Detail View:** Comprehensive recipe display with scaling controls and edit capabilities
- **User Profile Settings:** Account management with preferences for units, dietary restrictions, and interface options

### Accessibility: WCAG AA
Full WCAG 2.1 AA compliance ensuring keyboard navigation, screen reader compatibility, sufficient color contrast ratios, and alternative text for all visual elements. This supports users with disabilities while improving overall usability for all users.

### Branding
Clean, modern design leveraging Bulma's colorful and playful aesthetic to create an approachable, non-intimidating meal planning experience. Color palette should evoke freshness and appetite appeal while maintaining excellent readability. Typography should be friendly yet professional, supporting the "helpful kitchen assistant" brand personality rather than corporate or sterile design approaches.

### Target Device and Platforms: Web Responsive
Primary web application with fully responsive design optimized for desktop recipe entry and mobile shopping list usage. Interface adapts seamlessly from large desktop screens (recipe management) to smartphone displays (grocery shopping) with consistent functionality across all viewport sizes.

## Technical Assumptions

### Repository Structure: Monorepo
Single repository containing both Elm frontend and F# backend with clear separation and shared configuration. This approach supports the functional programming philosophy while enabling coordinated development and deployment of both application tiers.

### Service Architecture
**Functional Web Application Design:** Single-page application (SPA) with Elm frontend consuming a functional F# Web API backend. Architecture follows Domain-Driven Design principles with functional core and imperative shell pattern. The backend implements RESTful endpoints using pure functional domain logic separated from infrastructure concerns, while the frontend follows Elm Architecture with unidirectional data flow and immutable state management.

### Testing Requirements
**Unit + Integration Testing:** Comprehensive testing pyramid with heavy emphasis on pure function testing in F# domain logic and Elm model/update function testing. Integration tests focus on API contract validation and database interaction verification. Property-based testing leveraged where appropriate for functional code validation. Manual testing convenience methods provided for UI workflow validation during development.

### Additional Technical Assumptions and Requests

**Frontend Technology Stack:**
- **Elm Language:** Pure functional programming with strong typing, zero runtime exceptions, and enforced Elm Architecture pattern
- **Bulma CSS Framework:** Modern, responsive, colorful design system providing consistent component library
- **Build Tooling:** Elm standard toolchain with WebPack integration for asset management

**Backend Technology Stack:**
- **F# Language:** Functional-first programming with strong typing, pattern matching, and seamless .NET ecosystem integration
- **Web Framework:** F# web framework (ASP.NET Core with functional patterns or Giraffe) for RESTful API development
- **Authentication:** Secure JWT-based authentication with F# functional validation pipeline

**Database Design:**
- **PostgreSQL Primary Database:** Relational database with excellent F# integration through type providers or functional query libraries
- **Schema Design:** Normalized structure optimized for recipe/meal plan/shopping list relationships with strong typing enforcement
- **Data Access:** Functional database access layer using pure functions for query composition and immutable data structures

**Development Environment:**
- **Containerization:** Docker development environment for consistent local development and easy deployment
- **Version Control:** Git with conventional commit standards and functional code organization patterns
- **CI/CD Pipeline:** Automated testing and deployment pipeline supporting functional programming verification

**Performance and Scalability:**
- **Frontend Optimization:** Elm's compile-time optimizations with lazy loading for recipe collections
- **Backend Performance:** F# async workflows for non-blocking I/O operations with functional composition
- **Database Performance:** Indexed queries optimized for recipe search and shopping list aggregation operations

## Epic List

**Epic 1: Foundation & Authentication**
Establish project infrastructure, user authentication, and core application framework with basic health check and user account management functionality.

**Epic 2: Recipe Entry & Management**
Build the complete recipe creation, editing, and basic library management system optimized for the <5 minute entry target.

**Epic 3: Global Tag System**
Implement the shared tag library with autocomplete functionality that creates network effects across all users for both recipes and one-off items.

**Epic 4: One-Off Item Management**
Create the one-off item system with card-based interface that matches recipe interaction patterns while maintaining separate collections.

**Epic 5: Recipe Library Organization**
Develop search, filtering, browsing, and organization capabilities for the recipe library using the global tag system.

**Epic 6: Recipe Deck Planning Interface**
Build the drag-and-drop meal planning workspace where users select recipes and one-off items using card metaphors.

**Epic 7: Meal Inventory & Coverage Management**
Implement the coverage-based meal planning view that shows planned meals over flexible time periods without rigid calendar constraints.

**Epic 8: Shopping List Generation Engine**
Develop the ingredient aggregation algorithms and shopping list creation functionality that combines recipes and one-off items.

**Epic 9: Mobile Shopping Experience**
Create the mobile-optimized shopping list interface with responsive design and touch-friendly interactions for grocery store usage.

## Epic 1: Foundation & Authentication

**Epic Goal:** Establish project infrastructure using pure functional programming principles throughout the stack. Build Elm frontend with Elm Architecture, F# backend with functional composition, and PostgreSQL access through pure functions with dependency injection at composition root.

### Story 1.1: Project Infrastructure Setup
As a developer,  
I want the basic project structure with functional programming principles,  
so that I have a working development environment that strictly adheres to FP practices.

#### Acceptance Criteria
1. Monorepo structure with clear functional module organization
2. Elm project with pure functions, immutable state, and Elm Architecture pattern
3. F# web API using functional composition with no classes or OO patterns
4. **All business logic implemented as pure functions with explicit dependencies**
5. Composition root pattern for dependency injection without IoC containers
6. Build system configured for functional code compilation and optimization

### Story 1.2: Functional Database Access Layer
As a developer,  
I want database access through pure functional patterns,  
so that all database operations are composable, testable, and side-effect explicit.

#### Acceptance Criteria
1. PostgreSQL database with functional schema design (normalized, immutable-friendly)
2. **Database functions as pure functions taking connection as explicit parameter**
3. **Function modules (UserDb, AuthDb) with no state or classes**
4. Database operations using F# async workflows and Result types for error handling
5. **Composition root dependency injection for database connections**
6. **Test database setup with function composition for different connection contexts**

### Story 1.3: Functional Authentication System
As a user,  
I want secure authentication implemented through pure functional workflows,  
so that I can access the application with authentication logic that's predictable and testable.

#### Acceptance Criteria
1. **Authentication workflows as pure function compositions**
2. **Password hashing and validation as pure functions**
3. **JWT token generation/validation as pure functions with explicit dependencies**
4. Elm authentication state management through Model/Update/View pattern
5. **Authentication pipeline composition without middleware classes**
6. **Session management through functional state transformations**

### Story 1.4: Functional Application Health & Monitoring
As a system administrator,  
I want health monitoring through functional composition,  
so that system health is determined through pure function evaluation.

#### Acceptance Criteria
1. **Health check functions composed from database and system checks**
2. **Error handling through Result/Option types with no exceptions**
3. **Logging as pure functions with explicit side-effect handling**
4. **Application startup as function composition with dependency injection**
5. **Performance measurement functions with immutable data collection**
6. **System state queries as pure functions returning health status**

### Story 1.5: Functional UI Foundation
As a user,  
I want application layout built with functional UI patterns,  
so that the interface is predictable, maintainable, and follows functional principles.

#### Acceptance Criteria
1. **Elm View functions as pure functions of Model state**
2. **Navigation state managed through Elm Architecture with immutable routing**
3. **All UI state transformations through Update functions**
4. **Bulma CSS integration without imperative DOM manipulation**
5. **Mobile responsiveness through pure CSS and functional view composition**
6. **Authentication UI state managed through functional state machines**

### Story 1.6: Functional Testing Infrastructure
As a developer,  
I want testing infrastructure using functional patterns,  
so that I can test pure functions and composed behaviors without mocking frameworks.

#### Acceptance Criteria
1. **Test functions as pure functions with explicit test data parameters**
2. **Database testing through function composition with test connection parameters**
3. **Property-based testing for pure functions using FsCheck**
4. **Test data creation through pure builder functions**
5. **Integration testing through function composition with test environments**
6. **No mocking frameworks - testing through function parameterization**

## Epic 2: Recipe Entry & Management

**Epic Goal:** Implement complete recipe creation and management with global shared ingredient and unit systems that create network effects across all users, similar to the tag system approach.

### Story 2.1: Recipe Data Model & Global Systems
As a developer,  
I want immutable recipe data structures with global ingredient and unit systems,  
so that all users benefit from collective ingredient and unit libraries while maintaining data consistency.

#### Acceptance Criteria
1. **Recipe type with immutable fields referencing global ingredient and unit systems**
2. **Global Ingredient system with autocomplete functionality where users can select existing or add new ingredients**
3. **Global Unit system with autocomplete where users can select existing units (cups, tablespoons, pounds, etc.) or add custom units**
4. **Ingredient reference type containing quantity, global unit ID, and global ingredient ID**
5. **Pure validation functions for recipe data, quantities, and unit/ingredient consistency**
6. **Database schema with global ingredients table, global units table, and recipe_ingredients junction**

### Story 2.2: Ingredient & Unit Autocomplete System
As a user,  
I want to quickly find existing ingredients and units or add new ones seamlessly,  
so that recipe entry is fast while building the collective ingredient and unit libraries.

#### Acceptance Criteria
1. **Case-insensitive ingredient autocomplete with fuzzy matching against global ingredient library**
2. **Case-insensitive unit autocomplete with normalization handling**
3. **Ingredient normalization: "sea salt", "Sea Salt", "SEA SALT" all recognized as same ingredient**
4. **Unit normalization: "cup", "Cup", "CUP" all recognized as same unit**
5. **Display standardization: all ingredients and units stored and displayed in Title Case (e.g., "Sea Salt", "Olive Oil", "Cup", "Tablespoon")**
6. **Duplicate prevention with case-insensitive matching before allowing new ingredient/unit creation**

### Story 2.3: Recipe Entry Form with Seamless Global Systems
As a user,  
I want an intuitive recipe entry form with smart ingredient and unit suggestions,  
so that I can add recipes quickly while contributing to and benefiting from the collective libraries.

#### Acceptance Criteria
1. **Elm form with ingredient input fields featuring autocomplete that never navigates away from recipe**
2. **Inline ingredient creation: when user types non-existing ingredient, "Add '[ingredient name]' as new ingredient" option appears in autocomplete dropdown**
3. **Inline unit creation: when user types non-existing unit, "Add '[unit name]' as new unit" option appears in unit autocomplete dropdown**
4. **One-click creation: selecting "Add new..." option creates the ingredient/unit instantly and continues recipe entry without page change**
5. **Real-time availability: newly created ingredients/units immediately appear in current recipe form and become available for subsequent ingredient entries**
6. **Case-insensitive matching: typing "sea salt" shows existing "Sea Salt" in autocomplete if it exists**
7. **Automatic normalization: when creating new ingredient/unit, input is converted to Title Case for storage and display**
8. **Smart suggestions: autocomplete shows normalized matches even when user types in different case**

### Story 2.4: Global Ingredient & Unit Management Functions
As a developer,  
I want pure functional systems for managing global ingredients and units,  
so that the shared libraries grow organically while maintaining data quality.

#### Acceptance Criteria
1. **Pure functions for ingredient search, creation, and retrieval from global library**
2. **Pure functions for unit search, creation, and retrieval from global library**
3. **Duplicate detection functions using fuzzy matching algorithms**
4. **Case normalization functions converting input to Title Case using functional string transformations**
5. **Case-insensitive search functions using lowercase comparison for matching**
6. **Display formatting functions ensuring consistent Title Case presentation**

### Story 2.5: Recipe Storage with Global References
As a user,  
I want my recipes saved with proper ingredient and unit references,  
so that my recipes benefit from improvements to the global ingredient and unit libraries.

#### Acceptance Criteria
1. **Recipe persistence functions storing global ingredient and unit references, not local copies**
2. **Recipe retrieval functions joining with global ingredient and unit data**
3. **Recipe display showing current ingredient and unit names from global libraries**
4. **Migration handling when global ingredients or units are updated or normalized**
5. **User recipe data integrity maintained despite global library changes**
6. **Efficient database queries for recipe display with ingredient/unit join operations**

### Story 2.6: Recipe Scaling with Unit Conversion
As a user,  
I want to scale recipes with automatic unit conversions,  
so that I can adjust serving sizes and see results in appropriate measurement units.

#### Acceptance Criteria
1. **Pure scaling functions handling mathematical quantity transformations**
2. **Unit conversion system supporting common measurement conversions (cups to tablespoons, pounds to ounces, etc.)**
3. **Smart unit conversion during scaling (e.g., 4 tablespoons becomes 1/4 cup)**
4. **Scaling preview showing converted quantities in most appropriate units**
5. **Unit conversion database with common conversion factors**
6. **Custom unit handling for unconventional measurements users might create**

## Epic 3: Global Tag System

**Epic Goal:** Implement the shared tag library system with autocomplete functionality that enables flexible recipe and one-off item categorization while creating network effects across all users. Establish the foundation for hierarchical categories, temporal tags, and mood-based classifications.

### Story 3.1: Tag Data Model & Normalization System
As a developer,  
I want immutable tag data structures with case-insensitive normalization,  
so that tags are consistent, searchable, and follow the same normalization patterns as ingredients and units.

#### Acceptance Criteria
1. **Tag type definition with immutable fields (id, name, createdBy, createdDate)**
2. **Case-insensitive tag matching with Title Case display normalization**
3. **Tag validation functions preventing empty, duplicate, or malformed tags**
4. **Tag search functions using functional list operations with fuzzy matching**
5. **Database schema with global tags table and case-insensitive indexing**
6. **Pure functions for tag creation, retrieval, and normalization using functional composition**

### Story 3.2: Tag Autocomplete & Creation System
As a user,  
I want to quickly find existing tags or create new ones seamlessly,  
so that I can organize my recipes consistently while contributing to the collective tag library.

#### Acceptance Criteria
1. **Tag autocomplete with fuzzy matching against global tag library**
2. **Case-insensitive tag search showing normalized results ("mexican" matches "Mexican")**
3. **Inline tag creation: "Add '[tag name]' as new tag" option in autocomplete dropdown**
4. **Instant tag creation that immediately becomes available to all users**
5. **Duplicate prevention with smart suggestions for similar existing tags**
6. **Tag normalization to Title Case for consistent display and storage**

### Story 3.3: Multi-Tag Selection Interface
As a user,  
I want to add multiple tags to recipes using an intuitive interface,  
so that I can categorize recipes across multiple dimensions (cuisine, meal type, difficulty, etc.).

#### Acceptance Criteria
1. **Multi-select tag interface allowing addition of multiple tags per recipe**
2. **Tag removal functionality with visual feedback**
3. **Real-time tag filtering as user types in tag input field**
4. **Visual tag display showing selected tags as removable chips/badges**
5. **Tag limit handling (optional maximum tags per recipe with user feedback)**
6. **Mobile-responsive tag selection interface optimized for touch interactions**

### Story 3.4: Tag Management Functions
As a developer,  
I want pure functional tag management operations,  
so that tag operations are composable, testable, and maintain data consistency.

#### Acceptance Criteria
1. **Pure functions for tag association with recipes and one-off items**
2. **Tag retrieval functions for recipe filtering and organization**
3. **Tag popularity functions counting usage across all users**
4. **Tag suggestion functions based on recipe content or similar recipes**
5. **Result types for tag operation success/failure handling**
6. **Functional composition for complex tag operations (bulk tagging, tag migration)**

### Story 3.5: Tag-Based Organization Foundation
As a user,  
I want my tags to enable future recipe organization and filtering,  
so that the tagging effort provides immediate value in recipe discovery.

#### Acceptance Criteria
1. **Recipe-tag association storage in database with proper foreign key relationships**
2. **Tag display on recipe cards showing associated tags**
3. **Basic tag-based recipe filtering functionality (single tag filter)**
4. **Tag usage statistics for recipes (which tags are most commonly used)**
5. **Tag validation ensuring recipes maintain tag associations properly**
6. **Foundation for advanced tag-based search and filtering in future epics**

### Story 3.6: One-Off Item Tag Integration
As a user,  
I want one-off items to use the same tag system as recipes,  
so that all my meal planning items can be organized consistently using the same categorization system.

#### Acceptance Criteria
1. **One-off items use identical tag selection interface as recipes**
2. **Shared tag autocomplete functionality across recipes and one-off items**
3. **Tag associations work identically for both recipes and one-off items**
4. **Visual consistency between recipe tags and one-off item tags in UI**
5. **Database schema supporting tag associations for both entity types**
6. **Tag filtering works across both recipes and one-off items in future epic functionality**

## Epic 4: One-Off Item Management

**Epic Goal:** Create the one-off item system with card-based interface that provides identical interaction patterns to recipes while maintaining separate collections. Enable users to add non-recipe items (snacks, drinks, frozen meals) to their meal planning with the same tagging and organization capabilities as recipes.

### Story 4.1: One-Off Item Data Model
As a developer,  
I want immutable one-off item data structures that complement recipes,  
so that one-off items can be managed consistently while remaining organizationally separate from recipes.

#### Acceptance Criteria
1. **OneOffItem type definition with immutable fields (id, name, description, tags, quantity, notes, createdBy, createdDate)**
2. **Simplified data model compared to recipes (no ingredients list, directions, or cooking times)**
3. **Optional quantity field for items that have measurable amounts (e.g., "2 bottles of wine", "1 bag of chips")**
4. **Tag association using same global tag system as recipes**
5. **Validation functions ensuring one-off item completeness and consistency**
6. **Database schema with separate one_off_items table maintaining distinct collection**

### Story 4.2: One-Off Item Entry Form
As a user,  
I want to quickly add one-off items to my collection,  
so that I can plan for non-recipe items like snacks, drinks, and frozen meals alongside my recipes.

#### Acceptance Criteria
1. **Streamlined Elm form with fewer fields than recipe entry (name, description, quantity, tags, notes)**
2. **Same tag autocomplete functionality as recipes using shared global tag system**
3. **Quick entry workflow optimized for simple items (target <2 minutes per item)**
4. **Optional fields clearly marked to reduce entry friction**
5. **Form validation ensuring required fields are completed**
6. **Mobile-responsive design matching recipe entry form styling**

### Story 4.3: One-Off Item Card Interface
As a user,  
I want one-off items displayed as cards identical to recipe cards,  
so that I have consistent interaction patterns across all my meal planning content.

#### Acceptance Criteria
1. **One-off item cards using identical visual layout as recipe cards**
2. **Visual distinction through subtle background color, border style, or icon difference**
3. **Card content showing name, description, tags, and quantity in consistent format**
4. **Same drag-and-drop interaction capabilities as recipe cards (for future meal planning)**
5. **Consistent hover states, selection states, and interaction feedback**
6. **Mobile touch interactions identical to recipe cards**

### Story 4.4: One-Off Item Collection Management
As a user,  
I want to manage my one-off items in a separate collection from recipes,  
so that my recipes and one-off items remain organizationally distinct while sharing interaction patterns.

#### Acceptance Criteria
1. **Separate "One-Off Items" section in main navigation distinct from "My Recipes"**
2. **One-off item library display using same grid layout as recipe library**
3. **Identical sorting options (name, creation date) using functional list operations**
4. **Tag-based filtering functionality consistent with recipe filtering**
5. **Search functionality across one-off item names, descriptions, and tags**
6. **Edit and delete operations with same workflow patterns as recipe management**

### Story 4.5: One-Off Item Storage & Retrieval
As a developer,  
I want pure functional operations for one-off item persistence,  
so that one-off items follow the same functional patterns as recipe management.

#### Acceptance Criteria
1. **Pure functions for one-off item creation, update, and retrieval**
2. **Database operations using same functional composition patterns as recipes**
3. **Result types for error handling in one-off item operations**
4. **User association functions linking one-off items to authenticated users**
5. **Tag association functions using shared tag management system**
6. **Efficient queries for one-off item retrieval with tag joins**

### Story 4.6: Unified Card Interface Foundation
As a user,  
I want recipes and one-off items to work together seamlessly in future meal planning,  
so that I can plan complete meals including both recipes and non-recipe items.

#### Acceptance Criteria
1. **Common card interface traits shared between recipes and one-off items**
2. **Unified drag-and-drop behavior foundation for meal planning workflows**
3. **Consistent selection and interaction states across both card types**
4. **Tag filtering that can work across both recipes and one-off items**
5. **Search functionality that can span both collections when needed**
6. **Foundation for unified meal planning interface in subsequent epics**

## Epic 5: Recipe Library Organization

**Epic Goal:** Develop comprehensive search, filtering, browsing, and organization capabilities for the recipe library using the global tag system. Enable users to efficiently discover and organize their recipes through multiple access patterns and provide foundation for effective meal planning workflows.

### Story 5.1: Advanced Recipe Search
As a user,  
I want to search my recipes by name, ingredients, and tags,  
so that I can quickly find specific recipes or discover recipes based on what I want to cook or ingredients I have available.

#### Acceptance Criteria
1. **Multi-field search functionality across recipe names, ingredient names, directions, and tags**
2. **Real-time search results updating as user types using functional debouncing**
3. **Search highlighting showing matched terms in recipe cards**
4. **Case-insensitive search using same normalization functions as ingredients/units/tags**
5. **Search result ranking prioritizing exact matches, then partial matches, then tag matches**
6. **Empty state handling with helpful suggestions when no recipes match search criteria**

### Story 5.2: Tag-Based Recipe Filtering
As a user,  
I want to filter my recipes by multiple tags simultaneously,  
so that I can find recipes that match specific criteria like "Mexican AND Vegetarian AND Quick" or browse by single categories.

#### Acceptance Criteria
1. **Multi-select tag filtering with AND/OR logic options**
2. **Tag filter interface showing available tags with usage counts**
3. **Active filter display with easy removal of individual filter tags**
4. **Filter results updating in real-time using functional list operations**
5. **Filter persistence during session for consistent browsing experience**
6. **Combination of search and tag filtering working together seamlessly**

### Story 5.3: Recipe Library Sorting & Views
As a user,  
I want multiple ways to sort and view my recipe collection,  
so that I can organize my recipes by different criteria depending on my current needs.

#### Acceptance Criteria
1. **Multiple sorting options: alphabetical, creation date, last modified, cooking time, prep time**
2. **Sort direction toggles (ascending/descending) for all sort criteria**
3. **View options: grid view (cards) and list view for different browsing preferences**
4. **Sort and view preferences persisted across sessions**
5. **Efficient sorting using functional list operations without UI blocking**
6. **Mobile-optimized sorting interface with touch-friendly controls**

### Story 5.4: Recipe Organization Collections
As a user,  
I want to create custom collections or favorites within my recipe library,  
so that I can group recipes for special occasions, meal types, or personal preferences.

#### Acceptance Criteria
1. **Recipe favoriting functionality with star/heart toggle on recipe cards**
2. **"Favorites" collection automatically created and maintained**
3. **Recently added recipes collection showing newest recipes**
4. **Recently viewed recipes collection tracking user browsing history**
5. **Collection navigation integrated into recipe library interface**
6. **Collection filtering combined with search and tag filtering capabilities**

### Story 5.5: Personal Recipe Rediscovery
As a user,  
I want to rediscover recipes from my own collection that I haven't used recently,  
so that I can find variety in my meal planning using recipes I already own and have prepared before.

#### Acceptance Criteria
1. **"Haven't used lately" feature highlighting user's own recipes not selected for meal plans recently**
2. **"Forgotten favorites" showing user's previously favorited recipes that haven't been used in extended periods**
3. **Recipe usage history tracking when recipes are added to meal plans (not external recommendations)**
4. **"Random from my collection" discovery featuring only user's personal recipes**
5. **Recipe rotation suggestions ensuring variety within user's personal recipe library**
6. **All discovery algorithms operate exclusively on user's personal recipe collection using functional programming patterns**

### Story 5.6: Advanced Recipe Library Interface
As a user,  
I want a powerful but intuitive recipe library interface,  
so that managing large recipe collections feels organized and effortless.

#### Acceptance Criteria
1. **Advanced search and filter combination interface with clear visual hierarchy**
2. **Bulk operations for tagging multiple recipes or adding to collections**
3. **Recipe library statistics: total recipes, most used tags, average cooking times**
4. **Export functionality for recipe backup or sharing (future enhancement foundation)**
5. **Recipe library dashboard showing recent activity and quick access to common actions**
6. **Keyboard shortcuts for power users to navigate and search efficiently**

## Epic 6: Recipe Deck Planning Interface

**Epic Goal:** Build the core drag-and-drop meal planning workspace where users select recipes and one-off items using card metaphors. Implement the "Recipe Deck" interface that enables flexible meal planning without rigid calendar constraints, supporting the coverage-based planning approach that differentiates Zestro from calendar-based meal planning apps.

### Story 6.1: Recipe Deck Interface Foundation
As a user,  
I want a card-based interface for browsing my recipes and one-off items during meal planning,  
so that I can visually select items for meal plans using familiar, tactile interaction patterns.

#### Acceptance Criteria
1. **Recipe Deck view displaying both recipes and one-off items as draggable cards**
2. **Visual distinction between recipe cards and one-off item cards while maintaining interaction consistency**
3. **Card filtering integrated with existing search and tag functionality from Epic 5**
4. **Infinite scroll or pagination for large recipe collections**
5. **Card sorting options available within the deck interface**
6. **Mobile-responsive card layout optimized for touch interactions**

### Story 6.2: Drag-and-Drop Meal Planning
As a user,  
I want to drag recipe and one-off item cards into meal planning areas,  
so that I can intuitively build meal plans through direct manipulation without complex forms.

#### Acceptance Criteria
1. **Drag-and-drop functionality from Recipe Deck to meal planning zones**
2. **Visual feedback during drag operations (card highlighting, drop zone indicators)**
3. **Snap-to-grid behavior for organized meal plan layouts**
4. **Touch-friendly drag interactions optimized for mobile devices**
5. **Drag cancellation functionality (drag back to deck or ESC key)**
6. **Consistent drag behavior between recipes and one-off items**

### Story 6.3: Flexible Meal Planning Zones
As a user,  
I want flexible planning areas that aren't tied to specific dates or rigid schedules,  
so that I can plan meal coverage for any time period without calendar constraints.

#### Acceptance Criteria
1. **Customizable planning zones that can represent any time period (weekend, week, month)**
2. **Zone labeling functionality for user-defined periods ("Super Bowl Weekend", "Vacation Week")**
3. **Multiple meal planning sessions can be created and saved simultaneously**
4. **Zone resizing and organization to accommodate different planning scales**
5. **Visual meal plan organization without forced calendar grid structure**
6. **Planning zone persistence across user sessions**

### Story 6.4: Meal Plan State Management
As a developer,  
I want pure functional state management for meal planning operations,  
so that meal plan modifications are predictable, undoable, and maintain data consistency.

#### Acceptance Criteria
1. **Immutable meal plan data structures using Elm Model patterns**
2. **Pure functions for adding/removing items from meal plans**
3. **Undo/redo functionality for meal planning operations using functional state history**
4. **Recipe scaling integration allowing quantity adjustments during meal planning**
5. **Meal plan validation ensuring data consistency**
6. **State persistence functions for saving meal plans to database**

### Story 6.5: Meal Plan Management
As a user,  
I want to manage my current meal plan with option to save for future reuse,  
so that I can focus on my immediate meal planning needs while optionally preserving successful plans for later use.

#### Acceptance Criteria
1. **Single active meal plan focus - one current meal planning session**
2. **Meal plan naming functionality for saving completed plans**
3. **Meal plan save/reuse functionality allowing users to start from a previously successful plan**
4. **Clear meal plan completion workflow leading directly to shopping list generation**
5. **Simple meal plan history showing previously saved plans for optional reuse**
6. **New meal plan creation starts fresh with option to load from saved plan**

### Story 6.6: Meal Planning Workflow Integration
As a user,  
I want seamless transitions between recipe browsing and meal planning,  
so that I can efficiently move from recipe discovery to meal plan creation.

#### Acceptance Criteria
1. **Quick-add functionality for adding items to meal plans without drag-and-drop**
2. **Recipe scaling prompts when adding items to meal plans**
3. **Meal plan overview showing total recipes and one-off items selected**
4. **Integration with recipe library filters for focused meal planning**
5. **Meal plan progress indicators showing planning completeness**
6. **Foundation for shopping list generation integration in subsequent epic**

## Epic 7: Meal Inventory & Coverage Management

**Epic Goal:** Implement the coverage-based meal planning view that shows planned meals over flexible time periods without rigid calendar constraints. Enable users to visualize meal coverage and ensure adequate meal planning for their chosen time frame, supporting the core differentiator of flexible time-based planning.

### Story 7.1: Meal Inventory Display
As a user,  
I want to see my planned meals in an inventory-style view,  
so that I can visualize my meal coverage and ensure I have adequate meals planned for my time period.

#### Acceptance Criteria
1. **Meal inventory interface showing all recipes and one-off items in current meal plan**
2. **Visual meal representation using same card styling as Recipe Deck with quantity indicators**
3. **Coverage summary displaying total planned meals and estimated meal count**
4. **Grouped display options (by meal type tags, by recipe vs one-off items)**
5. **Quick removal functionality for items directly from inventory view**
6. **Mobile-responsive inventory layout optimized for overview and quick modifications**

### Story 7.2: Time Period Configuration
As a user,  
I want to define the time period I'm planning for,  
so that I can plan appropriate meal coverage without calendar complexity.

#### Acceptance Criteria
1. **Simple time period selection (weekend, week, 2 weeks, month, custom days)**
2. **Meal coverage calculation based on selected time period and planned meals**
3. **Coverage indicators showing adequacy (enough meals, too few, too many)**
4. **Flexible period naming for special scenarios ("Vacation Week", "Holiday Weekend")**
5. **Period-based meal suggestions from user's own inventory showing coverage gaps**
6. **No calendar interface - purely duration and coverage focused**

### Story 7.3: Coverage Assessment & Visualization
As a user,  
I want visual feedback on my meal plan adequacy,  
so that I can ensure I have sufficient variety and quantity for my planned time period.

#### Acceptance Criteria
1. **Coverage metrics showing meals planned vs time period requirements**
2. **Visual coverage indicators (progress bars, color coding) for meal adequacy**
3. **Variety assessment highlighting potential repetition or missing meal types**
4. **Quick-add suggestions for coverage gaps using user's recipe library**
5. **Coverage warnings for insufficient or excessive meal planning**
6. **Simple coverage dashboard providing at-a-glance meal planning status**

### Story 7.4: Meal Plan Adjustment Tools
As a user,  
I want to easily adjust my meal plan based on coverage feedback,  
so that I can fine-tune my planning without starting over.

#### Acceptance Criteria
1. **One-click item removal from meal inventory with immediate coverage updates**
2. **Quick-add functionality for adding more meals when coverage is insufficient**
3. **Meal scaling adjustments for recipes directly from inventory view**
4. **Drag-and-drop reordering or grouping within inventory view**
5. **Bulk operations for adding multiple similar items or removing meal categories**
6. **Real-time coverage updates as meal plan modifications are made**

### Story 7.5: Meal Plan Completion Workflow
As a user,  
I want clear indication when my meal plan is ready for shopping list generation,  
so that I know when to move from planning to shopping list creation.

#### Acceptance Criteria
1. **Meal plan readiness indicators showing when coverage is adequate**
2. **Plan completion checklist highlighting any missing elements or warnings**
3. **Transition interface from meal planning to shopping list generation**
4. **Final meal plan review showing total items, coverage period, and estimated shopping list complexity**
5. **Optional meal plan naming and saving before proceeding to shopping list**
6. **Clear workflow progression from coverage assessment to shopping list creation**

### Story 7.6: Coverage-Based Planning Intelligence
As a user,  
I want smart coverage suggestions based on my planning period and current selection,  
so that I can efficiently achieve appropriate meal coverage without over-planning.

#### Acceptance Criteria
1. **Coverage gap identification highlighting missing meal types or insufficient quantity**
2. **Smart suggestions from user's own recipe library to fill coverage gaps**
3. **Meal variety suggestions preventing too much repetition within planning period**
4. **Planning period optimization suggestions for better coverage balance**
5. **All suggestions operate exclusively on user's personal recipe and one-off item collections**
6. **Coverage intelligence uses functional algorithms analyzing user's current meal plan state**

## Epic 8: Shopping List Generation Engine

**Epic Goal:** Develop the core ingredient aggregation algorithms and shopping list creation functionality that combines recipes and one-off items. This epic delivers the primary user value proposition by transforming meal plans into accurate, comprehensive shopping lists with proper quantity calculations and organization.

### Story 8.1: Ingredient Aggregation Algorithm
As a developer,  
I want pure functional algorithms for ingredient aggregation across multiple recipes,  
so that shopping lists accurately combine quantities of the same ingredients from different recipes.

#### Acceptance Criteria
1. **Pure functions for grouping identical ingredients across all recipes in meal plan**
2. **Quantity summation algorithms handling same units (2 cups + 1 cup = 3 cups)**
3. **Unit conversion functions for compatible units (1 cup + 4 tablespoons = 1.25 cups)**
4. **Smart ingredient matching using same normalization as recipe entry (case-insensitive, exact matching)**
5. **Recipe scaling integration applying user-selected scaling factors before aggregation**
6. **Error handling for incompatible unit combinations with user-friendly messages**

### Story 8.2: Shopping List Data Structure & Organization
As a user,  
I want my shopping list organized in a logical, grocery-store-friendly format,  
so that I can shop efficiently without missing items or backtracking through the store.

#### Acceptance Criteria
1. **Shopping list data structure combining aggregated recipe ingredients and one-off items**
2. **Logical grouping by ingredient categories (produce, dairy, meat, pantry, etc.)**
3. **Quantity display with appropriate units and clear formatting**
4. **Item source tracking (which recipes contributed to each ingredient)**
5. **One-off items integrated seamlessly with recipe ingredients in appropriate categories**
6. **Alphabetical sorting within categories for consistent organization**

### Story 8.3: Shopping List Generation Functions
As a user,  
I want to generate a complete shopping list from my meal plan with one click,  
so that I can transform my meal planning directly into actionable shopping instructions.

#### Acceptance Criteria
1. **One-click shopping list generation from completed meal plan**
2. **Real-time shopping list preview during meal planning for immediate feedback**
3. **Shopping list generation completing in <10 seconds for typical meal plans (up to 20 recipes)**
4. **Comprehensive error handling for edge cases (missing ingredients, invalid quantities)**
5. **Shopping list metadata showing source meal plan and generation timestamp**
6. **Functional composition of all aggregation and organization algorithms**

### Story 8.4: Shopping List Customization & Editing
As a user,  
I want to modify my generated shopping list before shopping,  
so that I can add forgotten items, remove items I already have, or adjust quantities.

#### Acceptance Criteria
1. **Shopping list editing functionality allowing quantity adjustments and item removal**
2. **Manual item addition for forgotten non-recipe items or household supplies**
3. **Item checking/unchecking for items already owned or not needed**
4. **Quantity override functionality for items where calculated amounts seem incorrect**
5. **Shopping list notes or comments functionality for special instructions**
6. **Edit history preservation allowing reversion to original generated list**

### Story 8.5: Shopping List Persistence & Retrieval
As a developer,  
I want functional shopping list storage and retrieval systems,  
so that users can access their shopping lists reliably across sessions and devices.

#### Acceptance Criteria
1. **Shopping list persistence using pure functions for database storage**
2. **Shopping list retrieval functions with efficient loading for mobile access**
3. **Shopping list versioning tracking changes and enabling undo operations**
4. **Associated meal plan reference linking shopping lists to source meal plans**
5. **Shopping list sharing functionality (optional) for household shopping coordination**
6. **Historical shopping list access for reference and reuse**

### Story 8.6: Advanced Aggregation Features
As a user,  
I want intelligent handling of complex ingredient scenarios,  
so that my shopping lists are accurate even with complicated recipes and scaling.

#### Acceptance Criteria
1. **Fractional quantity handling with practical rounding (1.33 cups → 1⅓ cups)**
2. **Measurement precision appropriate for cooking (avoid excessive decimal places)**
3. **Bulk quantity suggestions when individual quantities are very large**
4. **Ingredient substitution notes when recipes specify alternatives**
5. **Special handling for "to taste" ingredients and optional recipe components**
6. **Recipe source attribution showing which recipes contributed each ingredient**

## Epic 9: Mobile Shopping Experience

**Epic Goal:** Create the mobile-optimized shopping list interface with responsive design and touch-friendly interactions for grocery store usage. Complete the end-to-end user value delivery by providing an excellent in-store shopping experience that makes the generated shopping lists easy to use while grocery shopping.

### Story 9.1: Mobile Shopping List Interface
As a user,  
I want a mobile-optimized shopping list that's easy to use while grocery shopping,  
so that I can efficiently check off items and navigate my list with one hand while pushing a cart.

#### Acceptance Criteria
1. **Mobile-first shopping list layout optimized for smartphone screens and one-handed use**
2. **Large touch targets for checking off items while wearing gloves or in crowded stores**
3. **Clear visual hierarchy with large, readable text for quick scanning**
4. **High contrast design ensuring readability under various store lighting conditions**
5. **Swipe gestures for checking off items and quick item interaction**
6. **Responsive design that works across all mobile screen sizes**

### Story 9.2: Shopping List Check-Off System
As a user,  
I want to easily mark items as completed while shopping,  
so that I can track my progress and avoid buying duplicate items.

#### Acceptance Criteria
1. **One-tap item check-off with clear visual feedback (strikethrough, color change)**
2. **Undo functionality for accidentally checked items**
3. **Progress indicator showing shopping completion percentage**
4. **Checked items remain visible but visually distinguished from unchecked items**
5. **Shopping list auto-saves progress preventing loss if app is closed**
6. **Quick "check all" functionality for category completion**

### Story 9.3: Mobile Shopping Navigation
As a user,  
I want easy navigation through my shopping list categories while in the store,  
so that I can shop efficiently following store layout without scrolling through entire list.

#### Acceptance Criteria
1. **Category jump navigation allowing quick movement between list sections**
2. **Sticky category headers remaining visible while scrolling through items**
3. **Category completion indicators showing which store sections are finished**
4. **Collapsible categories for hiding completed sections**
5. **Search functionality for quickly finding specific items on long lists**
6. **Smooth scrolling and navigation optimized for touch interaction**

### Story 9.4: Shopping Experience Optimization
As a user,  
I want my shopping experience to be as smooth and efficient as possible,  
so that using Zestro shopping lists saves time and reduces shopping stress.

#### Acceptance Criteria
1. **Shopping list loads quickly on mobile devices**
2. **Battery-optimized interface for extended shopping trips**
3. **Clear, readable interface under various store lighting conditions**
4. **Quick item notes display for special instructions or preferences**
5. **Simple, focused mobile experience without unnecessary complexity**
6. **Integration with device accessibility features for users with disabilities**

## Checklist Results Report

### **PRD & EPIC VALIDATION REPORT**

#### **Executive Summary**
- **Overall PRD Completeness:** 95%
- **MVP Scope Appropriateness:** Just Right  
- **Readiness for Architecture Phase:** Ready
- **Most Critical Concern:** Technical stack complexity may impact development velocity

#### **Category Analysis**

| Category                         | Status  | Critical Issues |
| -------------------------------- | ------- | --------------- |
| 1. Problem Definition & Context  | PASS    | None - excellent problem articulation and user research from Project Brief |
| 2. MVP Scope Definition          | PASS    | Well-defined boundaries, clear rationale for inclusion/exclusion |
| 3. User Experience Requirements  | PASS    | Comprehensive UI goals, accessibility, mobile experience |
| 4. Functional Requirements       | PASS    | Clear FR/NFR separation, testable acceptance criteria |
| 5. Non-Functional Requirements   | PASS    | Specific performance targets, security considerations |
| 6. Epic & Story Structure        | PASS    | 9 focused epics with logical sequencing, AI-agent sized stories |
| 7. Technical Guidance            | PASS    | Clear functional programming constraints, technology stack defined |
| 8. Cross-Functional Requirements | PASS    | Database design, global systems architecture |
| 9. Clarity & Communication       | PASS    | Clear language, consistent terminology, well-structured |

#### **Top Issues by Priority**

**HIGH:**
- **Functional Programming Learning Curve:** Team readiness for Elm + F# stack may impact timeline
- **Recipe Entry UX Validation:** <5 minute target needs prototype validation
- **Global Systems Complexity:** Shared ingredients/units/tags add implementation complexity

**MEDIUM:**
- **Mobile Testing Strategy:** Need device testing plan for shopping list interface
- **Unit Conversion Algorithm:** Complex measurement conversions require detailed specification

#### **MVP Scope Assessment**
- **Appropriately Scoped:** 9 epics represent true MVP delivering core shopping list generation value
- **No Recommended Cuts:** All epics contribute to core value proposition
- **Timeline Realistic:** 6-month target achievable with focused execution
- **Complexity Managed:** Epic breakdown enables incremental delivery

#### **Technical Readiness**
- **Clear Constraints:** Functional programming requirements well-documented
- **Identified Risks:** Technology stack learning curve, recipe entry UX
- **Architect Investigation Areas:** F# web framework selection, Elm package ecosystem

#### **Recommendations**

1. **Prototype Recipe Entry UX:** Validate <5 minute target before Epic 2 implementation
2. **Team Training Plan:** Ensure Elm/F# expertise before development begins  
3. **Technology Validation:** Confirm F# web framework and Elm package availability
4. **Global Systems Testing:** Plan database performance testing for shared tag/ingredient systems

### **Final Decision: READY FOR ARCHITECT**

The PRD comprehensively defines Zestro's requirements with clear functional programming constraints, well-structured epics, and appropriate MVP scope. The architect can proceed with confidence while investigating the identified technical areas.

## Next Steps

### UX Expert Prompt
Review the Zestro PRD and create comprehensive UI/UX specifications focusing on the <5 minute recipe entry target, Recipe Deck interface design, and mobile shopping list experience. Prioritize functional programming-friendly UI patterns and Bulma CSS framework integration.

### Architect Prompt
Design the functional architecture for Zestro using the PRD requirements. Focus on Elm frontend architecture, F# backend design with pure functional patterns, PostgreSQL schema for global ingredient/unit/tag systems, and scalable shopping list aggregation algorithms. Address the identified technical investigation areas and provide implementation guidance for the 9 defined epics.