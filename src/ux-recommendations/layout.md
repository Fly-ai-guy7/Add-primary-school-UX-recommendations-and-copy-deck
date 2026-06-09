# Layout and Navigation

## Navigation Model

**Recommendation: Bottom tab bar with 4 items maximum.**

ADHD users struggle with complex navigation hierarchies. A flat, always-visible tab bar provides constant orientation without requiring the user to remember where things live.

| Tab | Icon | Label |
|---|---|---|
| 1 | Lightning bolt | **Today** |
| 2 | Microphone / keyboard | **Capture** |
| 3 | Magnifying glass | **Memory** |
| 4 | Profile | **Me** |

The active session (Focus Mode / Body Double) should float as a persistent bar above the tab row — always accessible, never blocking content.

---

## Spatial Layout Principles

### Safe Zone Margins

Minimum 24px horizontal margins. ADHD users frequently use devices in motion or when distracted — generous touch targets and margins reduce mis-taps.

### Vertical Rhythm

Use consistent 8px grid spacing. Visual rhythm reduces cognitive load by making layout predictable.

### Information Density

Default to **low density**. Show less, not more. Advanced users can opt into denser views in settings.

---

## Colour Usage

| Colour Role | Recommendation |
|---|---|
| **Primary action** | Single bold accent colour — used only for the one thing the user should do next |
| **Background** | Near-black (dark mode default) or off-white (light mode) — avoid pure white, which increases eye strain |
| **Text** | High contrast at all times — minimum 7:1 ratio |
| **Status indicators** | Green for complete, muted grey for pending, never red for normal states |
| **Urgency** | Avoid red entirely except for genuine errors |

**Dark mode should be the default.** ADHD users often work late, and harsh white screens contribute to eye strain and sleep disruption.

---

## Typography

| Element | Recommendation |
|---|---|
| **Headlines** | Large, bold, single line — conveys the current state immediately |
| **Body** | 16px minimum, generous line height (1.6) |
| **Labels** | All-caps sparingly — only for category labels, never for sentences |
| **Font choice** | Humanist sans-serif (e.g., Inter, DM Sans) — readable at all sizes, not clinical |

---

## Motion and Animation

Use animation sparingly and purposefully:

- **Task completion** — satisfying micro-animation (check + brief pulse) to reinforce the win
- **Screen transitions** — fast, directional slide transitions (150ms) — never spinning loaders
- **Overwhelm state** — slower, gentler transitions into reduced view
- Provide a **Reduce Motion** setting that eliminates all non-essential animation
