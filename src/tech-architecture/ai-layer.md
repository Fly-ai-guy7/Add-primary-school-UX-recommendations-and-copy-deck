# AI Layer Architecture

## Design Principle — Model Agnostic

The AI layer is abstracted behind a single `AIProvider` interface. No product code calls OpenAI, Anthropic, or Google directly. This means models can be swapped, combined, or fine-tuned without touching the API or frontend.

```python
class AIProvider(Protocol):
    async def classify_brain_dump(self, text: str, user_context: UserContext) -> BrainDumpResult: ...
    async def generate_briefing(self, user_data: UserData, briefing_type: str) -> Briefing: ...
    async def prioritise_tasks(self, tasks: list[Task], context: UserContext) -> list[Task]: ...
    async def semantic_search(self, query: str, memories: list[Memory]) -> list[Memory]: ...
    async def generate_body_double_response(self, context: SessionContext) -> str: ...
    async def transcribe_audio(self, audio: bytes) -> str: ...
```

---

## Current Model Configuration (MVP)

| Function | Model | Notes |
|---|---|---|
| Brain Dump classification | GPT-5 | Primary — intent classification + entity extraction |
| Task prioritisation | GPT-5 | Reasoning-heavy; benefits from larger model |
| Daily Briefing generation | GPT-5 | Structured output with user context |
| Body Double responses | GPT-5 (lower temp.) | Warm, consistent, non-variable tone |
| Memory Vault search | Embeddings (text-embedding-3-large) | Semantic vector search |
| Voice transcription | Whisper (large-v3) | High accuracy, Arabic support |
| Overwhelm detection | Rule-based + lightweight classifier | Does not require LLM — reduces cost |

---

## Brain Dump Classification Pipeline

```
User input (text/audio)
       │
       ▼
[STT if voice] → transcript
       │
       ▼
[Pre-processing] → clean, split, language detect
       │
       ▼
[Classification prompt] → GPT-5
       │
       ▼
[Structured output parser] → Pydantic model
       │
       ▼
BrainDumpResult {
  tasks: [Task],
  ideas: [Idea],
  notes: [Note],
  reminders: [Reminder],
  projects: [Project]
}
```

**Prompt design principles:**
- System prompt includes user's active projects and recent context for smarter classification
- Output is forced to JSON schema via function calling / structured outputs
- Fallback: if classification fails, input is saved as a single unclassified note — nothing lost

---

## Memory Vault — Semantic Search

The Memory Vault uses vector embeddings for retrieval, not keyword search.

1. On every Brain Dump result, each item is embedded and stored in the vector database
2. On Memory search query, the query is embedded and a cosine similarity search is performed
3. Top-k results are returned, re-ranked by recency × relevance

**Vector database:** pgvector (PostgreSQL extension) — keeps the stack unified, avoids a separate service in MVP. Migrates to Pinecone or Weaviate if scale requires it.

---

## Prompt Engineering Standards

All prompts are:
- Versioned (prompt version stored alongside AI responses for auditability)
- Tested with ADHD-specific edge cases (fragmented input, multi-language, voice transcription artifacts)
- Evaluated on classification accuracy before deployment
- Stored in a prompt registry, not hardcoded in application code

---

## Future AI Roadmap

| Capability | Timeline | Description |
|---|---|---|
| Arabic-language fine-tuning | Post-seed | Fine-tune on Arabic ADHD content for improved classification |
| On-device inference | Version 3 | Lightweight model for offline Brain Dump processing |
| Multi-modal input | Version 2 | Photo capture of handwritten notes |
| Predictive prioritisation | Version 2 | Learn user patterns to improve daily priority selection |
