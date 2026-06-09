# Database Entities

The following core entities form the FocusFlow data model:

| Entity | Description |
|---|---|
| **Users** | Account data, preferences, subscription tier |
| **Projects** | Multi-task efforts with status and metadata |
| **Tasks** | Discrete actions with priority, status, and due dates |
| **Notes** | Freeform stored content linked to projects or standalone |
| **BrainDumps** | Raw captured input before classification |
| **Sessions** | Focus session records (start, end, task, body double activity) |
| **DailyBriefings** | Morning and evening briefing snapshots |
| **Memories** | Processed, searchable knowledge store (Memory Vault) |
| **ActivityLogs** | Audit trail for user actions and AI decisions |

---

## Key Relationships

```
Users → Projects → Tasks
Users → BrainDumps → [Tasks | Notes | Ideas]
Users → Sessions → Tasks
Users → Memories
Users → DailyBriefings
```

All entities are scoped to the owning user. Cross-user data access is not supported in MVP.
