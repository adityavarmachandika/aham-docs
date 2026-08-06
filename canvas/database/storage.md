# Storage Options

## PostgreSQL

PostgreSQL remains the structured-data direction. It can hold the canonical user, diary, transcript, translation, processing, date, and soft-delete data.

## Original audio

Original audio is retained. Its physical home still needs to be chosen:

- filesystem on the home host;
- object storage;
- cloud storage if the deployment moves to cloud.

The database should store a stable reference and metadata rather than treating an undocumented path as permanent architecture.

## English text across storage layers

The notebook asks for English transcription or translation to be available in all relevant database layers. The schema should first choose one canonical English representation, then define what is copied into search or graph stores. This is still a design choice, not a settled duplication rule.

## Vector storage later

Vector search is useful for semantic retrieval but is not part of the agreed Version 1 promise. Options remain:

- vector support inside PostgreSQL;
- a dedicated vector product;
- a later-stage addition.

## Knowledge graph later

A graph layer remains part of the longer-term connected-memory direction. It should be introduced after the base diary and keyword search are working.

## Hosting direction

Preferred:

1. A friend's home system, if it is practical and reliable.
2. Cloud hosting as the fallback.

The deployment design still needs decisions for backups, public networking, TLS, uptime, file durability, and recovery.

## AI location

- Current stage: Google or another free API may process audio.
- Future direction: local model.

The architecture must make the provider replaceable and clearly identify what private data leaves the host.
