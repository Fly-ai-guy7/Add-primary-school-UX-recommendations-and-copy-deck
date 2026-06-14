# Momentum Mode UX Recommendations

## Trigger Points

Momentum Mode can be activated from:
- The **Stuck?** button inside Focus Mode
- A **"Can't start?"** prompt that appears after a task has been in "today" for over 2 hours without being touched
- Manually, by long-pressing any task

---

## Interaction Flow

Momentum Mode is a focused conversation — not a new screen. It overlays the current view as a bottom sheet.

**Step 1: Acknowledge**
```
"This one feeling stuck?"

[ Yes ]   [ Not exactly — let me explain ]
```

**Step 2: Reduce**
```
"What's the smallest possible
 first action on this?"

 ___________________________________
│ e.g. Open the document            │
│                                   │

[ That works ]
```

- The user types a micro-step
- No validation — any text is accepted
- If the user leaves it blank and taps "That works", the system provides a suggestion

**Step 3: Start**
```
"Okay. Just do that one thing.
 I'll check in when you're done."

[ Start: Open the document ]
```

Focus Mode activates with the micro-step as the active task. The original task is queued as "next."

---

## Recovery Without Momentum Mode

If a user wants to skip Momentum Mode entirely, every task also has a plain **"Start"** button that activates Focus Mode directly. Momentum Mode is offered, never forced.

---

## Visual Design

- Bottom sheet, not full screen — does not feel like a new mode or commitment
- Conversational line spacing — the questions read as spoken, not clinical
- One question per step — never two fields on screen simultaneously
