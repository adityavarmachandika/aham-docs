# Current Direction

This document records the current engineering direction for AHAM. Historical notebook ideas remain available in the archive, but the decisions below are the active specification.

## Product boundary

### Phase 1 — ADI

Build a dependable private diary system with:

- audio and typed input;
- source preservation;
- transcription and English translation;
- faithful cleaned-English output;
- summary and optional title;
- date-based browsing and keyword search;
- immutable finalized entries;
- soft delete, restore, and purge;
- users, verification, authentication, sessions, storage, and processing infrastructure.

### Phase 2 — memory intelligence

Introduce natural AI conversation, semantic search, connected memories, evidence-backed user understanding, knowledge graphs, and local/on-device intelligence only after the diary foundation is stable.

## Interaction model

Phase 1 captures what the user chooses to say or type. It does not require the AI to understand and respond conversationally in real time.

Conversational behavior is a Phase 2 capability. The future interaction level may be configurable, including an effectively non-interactive mode and progressively deeper follow-up behavior.

## Diary semantics

AHAM does not assume one diary entry per day.

A user may create zero, one, or many entries on a given date. The system records:

- actual capture start time;
- capture timezone;
- diary/calendar date;
- one or more covered date ranges mentioned by the user.

Backdating is a first-class capability, not an edge case.

## Content policy

The source content is preserved. Phase 1 keeps finalized diary content immutable from the user's perspective.

Derived cleaned English exists to express the user's meaning clearly, not to reinterpret the user's history. The system may improve grammar and readability, but it must not add unsupported facts or motivations.

## Technical direction

- React web client first;
- Java / Spring Boot backend;
- Python may be used for AI-related processing;
- PostgreSQL as structured source of truth;
- private object storage for audio and future attachments;
- storage access hidden behind an application abstraction so Cloudflare R2 and local/self-hosted options remain interchangeable;
- asynchronous processing and retries where appropriate;
- initial operating target of roughly 1,000 users.

## Privacy direction

Phase 1 should use private objects, short-lived access URLs, TLS, strict ownership checks, and encryption at rest.

A future local-only mode where memories never leave the user's device remains a strategic direction. True end-to-end encrypted multi-device synchronization requires a dedicated key and recovery design and is intentionally not treated as solved by the Phase 1 server architecture.
