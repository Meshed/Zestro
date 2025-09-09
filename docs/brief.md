# Project Brief: Zestro

## Executive Summary

**Zestro** is a meal planning and shopping list generation platform that transforms the tedious process of creating grocery lists into a streamlined, automated experience. The platform addresses the universal pain of inefficient meal planning by allowing users to build meal plans from their own recipes and automatically generating combined shopping lists with accurate ingredient quantities.

**Primary Problem:** Weekly grocery shopping planning is time-consuming, error-prone, and often incomplete, leading to overspending, forgotten items, and multiple store trips. Existing meal planning solutions focus on recipe suggestions rather than solving the shopping list generation challenge.

**Target Market:** Home cooks and meal planners who shop regularly for varying time periods and want to maintain control over their recipes while eliminating shopping list creation friction.

**Key Value Proposition:** User-owned recipes combined with intelligent shopping list aggregation, differentiating from suggestion-based meal planning apps by focusing on the shopping outcome rather than meal discovery.

## Problem Statement

**Current State:** Home cooks spend significant time each week creating grocery shopping lists for planned meals, a process that is both time-consuming and fraught with errors. The typical workflow involves finding recipes, extracting ingredients, manually combining quantities (e.g., summing 1 lb + 2 lbs of ground beef across recipes), and remembering non-recipe items like snacks and drinks.

**Pain Points & Impact:**
- **Time Consumption:** Recipe gathering, ingredient extraction, and quantity summing can take 30-60 minutes weekly
- **Error-Prone Process:** Manual ingredient aggregation leads to under-buying (requiring additional store trips) or over-buying (food waste and overspending)
- **Mental Load:** Remembering non-recipe items, favorite meals not prepared recently, and proper scaling for different serving sizes
- **Incomplete Planning:** Forgetting items like drinks, snacks, or frozen meals that aren't part of recipe planning but essential for the shopping period

**Why Existing Solutions Fall Short:**
Current meal planning apps focus on recipe discovery and meal suggestions rather than solving the shopping list generation problem. They typically:
- Suggest meals users don't own or haven't customized
- Lack proper ingredient quantity aggregation across multiple recipes
- Don't handle mixed recipe/non-recipe shopping needs
- Force users into rigid calendar-based meal scheduling rather than flexible coverage planning

**Urgency & Importance:** This is a recurring weekly friction point that compounds over time. The brainstorming session revealed that the core differentiator opportunity lies in shopping list generation rather than competing in the crowded meal suggestion space. Users want to maintain control over their recipes while eliminating the tedious aggregation work.

## Proposed Solution

**Core Concept:** Zestro is a web-based meal planning platform that transforms user-owned recipes into intelligent shopping lists through automated ingredient aggregation. Users build their personal recipe library, create flexible meal plans using a "Recipe Deck" interface, and generate combined shopping lists with accurate quantity calculations.

**MVP Solution Components:**
- **Personal Recipe Library:** Users create and maintain their own recipe collection with full ownership and scaling capabilities for different serving sizes
- **Flexible Meal Planning:** "Recipe Deck + Meal Inventory" interface that focuses on meal coverage over rigid scheduling, allowing users to plan for time periods rather than specific dates
- **Intelligent Shopping List Generation:** Automated aggregation of ingredients across multiple recipes with quantity summing, plus integration of non-recipe items (snacks, drinks, frozen meals)
- **Multi-dimensional Organization:** Flexible tagging system combining hierarchical categories (cuisine type), temporal tags (breakfast/lunch/dinner), and mood-based classifications

**Core Differentiators:**
- **Shopping-First Approach:** Unlike meal suggestion apps, Zestro prioritizes shopping list accuracy and completeness over meal discovery
- **User Recipe Ownership:** Personal recipe library that users fully control and customize
- **Coverage-Based Planning:** Flexible meal planning focused on ensuring adequate meal coverage for a time period rather than rigid calendar scheduling
- **Complete Shopping Solution:** Integrates recipe ingredients with non-recipe shopping needs in a unified list

