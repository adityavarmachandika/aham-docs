# Database Overview

The current database design is for **Phase 1: ADI — Audio Diary Initiative**.

Its job is to provide a reliable diary source of truth and the CRUD foundation of the application. Phase 2 vector and graph models should not drive the Phase 1 schema prematurely.

```mermaid
flowchart LR
    APP[ADI services] --> SQL[(PostgreSQL diary source of truth)]
    APP --> OBJ[(Original audio storage)]
    SQL -. Phase 2 references later .-> VEC[(Vector search)]
    SQL -. Phase 2 references later .-> KG[(Knowledge graph)]
```

## Phase 1 data areas

- users and profiles;
- email verification;
- credentials and sessions;
- diary entries;
- diary dates and multi-day coverage;
- typed content;
- original transcripts;
- English translations;
- confidence information;
- original audio metadata and file references;
- processing jobs and failure states;
- keyword-search support;
- soft deletion and later purge.

## Working visual model

```mermaid
erDiagram
    USER ||--o{ SESSION : has
    USER ||--o{ DIARY_ENTRY : owns
    USER ||--o{ EMAIL_VERIFICATION : verifies
    DIARY_ENTRY ||--o{ TEXT_OUTPUT : contains
    DIARY_ENTRY ||--o| AUDIO_RECORD : keeps
    DIARY_ENTRY ||--o{ COVERED_DATE : may_cover
    DIARY_ENTRY ||--o{ PROCESSING_JOB : processes

    USER {
      string user_id
      string username
      string email
    }

    DIARY_ENTRY {
      string entry_id
      string input_kind
      datetime created_at
      datetime deleted_at
    }

    TEXT_OUTPUT {
      string text_id
      string text_kind
      text content
      number confidence
    }
```

These names remain working concepts until the detailed schema is approved.

## Phase 2 boundary

Vector embeddings and graph entities may later reference stable Phase 1 diary IDs. They do not need to be implemented during ADI.
