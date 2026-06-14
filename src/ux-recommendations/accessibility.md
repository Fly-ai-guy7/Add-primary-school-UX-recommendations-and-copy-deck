# Accessibility Recommendations

## Why Accessibility Is Central, Not Supplementary

ADHD frequently co-occurs with dyslexia, visual processing differences, anxiety, and motor coordination challenges. Accessibility features are not edge-case accommodations — they serve a significant portion of the core user base.

---

## Text and Readability

| Recommendation | Specification |
|---|---|
| Minimum body font size | 16px |
| Line height | 1.6 minimum |
| Maximum line length | 65 characters |
| Font weight for body | Regular (400) — avoid light weights |
| Letter spacing | Slightly increased for body (0.02em) |
| Avoid justified text | Left-aligned always |

**Dyslexia-friendly font option:** Offer OpenDyslexic or Lexie Readable as an alternative font in settings. Do not make this the default — it is an opt-in preference.

---

## Colour and Contrast

- All text meets WCAG AA minimum (4.5:1) — target AAA (7:1) for body text
- Never use colour alone to convey status — always pair with shape or label
- Provide a high-contrast mode that increases background/foreground contrast beyond defaults
- Colour blind safe palette — test all status indicators against deuteranopia and protanopia simulations

---

## Motor Accessibility

| Recommendation | Specification |
|---|---|
| Minimum touch target size | 44×44px (Apple HIG minimum) |
| Spacing between adjacent targets | 8px minimum |
| Avoid swipe-only gestures | All swipe actions have tap alternatives |
| Avoid press-and-hold | No functionality locked behind hold gestures |

---

## Cognitive Load Reduction

- **Reduce Motion setting** — disables all non-essential animation
- **Simplified Mode** — removes all decorative elements, increases text size, shows only task name and action button
- **Reading Mode** — for Memory Vault and briefings, strip navigation and show only content

---

## Screen Reader Support

- All interactive elements have descriptive labels
- Dynamic content (e.g., session timer, processing state) announces updates via `aria-live`
- Voice input alternative available for all text entry points

---

## RTL Language Support

FocusFlow targets Egyptian Arabic speakers. Full RTL (right-to-left) layout support is required:
- Mirrored navigation (tab bar icons and labels)
- Mirrored task cards and progress bars
- Arabic font pairing tested for readability at all sizes
- Dates and numbers displayed per regional convention