**Future Enhancement Vision:**
GitHub-style recipe sharing and cloning capabilities will enable community growth while maintaining individual recipe ownership, but the MVP focuses on perfecting the personal workflow first.

**Why This Will Succeed:**
The MVP addresses the core workflow pain point of shopping list generation while avoiding the competitive suggestion-based meal planning market. Future community features will build on a solid foundation of personal utility.

## Target Users

### Primary User Segment: Regular Home Cooks & Meal Planners

**Demographic Profile:**
- Adults aged 25-55 who cook at home regularly (3+ times per week)
- Household grocery shoppers responsible for meal planning
- Comfortable with web applications and basic technology
- Income sufficient for regular grocery shopping with preference for planning over impulse buying

**Current Behaviors & Workflows:**
- Shop for groceries for varying time periods: weekend events, weekly routine shopping, monthly bulk planning, or special occasions
- Plan meals for different scenarios: regular household meals, dinner parties, holiday gatherings, or extended periods
- Maintain mental or physical lists of favorite recipes but struggle to recall them consistently
- Currently create shopping lists manually for each planning scenario, often incompletely
- Make multiple store trips due to forgotten items or underestimated quantities for any time period

**Specific Needs & Pain Points:**
- **Flexible Planning Periods:** Need to plan meals for any duration from a weekend Super Bowl party to a month-long period
- **Time Efficiency:** Want to minimize shopping list creation time while maximizing accuracy regardless of planning scope
- **Recipe Management:** Need easy access to their favorite recipes with ability to scale serving sizes for different group sizes and durations
- **Planning Flexibility:** Prefer flexible meal coverage over rigid scheduling constraints across any time frame
- **Shopping Completeness:** Want confidence that their list includes everything needed for whatever period they're planning for
- **Quantity Accuracy:** Need reliable ingredient aggregation whether planning for 2 days or 30 days

**Goals They're Trying to Achieve:**
- Efficiently plan and shop for meals across any time period or occasion
- Eliminate additional grocery store trips regardless of planning scope
- Handle both routine meal planning and special event planning with the same tool
- Feel organized and in control of their food planning for any scenario

## Goals & Success Metrics

### Business Objectives
- **Launch successful MVP within 6 months** with core shopping list generation functionality and intuitive recipe entry experience
- **Achieve recipe entry adoption** demonstrating that users find recipe input simple enough to build substantial recipe libraries
- **Establish foundation for monetization** through comprehensive feature usage analytics and user workflow understanding
- **Build sustainable user base** of regular home cooks who demonstrate consistent platform usage beyond initial trial
- **Create competitive differentiation** in meal planning market through shopping-first approach with frictionless recipe management

### User Success Metrics
- **Recipe Entry Adoption:** Users successfully add 5+ recipes within first week and continue adding recipes over time
- **Recipe Entry Efficiency:** Users can input a complete recipe (ingredients, directions, metadata) in under 5 minutes
- **Planning Time Reduction:** Users report 50%+ reduction in shopping list creation time compared to manual methods
- **Shopping Trip Efficiency:** Users require fewer additional grocery trips due to forgotten or miscalculated items
- **Recipe Library Growth:** Users consistently add and organize recipes without abandoning the entry process
- **List Completeness:** Generated shopping lists include both recipe ingredients and non-recipe items with accurate quantities

### Key Performance Indicators (KPIs)
- **Recipe Entry Completion Rate:** Percentage of started recipes that are fully completed and saved (target: >90%)
- **Recipe Entry Abandonment Points:** Analytics on where users drop off during recipe input to identify friction
- **Time-to-First-Recipe:** How quickly new users successfully add their first complete recipe
- **Recipe Library Size Distribution:** Average number of recipes per active user and growth patterns
- **Feature Usage Analytics:** Detailed metrics on recipe creation workflow, meal planning patterns, and shopping list generation
- **User Retention:** Monthly active users, returning user percentage, with special focus on users who complete recipe entry
- **Recipe Entry User Feedback:** Direct user satisfaction scores specifically for recipe input experience

