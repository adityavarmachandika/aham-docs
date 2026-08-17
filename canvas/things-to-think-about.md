# Open Engineering Decisions

The core Phase 1 product and data model are now defined. The remaining decisions are implementation details that should be resolved before API and production contracts are finalized.

## Audio limits and formats

Decide:

- accepted upload/recording formats;
- typical and maximum recording duration;
- maximum file size;
- whether uploads need resumable/multipart support;
- browser recording format normalization strategy.

The initial product target is approximately 1,000 users, so these limits should favor simplicity and predictable processing rather than premature large-scale infrastructure.

## Processing behavior

The current direction is asynchronous processing with observable state and retries where appropriate.

Finalize:

- which transcription/translation provider is used first;
- timeout policy;
- retry count/backoff;
- how provider failures are surfaced;
- when an entry is considered viewable if some derived outputs are still pending;
- whether cleaned text and summary use the same or separate processing jobs.

Source capture must never be lost because a derived processing step fails.

## Diary date UX

The data model supports:

- `recorded_at`;
- `diary_date`;
- multiple covered date ranges.

Finalize the client UX for selecting a backdated `diary_date` and entering/confirming covered ranges.

Phase 1 does not rely on AI date inference. Inferred dates may be introduced later with user confirmation and confidence metadata.

## Keyword search implementation

Define the PostgreSQL full-text-search document and weighting strategy across:

- cleaned English;
- summary;
- original transcript/typed text;
- English translation.

Do not index AI-generated conversational prompts as if they were user memories.

## Authentication details

Still to define at contract level:

- username casing and allowed characters;
- password policy;
- OTP expiry and retry/rate limits;
- password reset flow;
- refresh-token rotation behavior;
- maximum/session-management policy;
- Google/Apple account-linking edge cases.

## Purge operations

The retention period is 30 days. Define:

- purge scheduler frequency;
- handling of failed object deletion;
- idempotent purge behavior;
- backup retention implications;
- audit/logging requirements for permanent deletion.

## Hosting and operations

A friend's home system remains a possible deployment environment, with cloud hosting as fallback.

Before public deployment, define:

- TLS termination;
- backups and restore testing;
- uptime expectations;
- monitoring and alerts;
- durable object storage;
- secrets management;
- external-provider privacy boundaries;
- disaster recovery.

## Future privacy architecture

True end-to-end encryption and a local-only mode are important future directions, but are not Phase 1 claims.

A future design must explicitly resolve:

- device key generation/storage;
- multi-device key synchronization;
- account/device recovery;
- what processing runs on-device;
- what, if anything, the server can decrypt;
- export/migration between server-backed and local-only modes.

## Phase 2 interaction

Conversational AI belongs to Phase 2. Future design can introduce configurable interaction depth, assistant messages, streaming, and voice responses using the Phase 1 capture/message/source model as the foundation.
