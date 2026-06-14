# Daily Briefing UX Recommendations

## Delivery Mechanism

**Recommendation: Push notification + in-app modal, not a separate screen.**

Briefings should feel like a message from a trusted assistant, not a form to fill in. On notification tap, the briefing opens as a full-screen modal over whatever the user was doing.

---

## Morning Briefing Layout

```
┌─────────────────────────────┐
│  Good morning, Karim.       │  ← Name, no time-based greeting on afternoons
│  Tuesday · 9 Jun            │
│                             │
│  YOUR DAY                   │
│  ─────────────────────────  │
│  ● Complete ITIDA proposal  │  ← Priority 1
│  ● Call Michael             │  ← Priority 2
│  ● Review FAB account       │  ← Priority 3
│                             │
│  2 meetings · ~4.5hrs work  │  ← Workload summary
│                             │
│  3 items waiting on you     │  ← Follow-ups (tap to expand)
│                             │
│  [ Let's start ]            │  ← Primary CTA
│  [ See full list ]          │  ← Secondary (takes to Today tab)
└─────────────────────────────┘
```

### Key Decisions

- **Three priorities only** — never more, never surfaced in a list
- **No calendar event details in the briefing** — just the count and next event time
- **Workload is shown as hours, not task count** — task count creates anxiety, hours creates planning
- **"Let's start"** goes directly into Focus Mode on Priority 1 — zero friction to first action

---

## Evening Briefing Layout

```
┌─────────────────────────────┐
│  Good work today, Karim.    │  ← Always positive, even on low days
│                             │
│  ✓  Completed: 4 tasks      │
│  →  Moved to tomorrow: 2    │
│                             │
│  TODAY'S SCORE: 78          │  ← Progress score (100 = all planned work done)
│  ████████░░  Good day       │
│                             │
│  Tomorrow's top priority:   │
│  Complete ITIDA proposal    │  ← AI-selected #1 for tomorrow
│                             │
│  [ See tomorrow's plan ]    │
│  [ Done for today ]         │
└─────────────────────────────┘
```

### Score Design

- Score is presented as a bar + word label (Excellent / Good / Solid / Light day)
- Never "bad", "poor", or anything negative
- "Light day" is the lowest label — it is neutral and factual
- Score is private — never shown comparatively or shared by default

---

## Dismissal Behaviour

Both briefings can be dismissed with a swipe down. A dismissed morning briefing is accessible from the Today tab for the rest of the day. A dismissed evening briefing is stored in the weekly review history.