## MVP Scope

### Core Features (Must Have)

- **Intuitive Recipe Entry System:** Simple, fast recipe input interface prioritizing ease of use over advanced features. Must allow users to add complete recipes (name, ingredients with quantities, directions, serving size, prep/cook time, tags) in under 5 minutes with minimal friction

- **Personal Recipe Library:** Storage and organization of user-created recipes with basic search and filtering by tags/categories. Users maintain full ownership of their recipe collection

- **Global Shared Tag System:** Platform-wide tag library where all user-created tags become available for all users. Features autocomplete/suggestion functionality during recipe entry to show existing tags before allowing new tag creation. Prevents tag proliferation and ensures consistency across users while maintaining flexibility for new categories

- **Flexible Multi-Tag Classification:** User-defined tagging system supporting hierarchical categories (cuisine type), temporal tags (breakfast/lunch/dinner), and mood-based classifications, all drawing from the shared tag library

- **Recipe Scaling Capability:** Ability to adjust ingredient quantities for different serving sizes (doubling, tripling, halving, custom scaling) during meal planning

- **Recipe Deck + Meal Inventory Interface:** Non-calendar based meal planning using card metaphor for recipe selection and inventory view for meal coverage over any time period

- **One-off Item Management:** Ability to add non-recipe items (snacks, drinks, frozen meals) to meal plans with same shared tagging system as recipes

- **Intelligent Shopping List Generation:** Automated aggregation of ingredients across multiple recipes with accurate quantity summing, combined with one-off items into unified shopping list

- **Mobile-Friendly Shopping List View:** Responsive design allowing easy viewing and interaction with generated shopping lists on mobile devices while shopping

- **User Account Management:** Basic user registration, login, profile settings, and data persistence

### Out of Scope for MVP

- Recipe sharing and GitHub-style cloning functionality
- Integration with delivery services (Instacart, Amazon Fresh, etc.)
- Cost tracking and price comparison features
- Mobile companion application
- Recipe importing from images, videos, or URLs
- AI-powered recipe recommendations
- Advanced analytics dashboard (basic usage tracking only)
- Multi-user collaboration features
- Recipe photography and visual enhancements

### MVP Success Criteria

**MVP is successful when users can:**
- Add their first recipe in under 5 minutes without abandoning the process
- Create meal plans for any time period (weekend to monthly) using their recipe library
- Generate accurate shopping lists that include both recipe ingredients and non-recipe items
- Access and use their shopping list effectively while grocery shopping
- Demonstrate continued usage by regularly adding recipes and creating meal plans

**Technical Success Criteria:**
- Recipe entry completion rate >90%
- Application loads in <3 seconds
- Shopping list generation completes in <10 seconds for typical meal plans
- Mobile shopping list view functions properly on standard smartphones

## Post-MVP Vision

### Phase 2 Features

**Community & Sharing Capabilities:**
- **GitHub-Style Recipe Sharing:** Users can publish recipes to community library with clear attribution and discoverability
- **One-Way Recipe Cloning:** Users can clone any shared recipe into their personal library where it becomes fully theirs to modify without affecting the original. Original recipe attribution is maintained but modifications create independent recipe ownership
- **Recipe Rating & Review System:** Community feedback on shared recipes with difficulty ratings and cooking success stories

**Enhanced Mobile Experience:**
- **Mobile Companion Application:** Native iOS/Android app focused on shopping checklist functionality, meal completion tracking, and quick recipe importing via camera
- **Offline Shopping Lists:** Downloadable lists for use in stores without reliable internet connectivity
- **Shopping Progress Tracking:** Check-off functionality with meal completion status updates

**Smart Recipe Import:**
- **Recipe Import from Images:** Camera-based recipe capture with AI text recognition and automatic formatting
- **YouTube Video Recipe Extraction:** AI-powered recipe extraction from cooking videos with ingredient and instruction parsing
- **URL Recipe Import:** Automatic recipe scraping from popular cooking websites

### Long-term Vision (12-18 months)

