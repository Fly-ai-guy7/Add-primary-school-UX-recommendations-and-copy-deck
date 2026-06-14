# Module 4 — ADHD Memory Vault

## Purpose

Act as an externalised long-term memory — storing all user context and making it retrievable through natural language queries, without the user needing to remember where they stored something.

## What It Stores

- Notes and brain dumps
- Projects and tasks
- Meeting summaries
- Decisions made
- Ideas and concepts

## Retrieval

Users query the vault in plain language. The system returns the most relevant stored context.

**Example queries:**

```
"What did I decide about Arena Resorts?"
"Find my notes about Reyeye."
"What was my idea about AI tourism?"
```

## Design Rationale

ADHD often impairs working memory — the ability to hold context in mind while working. The Memory Vault externalises this function entirely. Nothing needs to be remembered; everything can be retrieved. The act of recall becomes a search rather than a mental effort.

## Privacy

All stored content is encrypted at rest. The vault is personal and never shared without explicit user action.
