# Infrastructure and Deployment

## Hosting Strategy

FocusFlow targets a lean, managed infrastructure stack in MVP — minimising DevOps overhead for a solo founder while maintaining production-grade reliability.

| Component | Service | Rationale |
|---|---|---|
| Frontend (Next.js) | Vercel | Zero-config, global CDN, automatic preview deploys |
| Backend API (FastAPI) | Railway or Render | Managed Python hosting, auto-scaling, simple CI/CD |
| PostgreSQL | Supabase or Neon | Managed Postgres with pgvector support |
| Redis | Upstash | Serverless Redis — pay per use, no cluster management |
| File storage (S3) | AWS S3 (UAE region) | Data residency compliance |
| AI inference | OpenAI API | GPT-5 and Whisper |
| Background jobs | Railway workers | Celery workers alongside the API |
| Monitoring | Sentry (errors) + Betterstack (uptime) | Low-cost, high-signal |

---

## CI/CD Pipeline

```
Push to feature branch
       │
       ▼
GitHub Actions
  ├── Lint (ruff, eslint)
  ├── Type check (mypy, tsc)
  ├── Unit tests (pytest, vitest)
  ├── SAST + dependency scan
  └── Build check
       │
       ▼
PR created → Preview deploy (Vercel) + staging API
       │
       ▼
Merge to main → Production deploy (auto)
```

All production deployments are zero-downtime rolling deploys. Database migrations run as a pre-deploy step with automatic rollback on failure.

---

## Scaling Plan

**MVP (0–2,000 users):**
All components on managed services. Single API instance, single database. Total infrastructure cost: ~EGP 3,000–6,000/month.

**Growth (2,000–20,000 users):**
- API: horizontal scaling via load balancer
- Database: read replicas for Memory Vault search queries
- Vector search: evaluate migration from pgvector to dedicated vector DB (Pinecone)
- AI: caching of common briefing templates to reduce inference calls

**Scale (20,000+ users):**
- Evaluate self-hosted inference for cost reduction
- Egyptian data residency infrastructure for enterprise tier
- Multi-region deployment for Gulf expansion

---

## Uptime and SLO

| Tier | SLO Target | Downtime Budget |
|---|---|---|
| Brain Dump (capture) | 99.9% | ~8.7 hrs/year |
| Focus Mode | 99.5% | ~43.8 hrs/year |
| AI features (briefings, body double) | 99% | ~87.6 hrs/year |

Brain Dump has the highest SLO because it is the primary capture mechanism — losing a user's input is the worst possible failure.

---

## Observability

| Signal | Tool | What We Watch |
|---|---|---|
| Errors | Sentry | Exception rate, AI classification failures, auth errors |
| Uptime | Betterstack | Endpoint availability, response times |
| Business metrics | PostHog | DAU, brain dump completion, session start rate, conversion |
| AI performance | Custom logging | Classification accuracy, response times, cost per user |
| Infrastructure | Railway/Render dashboards | CPU, memory, database connections |
