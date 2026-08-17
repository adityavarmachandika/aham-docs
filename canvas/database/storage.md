# Storage Options

## Phase 1 — ADI

PostgreSQL remains the structured-data direction for the diary source of truth. Original audio is retained and should be referenced from the relational data rather than treated as an undocumented permanent path.

Possible audio homes remain:

- filesystem on the home host;
- object storage;
- cloud storage if deployment moves to cloud.

## Phase 2 — Vector and memory storage

The notebook now sketches two broad future directions for vector-enabled memory.

### Cloud-oriented option

Messages, transcripts, audio references, and derived memory data could live in a cloud architecture. The note explicitly raises end-to-end encryption as an important requirement if private memory data is stored remotely.

### Local-device option

A device such as Android could keep the user's memory data locally and run a smaller embedding model on-device. The attraction is privacy and speed. The clear trade-off noted in the notebook is reduced availability across the user's other devices unless a synchronization design is added later.

These are alternatives to investigate, not selected architecture.

## Vector lifecycle

The notebook describes a simple lifecycle for a future vector store:

1. insert vectors;
2. query vectors;
3. delete vectors.

Each vector should carry enough metadata to trace it back to the source material. The handwritten note specifically mentions:

- `user_id`;
- transcript/transcription ID.

The exact embedding model, vector database, chunking strategy, dimensions, distance metric, encryption scheme, and synchronization model are still open.

## English text across storage layers

The notebook asks for English transcription or translation to be available to later memory layers. The database design should first choose one canonical English representation and then define what search or graph stores actually copy.

## Knowledge graph later

A graph layer remains part of Phase 2. It should be introduced after the diary foundation is reliable and should reference stable source records rather than replacing them.

## Hosting direction

Preferred:

1. A friend's home system, if practical and reliable.
2. Cloud hosting as fallback.

Future public deployment still needs decisions for backups, TLS, uptime, recovery, durable file storage, and privacy boundaries.
