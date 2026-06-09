# Focus Mode UX Recommendations

## Entry State

When Focus Mode activates:
- All navigation elements fade out
- The current task fills 60% of the vertical screen height
- Estimated time appears small, below the task name
- One button: **Start**

No back button visible. No notification banners. The interface communicates: *this is the only thing that exists right now.*

---

## Active Session Layout

```
┌─────────────────────────────┐
│                             │
│                             │
│   Complete ITIDA proposal   │  ← Task name (large, centred)
│                             │
│        ~25 minutes          │  ← Estimated time (small, muted)
│                             │
│                             │
│  ──────────────────────────  │  ← Thin progress bar (fills over time)
│                             │
│  [  ✓ Done  ]  [ Stuck? ]   │  ← Primary and secondary actions
│                             │
│  Up next: Review FAB account │  ← Next task (very small, bottom)
└─────────────────────────────┘
```

### Progress Bar

- Fills passively based on elapsed time vs. estimate
- Does not turn red when time runs out — it simply fills and stops
- Never creates pressure, only provides orientation

---

## "Done" Interaction

1. User taps **Done**
2. Full-screen success moment — task name, check mark, brief (1.5s) celebration
3. Immediately transitions to the next task start screen
4. No confirmation dialog — the task is done, full stop

---

## "Stuck?" Interaction

Tapping **Stuck?** opens a bottom sheet with three options:
- **"Break it down"** — Momentum Mode activates for this task
- **"Take a 5-minute break"** — starts a rest timer
- **"Skip to next task"** — no explanation required, no guilt

---

## Interruptions

If the user leaves the app mid-session:
- Session pauses silently — no alert
- On return, Context Recovery screen appears (see Context Recovery UX)
- The progress bar reflects only active time

---

## Exiting Focus Mode

No exit button is shown by default — the interface should communicate commitment.

To exit: swipe down from the top, or three-second long-press on the task name. This is intentional friction — enough to be deliberate, not enough to be punishing.
