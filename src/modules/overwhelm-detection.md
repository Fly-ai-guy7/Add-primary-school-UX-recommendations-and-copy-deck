# Module 8 — Overwhelm Detection

## Purpose

Proactively identify when a user is approaching cognitive overload and automatically reduce the visible task surface before paralysis sets in.

## Trigger Conditions

The system flags overwhelm when it detects:

| Signal | Description |
|---|---|
| **High task volume** | Backlog exceeds a threshold relative to available time |
| **Repeated context switching** | Rapid movement between unrelated tasks |
| **Session stalls** | Long periods of inactivity on an active task |
| **Brain dump spikes** | Sudden large influx of captured items |

## System Response

When overwhelm is detected:

1. **Reduce visible tasks** — all tasks except the top 3 are hidden
2. **Surface top 3 priorities** — AI selects the highest-impact items for now
3. **Offer a reset** — user can trigger a 5-minute grounding exercise before continuing

## Design Rationale

ADHD overwhelm is self-reinforcing: more tasks make it harder to start any task, which creates more backlog, which creates more overwhelm. Overwhelm Detection breaks this loop by intervening before it escalates — reducing the visible problem space until it is manageable again.
