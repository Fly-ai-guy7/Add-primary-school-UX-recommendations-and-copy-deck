# Context Recovery UX Recommendations

## Trigger Conditions

Context Recovery activates when:
- The user returns to the app after **30+ minutes** of inactivity
- The device was locked during an active session
- The app was backgrounded and force-quit

---

## Recovery Screen Design

Context Recovery replaces the normal launch screen. It should load in under 1 second and never make the user wait.

```
┌─────────────────────────────┐
│                             │
│  Welcome back.              │  ← No time-based greeting
│                             │
│  You were working on:       │
│                             │
│  ┌─────────────────────┐    │
│  │  ITIDA Proposal     │    │  ← Task card, prominent
│  │                     │    │
│  │  Last action:       │    │
│  │  Introduction draft │    │
│  │                     │    │
│  │  ~12 min remaining  │    │
│  └─────────────────────┘    │
│                             │
│  [ Resume ]                 │  ← Primary action
│  [ Something changed ]      │  ← Opens task list
└─────────────────────────────┘
```

### Key Design Decisions

- **"Welcome back"** — not "You were away for 2 hours 14 minutes" — no shame, no accounting
- Task card is the largest element on screen — the user's eye goes there first
- **One primary action** — Resume — requires a single tap to re-enter flow
- "Something changed" for when the user needs to reprioritise — surfaces Today tab with full list

---

## Session History

The "Last action" line comes from the session log. If no specific action was recorded (e.g., the session was a Brain Dump), show the last completed item instead. If nothing is available, omit the line entirely — never show a placeholder.

---

## Return After Long Absence (3+ Days)

After a multi-day absence, Context Recovery gives a brief status summary instead:

```
Welcome back.

Since you were last here:
· 3 new tasks added automatically
· 1 deadline passed (Arena Resorts)
· 2 items waiting on you

[ See what needs attention ]
```

No list of everything missed. One action. The system has already triaged.
