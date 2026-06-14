# Frontend Architecture

## Stack

| Technology | Version | Role |
|---|---|---|
| Next.js | 14+ (App Router) | Primary web framework |
| TypeScript | 5+ | Type safety across all components |
| Tailwind CSS | 3+ | Utility-first styling |
| React Query (TanStack) | 5+ | Server state management, caching |
| Zustand | 4+ | Client-side UI state |
| Framer Motion | — | Micro-animations (with Reduce Motion support) |

---

## Application Structure

```
app/
├── (auth)/
│   ├── sign-in/
│   └── onboarding/
├── (app)/
│   ├── today/          ← Today tab (Focus Mode entry)
│   ├── capture/        ← Brain Dump
│   ├── memory/         ← Memory Vault
│   └── me/             ← Profile, settings, subscription
├── api/                ← Next.js API routes (thin proxy to FastAPI)
└── layout.tsx
```

---

## Key Frontend Decisions

### Server Components by Default
All data-fetching pages use React Server Components. Interactive islands (Brain Dump input, Focus Mode timer, Body Double session) are Client Components.

### Offline-First Brain Dump
The Brain Dump input stores to local IndexedDB first, then syncs to the server. If the user is offline, their brain dump is never lost — it queues for sync on reconnect.

### Real-Time Session State
Focus Mode and Body Double sessions use WebSocket connections for real-time timer sync and check-in events. Falls back gracefully to polling if WebSocket is unavailable.

### RTL Support
RTL (right-to-left) layout is controlled via the HTML `dir` attribute set at the root. All Tailwind utilities use logical properties (`ms-`, `me-`, `ps-`, `pe-`) rather than physical left/right properties, ensuring correct RTL rendering without a separate stylesheet.

### Progressive Web App (PWA)
FocusFlow ships as a PWA from day one:
- Installable on iOS and Android home screens
- Offline Brain Dump capture (IndexedDB queue)
- Push notifications via Web Push API
- Native-like transitions

This defers native app development cost until post-seed while delivering a near-native mobile experience.

---

## Performance Targets

| Metric | Target |
|---|---|
| First Contentful Paint | < 1.2s |
| Time to Interactive | < 2.5s |
| AI response display | < 3s from submission |
| Focus Mode load | < 500ms |

---

## Testing

| Type | Tool |
|---|---|
| Unit / Component | Vitest + React Testing Library |
| E2E | Playwright |
| Accessibility | axe-core (automated) + manual screen reader testing |
