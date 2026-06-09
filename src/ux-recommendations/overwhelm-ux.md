# Overwhelm Detection UX Recommendations

## Detection Signal — User-Facing Behaviour

Overwhelm Detection should be **invisible until it acts**. The user should not see a score, a warning, or a meter that tells them they are overwhelmed — this worsens anxiety.

The system acts. The user experiences the result.

---

## Transition into Reduced View

When overwhelm is detected:

1. The full task list **quietly condenses** — no alert, no modal
2. The Today tab now shows only 3 items, with a subtle indicator below: *"Showing your top 3. [See all →]"*
3. The rest of the list is behind a single tap — not hidden, but not in view

The transition should take 300ms and feel like the app exhaling.

---

## Reduced View Design

```
┌─────────────────────────────┐
│  Today                      │
│  ─────────────────────────  │
│                             │
│  ● Complete ITIDA proposal  │  ← Priority 1
│  ● Call Michael             │  ← Priority 2
│  ● Review FAB account       │  ← Priority 3
│                             │
│  ·····                      │
│  Showing your top 3.        │
│  See full list →            │
│                             │
└─────────────────────────────┘
```

- Visual calm — nothing flashing, no warning colours
- The "Showing your top 3" line is small and muted — informative, not alarming
- "See full list" is always present — the user retains control

---

## Optional Reset Moment

When transitioning to reduced view, the system may offer (not require) a brief reset:

```
┌─────────────────────────────┐
│  You've got a lot going on. │
│                             │
│  I've highlighted your top  │
│  3 priorities for now.      │
│                             │
│  Want to take 5 minutes     │
│  before starting?           │
│                             │
│  [ Yes, let's reset ]       │
│  [ No — show me what's next ]│
└─────────────────────────────┘
```

This is offered once per overwhelm event, never repeated within the same session.

---

## Exit from Reduced View

The system returns to full view automatically when:
- The task backlog drops below the overwhelm threshold
- The user taps "See full list" (their choice, not a system reset)
- A new day begins

The user can also manually toggle reduced view on/off from the Today tab header.
