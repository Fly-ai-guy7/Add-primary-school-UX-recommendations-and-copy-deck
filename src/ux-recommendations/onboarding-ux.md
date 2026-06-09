# Onboarding UX Recommendations

## Design Principle

**The fastest path to value is the only acceptable path.**

ADHD users will not complete a 10-step onboarding flow. Every additional screen is a dropout risk. The onboarding goal is to reach the first Brain Dump in under 90 seconds.

---

## Onboarding Flow (Maximum 4 Screens)

### Screen 1 — Welcome (10 seconds to read)

```
┌─────────────────────────────┐
│                             │
│  FocusFlow AI™              │
│                             │
│  Your thinking partner      │
│  for getting things done.   │
│                             │
│  No setup. Just start.      │
│                             │
│  [ Continue with Google ]   │
│  [ Continue with Apple ]    │
│                             │
└─────────────────────────────┘
```

No feature list. No bullet points. One claim, one action.

### Screen 2 — First Brain Dump (the product itself)

```
┌─────────────────────────────┐
│                             │
│  What's on your mind        │
│  right now?                 │
│                             │
│  ___________________________│
│  │ Tap to type or speak... ││  ← cursor active
│  │                         ││
│  │                         ││
│  ───────────────────────────│
│                             │
│  🎤  Speak instead          │
│                             │
│  [ Skip for now ]           │
└─────────────────────────────┘
```

This IS the onboarding. The user's first action is using the product's core feature. No explanation precedes it.

### Screen 3 — Briefing Time (if Brain Dump was completed)

```
┌─────────────────────────────┐
│                             │
│  When should I brief        │
│  you each morning?          │
│                             │
│  [ 7:00 ][ 8:00 ][ 9:00 ]  │
│                             │
│  [ Pick a different time ]  │
│  [ Skip — I'll set this up later ] │
└─────────────────────────────┘
```

Quick-select. One decision. Skippable.

### Screen 4 — Ready

```
┌─────────────────────────────┐
│                             │
│  You're set up.             │
│                             │
│  Based on what you told me, │
│  here's your first task:    │
│                             │
│  ┌───────────────────────┐  │
│  │  Complete ITIDA       │  │  ← From the brain dump
│  │  proposal             │  │
│  └───────────────────────┘  │
│                             │
│  [ Start this now ]         │
│  [ See everything ]         │
└─────────────────────────────┘
```

The product has already done work for the user. They see immediate value before they've done anything intentional.

---

## Progressive Disclosure

Features not introduced in onboarding are revealed contextually:
- **Memory Vault** — surfaced first time the user asks a question in Brain Dump ("What did I say about X?")
- **Body Double** — offered the first time a task stalls for 2+ hours
- **Momentum Mode** — offered the first time a user taps "Stuck?"

No feature tours. No tooltips on first visit. Features reveal themselves through use.