**AI-Powered Enhancements:**
- **Recipe Recommendation Engine:** Suggest recipes based on historical usage patterns, seasonal availability, and user preferences
- **Smart Meal Planning Assistant:** AI-powered suggestions for meal coverage optimization and variety balancing
- **Ingredient Substitution Intelligence:** Automatic suggestions for ingredient replacements based on dietary restrictions or availability

**Advanced Shopping Features:**
- **Multi-Service Delivery Integration:** Integration with Instacart, Amazon Fresh, Walmart+ with commission-based revenue model
- **Cost Tracking & Optimization:** Real-time price comparison across local stores with shopping route optimization
- **Manufacturer Deal Integration:** Targeted coupons and discounts based on planned recipes and shopping lists

**Platform Expansion:**
- **Smart Kitchen Integration:** Connect with IoT appliances for inventory tracking and cooking guidance
- **Nutritional Analysis:** Automatic nutritional information calculation for recipes and meal plans
- **Social Features:** Meal sharing, cooking challenges, and community events

### Expansion Opportunities

**Monetization Stream Development:**
- **Premium Subscription Tiers:** Advanced features like detailed cost tracking, unlimited recipe imports, and priority customer support
- **Partnership Revenue:** Commission from delivery services, affiliate marketing with kitchen equipment, and sponsored recipe content
- **Data Analytics Services:** Anonymized food trend insights for manufacturers and retailers

**Market Expansion:**
- **International Localization:** Support for regional ingredients, measurements, and dietary preferences
- **Enterprise Solutions:** Meal planning tools for restaurants, catering companies, and institutional food service
- **White-Label Platform:** Licensing the core technology to grocery chains and meal kit companies

## Technical Considerations

### Platform Requirements
- **Target Platforms:** Web application (primary), mobile-responsive design for shopping list access
- **Browser/OS Support:** Modern browsers (Chrome, Firefox, Safari, Edge) with ES6+ support, mobile Safari and Chrome for shopping functionality

### Technology Preferences

**Frontend Technology:**
- **Framework:** Elm for functional programming adherence and type safety
- **CSS Framework:** Bulma for modern, playful, colorful design that aligns with friendly/helpful tone requirements
- **Architecture:** Single-page application with component-based structure following functional programming principles

**Backend Technology:**
- **Language:** F# for functional programming consistency and strong typing
- **Architecture:** Functional web API design with immutable data structures and pure functions where possible
- **Authentication:** Secure user authentication system with session management

**Database:**
- **Primary Database:** PostgreSQL for relational data management, excellent F# integration, and functional programming compatibility
- **Schema Design:** Normalized relational structure optimized for recipe, meal plan, and shopping list relationships
- **Data Integrity:** Strong typing and constraints to ensure data consistency

### Architecture Considerations

**Repository Structure:**
- **Monorepo Approach:** Single repository containing both Elm frontend and F# backend with clear separation
- **Functional Architecture:** Domain-driven design with functional core and imperative shell pattern
- **Data Flow:** Unidirectional data flow following Elm Architecture pattern

**Service Architecture:**
- **Web API Design:** RESTful API with functional F# controllers and domain models
- **Data Layer:** Functional database access layer with query composition and type safety
- **Business Logic:** Pure functional domain logic separated from infrastructure concerns

**Integration Requirements:**
- **Database Integration:** Type-safe F# database access with PostgreSQL
- **Mobile Responsiveness:** CSS Grid/Flexbox with Bulma responsive utilities
- **Future API Readiness:** Designed for potential delivery service integrations (post-MVP)

**Security/Compliance:**
- **Data Protection:** User recipe data encryption at rest and in transit
- **Authentication:** Secure password hashing and session management
- **Privacy:** Clear data ownership policies with user control over recipe sharing
- **GDPR Considerations:** Data export and deletion capabilities for user privacy compliance

## Constraints & Assumptions

### Constraints

**Budget:**
- MVP development operating within personal project budget constraints
- Technology choices prioritize open-source solutions and cost-effective hosting options
- Development team likely small (solo or small team) requiring technology choices that maximize productivity

