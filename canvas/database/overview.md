# Database Overview

The database canvas separates three different jobs rather than forcing everything into one model.

```mermaid
flowchart LR
    APP[AHAM services] --> SQL[(Relational data)]
    APP --> VEC[(Semantic vectors)]
    APP --> KG[(Memory graph)]
    APP --> OBJ[(Audio and attachments)]

    SQL --- VEC
    SQL --- KG
    SQL --- OBJ
```

## Relational data

Useful for users, sessions, diary entries, timestamps, transcripts, and attachment metadata.

## Vector data

Useful for finding memories with similar meaning even when the exact words differ.

## Graph data

Useful for showing connections among people, events, habits, goals, and memories.

## File or object storage

Useful for source audio and future attachments.

## Visual entity map

```mermaid
erDiagram
    USER ||--o{ SESSION : has
    USER ||--o{ MEMORY_ENTRY : owns
    MEMORY_ENTRY ||--o{ TRANSCRIPT : produces
    MEMORY_ENTRY ||--o{ ATTACHMENT : includes
    MEMORY_ENTRY ||--o{ MEMORY_CONNECTION : connects

    USER {
      string user_id
      string email
      string first_name
      string last_name
    }

    MEMORY_ENTRY {
      string entry_id
      datetime created_at
      string input_kind
    }

    TRANSCRIPT {
      string transcript_id
      string language_form
      text content
    }
```

`MEMORY_ENTRY` and `MEMORY_CONNECTION` are shown as helpful canvas concepts, not as notebook-confirmed table names. They make the diagram easier to discuss before a final schema exists.
