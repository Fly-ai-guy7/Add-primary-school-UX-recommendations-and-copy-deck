# Module 1 — Brain Dump Engine

## Purpose

Capture thoughts rapidly and convert them into structured, actionable information — without requiring the user to organise first.

## Inputs

- **Voice** — spoken input processed via speech-to-text
- **Text** — typed or pasted freeform input

## Outputs

The engine classifies input into:

| Output Type | Description |
|---|---|
| **Tasks** | Discrete actions with a clear owner and completion state |
| **Projects** | Multi-step efforts requiring ongoing tracking |
| **Reminders** | Time-sensitive items |
| **Ideas** | Concepts to explore later |
| **Notes** | Contextual information without an immediate action |

## Example

**Input:**
> "I need to call Michael, finish the ITIDA proposal, check the FAB account and remember the shark detection idea."

**Output:**

**Tasks:**
- Call Michael
- Complete ITIDA proposal
- Review FAB account

**Ideas:**
- Shark Detection System enhancement

## Design Principles

- Zero friction capture — the user should never feel blocked by the interface
- Immediate classification — output is structured on submission, not later
- No penalty for messiness — the engine handles clarity so the user doesn't have to
