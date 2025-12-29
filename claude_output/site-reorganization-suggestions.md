# Site Reorganization Suggestions

## Current State

The site has 7 sections at the same level: coding, machine-learning, computer-vision, embedded-systems, math, japan-trip-2024, and japanese-milk-bread. This flat structure mixes educational content with personal content.

---

## Option 1: Three-Category Grouping (Recipes, Education, Travel)

Reorganize the homepage into three clear sections with nested content.

### Proposed Structure

```
/
├── index.html                    # Landing page with 3 sections
├── education/
│   ├── index.html                # Education hub page
│   ├── coding/
│   │   ├── index.html
│   │   ├── flashcards.html
│   │   ├── patterns/
│   │   └── problems/
│   ├── machine-learning/
│   │   ├── index.html
│   │   ├── flashcards.html
│   │   └── flashcards.csv
│   ├── computer-vision/
│   │   └── index.html
│   ├── embedded-systems/
│   │   └── index.html
│   └── math/
│       └── index.html
├── recipes/
│   ├── index.html                # Recipe hub page
│   └── japanese-milk-bread/
│       └── index.html
└── travel/
    ├── index.html                # Travel hub page
    └── japan-2024/
        ├── index.html
        └── img/
```

### Homepage Layout

```
┌─────────────────────────────────────┐
│         Michael Laielli             │
├───────────┬───────────┬─────────────┤
│ Education │  Recipes  │   Travel    │
│           │           │             │
│ • Coding  │ • Milk    │ • Japan     │
│ • ML      │   Bread   │   2024      │
│ • CV      │           │             │
│ • Embedded│           │             │
│ • Math    │           │             │
└───────────┴───────────┴─────────────┘
```

### Pros
- Clear separation of professional and personal content
- Scalable (easy to add more recipes or trips)
- Intuitive for visitors

### Cons
- Requires URL redirects or updates to preserve existing links
- More nested directory structure

---

## Option 2: Two-Category Split (Professional / Personal)

Simpler binary division between work-related and personal content.

### Proposed Structure

```
/
├── index.html                    # Landing page with 2 sections
├── professional/
│   ├── index.html                # Professional hub
│   ├── coding/
│   ├── machine-learning/
│   ├── computer-vision/
│   ├── embedded-systems/
│   └── math/
└── personal/
    ├── index.html                # Personal hub
    ├── travel/
    │   └── japan-2024/
    └── recipes/
        └── japanese-milk-bread/
```

### Homepage Layout

```
┌─────────────────────────────────────┐
│         Michael Laielli             │
├─────────────────┬───────────────────┤
│  Professional   │     Personal      │
│                 │                   │
│ • Coding        │ • Japan 2024      │
│ • ML            │ • Milk Bread      │
│ • CV            │                   │
│ • Embedded      │                   │
│ • Math          │                   │
└─────────────────┴───────────────────┘
```

### Pros
- Simplest reorganization (only 2 top-level categories)
- Clear professional/personal boundary
- Minimal cognitive load for visitors

### Cons
- Less granular than 3-category approach
- "Personal" mixes different content types (travel vs recipes)

---

## Option 3: Flat Structure with Visual Grouping

Keep the flat URL structure but reorganize the homepage visually into sections. No directory changes needed.

### Proposed Structure

```
/
├── index.html                    # Reorganized landing page
├── coding/                       # (unchanged)
├── machine-learning/             # (unchanged)
├── computer-vision/              # (unchanged)
├── embedded-systems/             # (unchanged)
├── math/                         # (unchanged)
├── japan-trip-2024/              # (unchanged)
└── japanese-milk-bread/          # (unchanged)
```

### Homepage Layout

The `index.html` is updated to visually group links:

```
┌─────────────────────────────────────┐
│         Michael Laielli             │
├─────────────────────────────────────┤
│            EDUCATION                │
│  Coding • ML • CV • Embedded • Math │
├─────────────────────────────────────┤
│             TRAVEL                  │
│           Japan 2024                │
├─────────────────────────────────────┤
│            RECIPES                  │
│       Japanese Milk Bread           │
└─────────────────────────────────────┘
```

### Pros
- No URL changes (preserves all existing links)
- Minimal code changes (just update index.html)
- Quick to implement

### Cons
- Doesn't scale as well (flat structure gets unwieldy with more content)
- Less organized at the filesystem level

---

## Recommendation

**Option 1 (Three-Category Grouping)** provides the best balance of organization and scalability. It creates a clear mental model for visitors and makes the site easy to expand.

**Option 3 (Visual Grouping)** is the fastest to implement if you want immediate improvement with minimal effort.

| Criteria | Option 1 | Option 2 | Option 3 |
|----------|----------|----------|----------|
| Implementation effort | High | Medium | Low |
| Scalability | High | Medium | Low |
| URL preservation | No | No | Yes |
| Clarity | High | Medium | Medium |
