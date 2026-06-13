# Backend Architecture

## Stack

| Technology | Role |
|---|---|
| **FastAPI** (Python 3.12+) | Primary API framework |
| **Pydantic v2** | Request/response validation and serialisation |
| **SQLAlchemy 2** + **Alembic** | ORM and database migrations |
| **Celery** + **Redis** | Async task queue (Brain Dump processing, briefing generation) |
| **Redis** | Caching, session state, rate limiting |

---

## API Design

### REST + WebSocket

The API is primarily REST with WebSocket endpoints for real-time features.

```
/api/v1/
├── auth/
│   ├── POST /session          ← OAuth token exchange
│   └── DELETE /session        ← Sign out
├── brain-dump/
│   ├── POST /                 ← Submit brain dump
│   └── GET /{id}              ← Get classified results
├── tasks/
│   ├── GET /                  ← List tasks (today's view)
│   ├── POST /                 ← Create task
│   ├── PATCH /{id}            ← Update task (status, priority)
│   └── DELETE /{id}           ← Remove task
├── sessions/
│   ├── POST /                 ← Start focus session
│   ├── PATCH /{id}            ← Update session state
│   └── WS /{id}               ← Real-time session WebSocket
├── memory/
│   ├── GET /search            ← Semantic search query
│   ├── GET /{id}              ← Retrieve memory item
│   └── POST /                 ← Manually save to memory
├── briefing/
│   ├── GET /morning           ← Today's morning briefing
│   └── GET /evening           ← Evening briefing
└── users/
    ├── GET /me                ← Current user profile
    └── PATCH /me              ← Update preferences
```

### Authentication

Google OAuth 2.0 and Apple Sign-In are handled via the frontend (next-auth). The resulting JWT is validated on every API request. No username/password authentication in MVP.

### Rate Limiting

Per-user rate limits on AI-intensive endpoints (Brain Dump, Memory search):
- Brain Dump: 60 requests/hour (Free), unlimited (Pro+)
- Memory search: 200 requests/hour (Pro+)

---

## Async Processing

Brain Dump classification and Daily Briefing generation are asynchronous — they run in a Celery worker queue to avoid blocking the API response.

**Brain Dump flow:**
1. `POST /brain-dump/` immediately returns `{ id, status: "processing" }`
2. Client polls `GET /brain-dump/{id}` or uses WebSocket subscription
3. Celery worker calls AI layer, stores results
4. Status updates to `"complete"` with classified output

This ensures the API never blocks on AI inference, and the user sees a smooth processing state rather than a hanging request.

---

## Background Jobs

| Job | Schedule | Description |
|---|---|---|
| `generate_morning_briefing` | User-configured time (default 8AM) | AI briefing generation for each active user |
| `generate_evening_briefing` | User-configured time (default 6PM) | Evening review generation |
| `detect_overwhelm` | Every 30 min during active hours | Check task load and flag overwhelm state |
| `sync_follow_ups` | Every 6 hours | Surface stale follow-ups for reminders |
| `context_recovery_snapshot` | On session end | Store last-known context for recovery |
