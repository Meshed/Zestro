# Error States & Edge Case Wireframes

*Comprehensive error handling, empty states, and loading patterns for robust user experience*

## A. Network/Connection Errors

```
┌─────────────────────────────────────────────────────────────────┐
│ 🍳 Zestro                                                       │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│                        🌐❌                                     │
│                                                                 │
│                Connection Lost                                  │
│                                                                 │
│ We're having trouble connecting to our servers.                │
│ Don't worry - your work is saved locally!                      │
│                                                                 │
│ ┌─ What You Can Still Do: ──────────────────────────────────── │ │
│ │ ✅ Continue editing your current recipe                      │ │
│ │ ✅ View your existing recipes and meal plans                 │ │
│ │ ✅ Access your saved shopping lists                         │ │
│ │ ❌ Create new ingredients or tags                           │ │
│ │ ❌ Generate new shopping lists                              │ │
│ └─────────────────────────────────────────────────────────────┘ │
│                                                                 │
│ We'll automatically sync your changes when you're back online. │
│                                                                 │
│ [Try Again] [Work Offline] [Check System Status]               │
│                                                                 │
│ Last sync: 2 minutes ago ✅                                    │
└─────────────────────────────────────────────────────────────────┘
```

## B. Empty States

### Empty Recipe Library
```
┌─────────────────────────────────────────────────────────────────┐
│ 🍳 My Recipe Library                                            │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│                       📚✨                                      │
│                                                                 │
│                Your Recipe Library is Empty                     │
│                                                                 │
│ Ready to build your personal recipe collection?                │
│ Add your first recipe and start creating amazing meal plans!   │
│                                                                 │
│ ┌─ Getting Started Ideas: ──────────────────────────────────── │ │
│ │ 💡 Start with a family favorite                             │ │
│ │ 💡 Add a quick weeknight dinner                             │ │
│ │ 💡 Try that recipe you always make from memory              │ │
│ └─────────────────────────────────────────────────────────────┘ │
│                                                                 │
│ [🎯 Add Your First Recipe] [📖 Browse Recipe Examples]         │
│                                                                 │
│ Need help? [📹 Watch Tutorial] [💬 Get Support]                │
└─────────────────────────────────────────────────────────────────┘
```

### No Search Results
```
┌─────────────────────────────────────────────────────────────────┐
│ 🔍 Search Results for "vegan sushi"                             │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│                       🔍❌                                      │
│                                                                 │
│                 No recipes found                                │
│                                                                 │
│ We couldn't find any recipes matching "vegan sushi"            │
│                                                                 │
│ ┌─ Try This Instead: ───────────────────────────────────────── │ │
│ │ • Check your spelling                                       │ │
│ │ • Try broader terms like "vegan" or "sushi"                │ │
│ │ • Browse by tags: [Vegan] [Asian] [Japanese]               │ │
│ │ • Create a new recipe with these ingredients!              │ │
│ └─────────────────────────────────────────────────────────────┘ │
│                                                                 │
│ [🎯 Add "Vegan Sushi" Recipe] [Clear Search] [Browse All Tags] │
│                                                                 │
│ Suggested searches: [vegetarian sushi] [vegan rolls]           │
└─────────────────────────────────────────────────────────────────┘
```

## C. System Errors

### Server Error (500)
```
┌─────────────────────────────────────────────────────────────────┐
│ 🍳 Zestro                                                       │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│                        🔧💔                                     │
│                                                                 │
│               Oops! Something went wrong                        │
│                                                                 │
│ We're experiencing a temporary hiccup on our end.              │
│ Our team has been notified and is working on a fix.           │
│                                                                 │
│ ┌─ What Happened: ──────────────────────────────────────────── │ │
│ │ Error ID: ZST-2025-0909-1445                                │ │
│ │ Time: September 9, 2025 2:45 PM                             │ │
│ │ Your data is safe and will be restored shortly.             │ │
│ └─────────────────────────────────────────────────────────────┘ │
│                                                                 │
│ ┌─ While You Wait: ─────────────────────────────────────────── │ │
│ │ ✅ Check our [Status Page] for updates                      │ │
│ │ ✅ Follow @ZestroApp for real-time updates                  │ │
│ │ ✅ Contact support if this persists                         │ │
│ └─────────────────────────────────────────────────────────────┘ │
│                                                                 │
│ [Try Again] [Contact Support] [System Status]                  │
│                                                                 │
│ Estimated fix time: < 30 minutes                               │
└─────────────────────────────────────────────────────────────────┘
```

## D. Data Loading States

### Shopping List Generation
```
┌─────────────────────────────────────────────────────────────────┐
│ 🛒 Generating Your Shopping List...                             │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│                    🔄 Working on it...                          │
│                                                                 │
│ ┌─ Progress ─────────────────────────────────────────────────── │ │
│ │                                                             │ │
│ │ ✅ Analyzing your meal plan...                               │ │
│ │ ✅ Combining ingredient quantities...                        │ │
│ │ 🔄 Organizing by store sections...                          │ │
│ │ ⏳ Adding one-off items...                                   │ │
│ │ ⏳ Final optimization...                                     │ │
│ │                                                             │ │
│ │ [██████████░░] 75% complete                                 │ │
│ └─────────────────────────────────────────────────────────────┘ │
│                                                                 │
│ Smart aggregation in progress:                                 │
│ • Ground beef: 1 lb + 2 lbs = 3 lbs total ✅                  │
│ • Onions: 2 medium + 1 large = 3 medium equivalent ✅         │
│ • Olive oil: 2 tbsp + 1/4 cup = 6 tbsp total 🔄              │
│                                                                 │
│ This usually takes 5-10 seconds...                             │
│                                                                 │
│ [Cancel] - Your meal plan will be saved                        │
└─────────────────────────────────────────────────────────────────┘
```

---

## Error Handling Principles

### User-Centric Error Messages
- **Clear Language**: Avoid technical jargon, use conversational tone
- **Actionable Guidance**: Always provide next steps users can take
- **Reassurance**: Confirm data safety and automatic recovery when possible
- **Context**: Include relevant details (error IDs, timestamps) for support

### Progressive Disclosure
- **Primary Message**: Clear, simple explanation of what happened
- **Secondary Details**: Technical information hidden behind expandable sections
- **Help Options**: Multiple support channels based on user preference
- **Recovery Actions**: Clear, obvious ways to continue or retry

### Offline-First Design
- **Local Storage**: Critical data cached for offline access
- **Sync Indicators**: Clear status of when data was last synchronized
- **Graceful Degradation**: Core functionality available without network
- **Automatic Recovery**: Seamless sync when connection restored

### Loading State Patterns
- **Progress Indicators**: Show completion percentage and current step
- **Estimated Time**: Set user expectations with realistic time estimates
- **Cancellation**: Allow users to stop long-running operations
- **Skeleton States**: Show layout structure while content loads

### Empty State Conversion
- **Onboarding Value**: Turn empty states into engagement opportunities
- **Clear CTAs**: Obvious actions to start adding content
- **Inspiration**: Provide examples and suggestions to reduce blank page anxiety
- **Educational**: Use empty states to teach product features

These error states maintain user trust and engagement even when things go wrong, turning potential frustration into opportunities for user education and product adoption.