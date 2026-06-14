# Notifications UX Recommendations

## Core Rule

**Every notification must earn its place.** ADHD users are already overwhelmed by notification noise. A notification that adds to the noise — rather than cutting through it — damages trust and gets disabled.

Default to fewer notifications. Let users opt into more.

---

## Notification Taxonomy

| Type | Default | Rationale |
|---|---|---|
| **Morning briefing** | ON | Core product loop — the most valuable notification |
| **Evening briefing** | ON | Closes the day loop |
| **Session check-in** | ON (in-app only) | Only fires when a session is active |
| **Follow-up reminders** | ON (1x daily max) | One reminder per item, never repeated |
| **Task deadline** | ON | Only for items with explicit deadlines |
| **Inactivity nudge** | OFF by default | Opt-in only — can feel nagging |
| **Progress milestones** | OFF by default | Opt-in — positive but not universally wanted |

---

## Notification Copy Principles

- **Maximum 8 words** in the notification title
- No emojis in notifications — they can feel infantilising
- No urgent language — no exclamation points, no "URGENT" prefixes
- Always action-oriented — the user should know exactly what they're returning to

---

## Notification Timing

- Morning briefing: user-configured time (default 8:00 AM)
- Evening briefing: user-configured time (default 6:00 PM)
- Never send notifications between **10 PM and 7 AM**
- Group same-day notifications into a digest if more than 3 would fire within 1 hour

---

## Notification Settings Screen

A simple, clearly labelled list. Each notification has:
- Name of the notification
- One-sentence description of when it fires
- Toggle (on/off)
- Timing options where relevant

No categories, no nested menus. A flat list the user can scan in 30 seconds.