**Timeline:**
- 6-month MVP development timeline as stated in business objectives
- Single developer or small team capacity requiring realistic scope management
- Functional programming learning curve factored into development estimates

**Resources:**
- Development team must acquire or possess Elm and F# functional programming expertise
- Database design and management capabilities required for PostgreSQL implementation
- UI/UX design skills needed for intuitive recipe entry interface design

**Technical:**
- Strict adherence to functional programming paradigms across entire stack (Elm + F#)
- Web-first platform with mobile responsiveness rather than native mobile development
- Single database solution (PostgreSQL) must handle all data persistence requirements

### Key Assumptions

- **User Behavior:** Target users are willing to invest time in building their personal recipe library if the entry process is sufficiently intuitive
- **Market Need:** The shopping list generation focus represents a genuine market gap not adequately addressed by existing meal planning solutions
- **Technical Approach:** Functional programming stack (Elm + F#) will provide sufficient development velocity despite potential learning curve
- **Recipe Entry:** Users can effectively input recipes through web interface without requiring mobile app for initial capture
- **Competitive Position:** Shopping-first approach provides sustainable competitive differentiation in meal planning market
- **Global Tag System:** Users will adopt shared tagging system and benefit from collective tag library growth
- **Flexible Planning:** Coverage-based meal planning (vs. calendar scheduling) resonates with target user preferences
- **Monetization Path:** MVP user base and analytics will validate assumptions for future revenue streams
- **Technology Scaling:** PostgreSQL and chosen architecture can support anticipated user growth through Phase 2 features

## Risks & Open Questions

### Key Risks

- **Recipe Entry UX Risk:** If recipe input is too complex or time-consuming, users will abandon the platform before building meaningful recipe libraries. This is the highest priority risk given your concerns about user adoption
- **Functional Programming Learning Curve:** Development velocity may be slower than anticipated if team needs significant time to master Elm and F# functional programming paradigms
- **Market Validation Risk:** The shopping list generation focus may not resonate strongly enough with target users to drive sustained engagement and growth
- **Competitive Response Risk:** Established meal planning platforms could quickly add shopping list aggregation features, reducing Zestro's differentiation advantage
- **Recipe Library Network Effects:** Platform value depends on users building substantial recipe libraries, but early users have limited recipes, creating potential chicken-and-egg adoption challenge
- **Mobile Shopping Experience:** Users may expect native mobile app functionality for grocery shopping that the responsive web design cannot adequately provide

### Open Questions

- **Recipe Entry Interface Design:** What specific UI patterns and interactions will make recipe input feel effortless rather than tedious? Should we prototype multiple approaches?
- **Global Tag Management:** How do we prevent tag system from becoming cluttered with near-duplicate tags while maintaining user flexibility?
- **User Onboarding Strategy:** How do we guide new users through their first recipe entry and meal plan creation to demonstrate value quickly?
- **Recipe Scaling Algorithm:** What's the best approach for handling complex ingredient scaling (e.g., "1 medium onion" when doubling a recipe)?
- **Shopping List Format Optimization:** What information hierarchy and visual design makes shopping lists most effective in actual grocery store environments?
- **Data Migration Strategy:** How will users import existing recipes from other formats (handwritten, other apps, printed recipes)?
- **Community Recipe Quality:** When Phase 2 sharing is implemented, how do we ensure recipe quality without heavy moderation overhead?

### Areas Needing Further Research

- **Recipe Entry Usability Testing:** Conduct user testing sessions focused specifically on recipe input workflows to identify friction points
- **Competitive Analysis Deep Dive:** Detailed analysis of how existing meal planning apps handle shopping list generation and where they fall short
- **Mobile Shopping Behavior Research:** Study how users actually interact with shopping lists on mobile devices in grocery store environments
- **Functional Programming Team Readiness:** Assessment of development team's current functional programming skills and learning timeline requirements
- **Database Schema Validation:** Prototype core data relationships to validate PostgreSQL design can handle complex recipe/meal plan relationships efficiently
- **Tag System Architecture:** Research existing tagging systems to identify best practices for autocomplete, duplicate prevention, and user experience

## Appendices

### A. Research Summary

**Brainstorming Session Analysis (September 8, 2025):**
Key findings from comprehensive brainstorming session using multiple ideation techniques:
- **Core Differentiator Validated:** Shopping list generation focus provides competitive advantage over meal suggestion platforms
- **UI Solution Identified:** Recipe Deck + Meal Inventory interface solves calendar rigidity problem with familiar metaphors
- **Technical Stack Clarified:** PostgreSQL + Bulma combination supports functional programming requirements and playful design goals
- **Revenue Model Validated:** Multi-service delivery integration and manufacturer partnerships create win-win monetization opportunities
- **User Workflow Insights:** Coverage-based planning more valuable than scheduling-based approaches for target users

**Technology Research:**
- PostgreSQL selected for relational data model fit and F# functional programming integration
- Bulma CSS framework chosen for modern, playful design that aligns with friendly brand tone
- Recipe Deck interface metaphor validated through analogical thinking with fitness/gaming workflows

**Competitive Positioning:**
- Existing meal planning solutions focus on recipe discovery rather than shopping list accuracy
- Market gap exists for user-owned recipe libraries with intelligent shopping list generation
- Flexible time planning (vs. calendar-based) represents unexploited user preference

### B. Stakeholder Input

**Project Owner Requirements:**
- Emphasis on recipe entry simplicity as critical success factor
- Strong preference for flexible time planning over rigid calendar scheduling
- Requirement for comprehensive analytics and usage tracking for future decision making
- Insistence on functional programming adherence (Elm + F#) throughout entire stack
- Clear vision for one-way recipe sharing model in future phases (clone without feedback loops)

### C. References

- **Initial Requirements Document:** `docs/zestrorequrements.md` - Complete problem definition and MVP specifications
- **Brainstorming Session Results:** `docs/brainstorming-session-results.md` - Comprehensive ideation session with 25+ actionable ideas across 6 major categories
- **BMAD Core Configuration:** `.bmad-core/core-config.yaml` - Project structure and documentation standards

## Next Steps

### Immediate Actions

1. **Create Recipe Entry UX Prototypes** - Design and test multiple recipe input interface approaches to validate the <5 minute entry target and identify optimal user workflow
2. **Validate Recipe Deck + Meal Inventory Interface** - Create clickable mockups of the non-calendar meal planning approach and test with target users
3. **Set up Development Environment** - Configure Elm + F# + PostgreSQL development stack and establish project repository structure
4. **Design Global Tag System Architecture** - Define database schema and UI patterns for shared tag library with autocomplete functionality
5. **Create Initial Database Schema** - Design PostgreSQL tables for recipes, meal plans, users, and shopping lists following functional programming principles
6. **Conduct Competitive Analysis Deep Dive** - Research existing meal planning platforms' shopping list capabilities and identify specific differentiation opportunities
7. **Plan User Onboarding Flow** - Design first-time user experience focused on successful first recipe entry and meal plan creation

### PM Handoff

This Project Brief provides the full context for **Zestro**. Please start in 'PRD Generation Mode', review the brief thoroughly to work with the user to create the PRD section by section as the template indicates, asking for any necessary clarification or suggesting improvements.

**Key Focus Areas for PRD Development:**
- **Recipe Entry UX Specifications:** Detailed user interface requirements and interaction patterns for intuitive recipe input
- **Shopping List Generation Algorithm:** Technical specifications for ingredient aggregation, quantity summing, and list formatting
- **Global Tag System Implementation:** Database design and user interface specifications for shared tagging functionality
- **Mobile-Responsive Shopping Lists:** Detailed requirements for mobile grocery shopping experience

**Critical Success Factors to Maintain:**
- Recipe entry simplicity as #1 priority (target: <5 minutes, >90% completion rate)
- Functional programming adherence throughout entire stack
- Flexible time period planning rather than calendar-based scheduling
- User-owned recipe library model with future one-way sharing capability