# Technical Architecture — FocusFlow AI™

This document describes the technical design of FocusFlow AI™ at the system level, covering the full stack, AI layer, data model, integrations, and infrastructure decisions.

---

## Architecture Philosophy

FocusFlow is built on three principles:

1. **AI-first, not AI-added** — The AI layer is not a feature bolted onto a to-do list. Every module is designed around AI capabilities from the ground up.

2. **Model-agnostic** — The AI abstraction layer allows switching between GPT-5, Claude, Gemini, or local models without changes to the product layer. This de-risks dependency on any single provider.

3. **Privacy by design** — All user data is encrypted at rest and in transit. Memory Vault content is never used for training external models. Egyptian data residency is supported for enterprise.

---

## System Diagram (Overview)

```
┌──────────────────────────────────────────────────────────┐
│                    CLIENT LAYER                           │
│  Next.js (Web)  │  iOS / Android (React Native — v2)    │
└─────────────────────────┬────────────────────────────────┘
                          │ HTTPS / WebSocket
┌─────────────────────────▼────────────────────────────────┐
│                    API LAYER (FastAPI)                    │
│  Auth  │  Brain Dump  │  Tasks  │  Sessions  │  Memory  │
└────────┬────────────────────────────────────┬────────────┘
         │                                    │
┌────────▼─────────┐                ┌─────────▼────────────┐
│   AI LAYER       │                │  DATA LAYER          │
│  Orchestrator    │                │  PostgreSQL (primary) │
│  GPT-5 / Claude  │                │  Redis (cache/queue)  │
│  STT Engine      │                │  S3-compatible (files)│
│  Embeddings      │                │  Vector DB (memories) │
└──────────────────┘                └──────────────────────┘
```

---

## Sections

- [Frontend](./frontend.md)
- [Backend API](./backend.md)
- [AI Layer](./ai-layer.md)
- [Data Layer](./data-layer.md)
- [Security and Compliance](./security.md)
- [Infrastructure and Deployment](./infrastructure.md)
