# Brain Dump UX Recommendations

## Entry Point

**Recommendation: The Capture tab should open directly into an active input field.**

The user should never arrive at a blank screen and wonder what to do. The cursor should be in the text field — or the voice recorder should be ready to activate — the moment they tap Capture.

Do not show categories, labels, or type selectors before capture. Classification happens after, invisibly.

---

## Input Surface

### Text Input

- Full-screen text area — no decorative chrome around the input
- Placeholder text should feel like permission, not instruction (see Copy Deck)
- Auto-grow to fill screen as the user types
- No character limit displayed — no visual pressure

### Voice Input

- Single large microphone button, centre of screen
- Activate on tap — do not require press-and-hold (motor coordination challenge)
- Show live waveform while recording — visual confirmation the input is being heard
- Transcription appears in real time below the waveform
- "Done" button stops recording and submits — do not auto-stop on silence

---

## Processing State

After submission:
1. Brief "Processing your thoughts..." state (spinner or animated dots) — never more than 3 seconds
2. Transition directly to the classified output view
3. Do not show the raw input alongside the output — this creates confusion

---

## Output View

Display classified items in grouped cards:

```
[Tasks]          [2 items]
  ○ Call Michael
  ○ Complete ITIDA proposal

[Ideas]          [1 item]
  ✦ Shark Detection enhancement
```

- Each item has a one-tap "looks right" confirm or inline edit
- Provide a single "Add to today" action for all tasks at once — do not require item-by-item confirmation
- "Save all and close" should be the prominent primary action

---

## Failure Tolerance

- If the AI fails to classify, show the raw input as a single uncategorised note — never show an error and discard input
- Allow retroactive editing of classifications from the Memory Vault
