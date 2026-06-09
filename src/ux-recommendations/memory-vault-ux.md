# Memory Vault UX Recommendations

## Entry and Navigation

The Memory tab should open to a search-first view — a large search bar, full width, cursor active. There is no browse-by-category default view. The vault is accessed through search, not navigation.

Rationale: ADHD users rarely remember what category they filed something under. They remember fragments — a name, a feeling, a project — and search works with that.

---

## Search Interaction

```
┌─────────────────────────────┐
│  🔍  What do you remember?  │  ← Placeholder, cursor active
│                             │
│  Recent searches:           │
│  · Arena Resorts            │
│  · ITIDA proposal           │
│  · shark idea               │
└─────────────────────────────┘
```

- Search is instant — results appear as the user types, no search button
- Results ranked by relevance, not date
- Show a short excerpt from each result — enough to confirm it's the right item
- No empty state on an unfocused search bar — show recent searches instead

---

## Result Cards

Each result card shows:

```
┌─────────────────────────────┐
│  Note · 3 days ago          │
│                             │
│  Arena Resorts — decided    │
│  to proceed with homepage   │
│  first, pricing page after. │
│                             │
│  [ Open ]  [ Add to today ] │
└─────────────────────────────┘
```

- Type badge (Note / Task / Decision / Idea / Meeting)
- Age is relative ("3 days ago") not absolute date
- Short excerpt — enough context to confirm relevance
- Two quick actions: open full item, or surface it in today's task list

---

## Storing Items

Items are stored automatically from:
- Brain Dump outputs
- Completed sessions
- Daily briefings

Users can also store manually via a "+ Save to Memory" button on any content surface in the app.

**Never require the user to choose a category before saving.** Category is inferred and editable after.

---

## Privacy Indicator

A small lock icon in the tab bar and at the top of the vault view confirms: *this is yours, only visible to you.* No explanation needed beyond the icon — but it should always be present.
