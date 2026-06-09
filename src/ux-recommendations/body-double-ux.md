# AI Body Double UX Recommendations

## Activation

Body Double sessions are initiated from:
1. The **Today** tab — "Work with AI support" option under any task
2. The **Focus Mode** active session — tap avatar to activate
3. A standalone "Start a session" button on the Today tab

When activated, a small persistent avatar appears in the top corner of the screen — a subtle but constant visual presence.

---

## Session Initiation Screen

```
┌─────────────────────────────┐
│                             │
│         [  Avatar  ]        │  ← Simple, non-anthropomorphic avatar
│                             │
│  "What are we working on    │
│   today?"                   │
│                             │
│  Complete ITIDA proposal    │  ← Pre-populated from current task
│                             │
│  "How long should we work   │
│   for?"                     │
│                             │
│  [ 15 min ][ 25 min ][ 45 ] │  ← Quick-select, no custom entry needed
│                             │
│  [ Let's go ]               │
└─────────────────────────────┘
```

### Avatar Design

- Abstract, geometric — not a humanoid face
- Calm, still animation (gentle pulse) — not distracting
- Never uses a human name — "Your Focus Partner" or just the FocusFlow logo avatar
- Avoids anything that could feel infantilising or patronising

---

## Check-In Interaction

At the midpoint of a session, a subtle notification appears:

```
┌─────────────────────────────┐
│  Halfway there. How's it    │
│  going?                     │
│                             │
│  [ Good — keep going ]      │
│  [ Need help ]              │
└─────────────────────────────┘
```

- This appears as a non-blocking overlay — the user can ignore it and it disappears after 30 seconds
- "Need help" opens the Stuck? flow from Focus Mode
- "Keep going" dismisses with a single tap

---

## Session Completion

```
┌─────────────────────────────┐
│                             │
│  Session complete.          │
│  25 minutes of solid work.  │
│                             │
│  [ ✓ ]                      │  ← Brief animation
│                             │
│  [ Start another session ]  │
│  [ I'm done for now ]       │
└─────────────────────────────┘
```

No score. No metrics. Just acknowledgement.

---

## Tone Boundary

The Body Double never:
- Expresses disappointment
- Uses urgency ("You only have 3 hours left!")
- Sends unsolicited motivational quotes
- Pings the user outside of check-ins

It is present when needed, invisible when not.
