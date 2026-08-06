# Current Direction

## Development phases

### Phase 1 / Version 1 — ADI

**ADI — Audio Diary Initiative** is the current development phase.

All Phase 1 development is related to the diary product and the foundation of the application. It includes the CRUD, authentication, storage, processing, and API capabilities required to make the diary dependable.

### Phase 2 — Second brain

Second-brain functionality begins only after ADI is complete. This includes semantic search, knowledge graphs, connected memories, personal patterns, dashboards, reminders, and deeper insights.

## ADI product shape

- The product is intended to become public as it matures.
- The experience should feel like a diary or trusted friend.
- Audio and typed diary input are part of the base.
- Original audio, original transcript, and English translation are retained.
- Entries can be browsed by date, viewed individually, and searched by keyword.
- Backdated and multi-day entries are supported conceptually.
- Soft deletion is required.
- User accounts and authentication are part of the Phase 1 foundation.

## ADI account direction

- Email is mandatory.
- Registration uses email OTP verification.
- Login may use username/password or email/password.
- Authentication is developed after the core diary flow, but remains inside Phase 1.

## ADI AI direction

- An external Google or other free API may be used initially for audio processing.
- A local model is a later direction.
- Transcription confidence and uncertainty should be retained.
- Conversational follow-up and streaming are diary-experience possibilities, but their exact Phase 1 increment is still to be decided.

## CRUD clarification still required

The project now states that Phase 1 covers CRUD foundations. An earlier note said editing is disabled. The update boundary must therefore be confirmed before database and API contracts are finalized.

## Hosting direction

Prefer a friend's home system if practical and reliable. Cloud hosting is the fallback.
