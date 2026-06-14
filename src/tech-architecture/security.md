# Security and Compliance

## Authentication

| Method | Implementation |
|---|---|
| Google OAuth 2.0 | via next-auth / authjs |
| Apple Sign-In | via next-auth / authjs |
| Session tokens | Short-lived JWT (15min) + long-lived refresh token (30 days) |
| Token storage | HttpOnly cookies — never localStorage |

No username/password authentication. This eliminates credential stuffing and password reuse risks.

---

## Data Encryption

| Layer | Encryption |
|---|---|
| Data in transit | TLS 1.3 minimum |
| Data at rest (PostgreSQL) | AES-256 (managed by cloud provider at disk level) |
| Memory Vault content | Application-level encryption for sensitive fields |
| Voice audio files | Server-side encryption on S3 |
| API keys / secrets | Environment secrets manager (AWS Secrets Manager or equivalent) |

---

## Access Control

- All API routes require authenticated session tokens
- User data is row-level scoped — queries always include `WHERE user_id = :current_user`
- No admin backdoor to user Memory Vault content — privacy is architectural, not policy
- Rate limiting on all AI endpoints to prevent abuse

---

## GDPR Compliance

FocusFlow is designed for GDPR compliance from the start:

| Requirement | Implementation |
|---|---|
| **Right to access** | `/api/v1/users/me/export` — full data export in JSON |
| **Right to erasure** | `/api/v1/users/me` DELETE — full account and data deletion |
| **Data minimisation** | Voice audio deleted post-transcription; logs anonymised after 90 days |
| **Consent** | Explicit consent captured at signup for data processing |
| **Data portability** | JSON export of all user data available at any time |

---

## Egyptian Data Residency

For enterprise deployments and to comply with Egyptian data sovereignty requirements:

- Cloud region: AWS Middle East (UAE) — closest available option
- Self-hosted option: Full stack deployable on Egyptian government cloud infrastructure (EgyptCloud) for regulated clients
- No user data leaves the region for non-AI-inference operations
- AI inference: note that GPT-5 inference routes through OpenAI infrastructure (US); for strict residency requirements, local model alternatives will be evaluated in Version 2

---

## Security Testing

| Activity | Frequency |
|---|---|
| Dependency scanning | Every CI build (Dependabot + pip-audit) |
| SAST (static analysis) | Every CI build (Bandit for Python, ESLint security rules for TS) |
| Penetration testing | Annually, and before any enterprise contract |
| Secret scanning | Pre-commit hooks + GitHub secret scanning |
