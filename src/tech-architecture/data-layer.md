# Data Layer

## Primary Database — PostgreSQL

All structured data lives in PostgreSQL. Using pgvector extension for Memory Vault embeddings.

### Schema Overview

```sql
-- Core entities

Users
  id, email, name, subscription_tier, preferences (jsonb),
  created_at, last_active_at

Projects
  id, user_id, name, status, metadata (jsonb), created_at, updated_at

Tasks
  id, user_id, project_id (nullable), title, description,
  status (pending|active|complete|deferred),
  priority (1–5), estimated_minutes, due_date,
  source (brain_dump|manual|ai_generated),
  created_at, completed_at

Notes
  id, user_id, project_id (nullable), content, tags (text[]),
  created_at

BrainDumps
  id, user_id, raw_input (text), input_type (text|voice),
  processing_status (pending|complete|failed),
  classified_at, created_at

Sessions
  id, user_id, task_id, session_type (focus|body_double),
  status (active|paused|complete|abandoned),
  planned_minutes, actual_minutes,
  started_at, ended_at

DailyBriefings
  id, user_id, briefing_type (morning|evening),
  content (jsonb), score (integer nullable),
  delivered_at, dismissed_at

Memories
  id, user_id, source_type (brain_dump|note|session|task),
  source_id, content (text),
  embedding (vector(1536)),  ← pgvector
  created_at

ActivityLogs
  id, user_id, event_type (text), metadata (jsonb),
  created_at
```

---

## Caching — Redis

| Cache Key Pattern | TTL | Purpose |
|---|---|---|
| `briefing:{user_id}:{date}:morning` | 24h | Today's morning briefing (generated once) |
| `briefing:{user_id}:{date}:evening` | 12h | Evening briefing |
| `tasks:{user_id}:today` | 5m | Today's prioritised task list |
| `overwhelm:{user_id}` | 30m | Overwhelm state flag |
| `session:{session_id}:state` | Session TTL | Real-time session state |

---

## File Storage — S3-Compatible

Voice brain dump audio files are stored in S3-compatible object storage (AWS S3 or locally hosted MinIO for Egyptian data residency). Audio is deleted after transcription unless the user explicitly saves it.

---

## Data Retention Policy

| Data Type | Retention |
|---|---|
| Active user data | Indefinite while account is active |
| Voice audio (post-transcription) | 7 days, then deleted |
| Activity logs | 90 days |
| Deleted account data | 30 days, then purged |
| Anonymised analytics | 24 months |

---

## Backup and Recovery

- PostgreSQL: daily automated snapshots, 30-day retention
- Point-in-time recovery (PITR) enabled for the previous 7 days
- Redis: AOF persistence for session state durability
- RTO target: < 4 hours | RPO target: < 1 hour
