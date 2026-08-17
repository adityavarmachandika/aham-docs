# Database Entities

This document defines the current Phase 1 entity model. Exact SQL types, indexes, and JPA contracts are designed separately from these domain responsibilities.

## User

Represents the AHAM account and frequently accessed profile data.

Recommended fields:

- `id`;
- `username`;
- `email`;
- `password_hash` (nullable for OAuth-only accounts);
- `display_name`;
- `date_of_birth`;
- `timezone`;
- `preferred_language`;
- `locale`;
- `email_verified_at`;
- `status`;
- `created_at`;
- `updated_at`;
- `deleted_at`.

Email and username are unique account identifiers. User understanding derived from memories belongs to Phase 2, not as an expanding set of columns on this table.

## Auth identity

Links a user to an external authentication provider.

Representative fields:

- `id`;
- `user_id`;
- `provider`;
- `provider_subject`;
- provider metadata when required;
- `created_at`.

Google and Apple are planned Phase 1 providers.

## User session

Represents one authenticated device/session.

Representative fields:

- `id`;
- `user_id`;
- `refresh_token_hash`;
- `expires_at`;
- `revoked_at`;
- `user_agent` / device metadata;
- `ip_address`;
- `created_at`.

## Auth token

Represents short-lived authentication workflows such as email verification and password reset.

Representative fields:

- `id`;
- `user_id` or pending-registration reference;
- `purpose`;
- `token_hash` / OTP verification state;
- `expires_at`;
- `used_at`;
- `created_at`.

## Diary capture

Represents the draft/pre-finalization lifecycle of one diary entry.

One capture produces at most one finalized diary entry.

Representative fields:

- `id`;
- `user_id`;
- `status` (`ACTIVE`, `COMPLETED`, `ABANDONED`, `DELETED` or equivalent);
- `input_kind` / capture metadata where useful;
- `started_at`;
- `timezone_at_start`;
- `completed_at`;
- `created_at`;
- `updated_at`;
- `deleted_at`.

Captures may be resumed, and a user may have multiple unfinished captures.

## Diary message / input

Represents an ordered unit of input inside a capture.

Phase 1 primarily records user input. The entity intentionally supports a role field so Phase 2 conversational AI can add assistant turns without changing the ownership model.

Representative fields:

- `id`;
- `capture_id`;
- `sequence_no`;
- `role` (`USER`, later `ASSISTANT`);
- `text` for typed input or model messages;
- `created_at`.

A message may have zero or many attachments.

## Attachment

Represents one binary object associated with a diary message.

Representative fields:

- `id`;
- `user_id`;
- `message_id`;
- `type` (`AUDIO`, later `IMAGE`, `VIDEO`, `DOCUMENT`, etc.);
- `mime_type`;
- `storage_provider`;
- `storage_bucket` / namespace;
- `storage_key`;
- `original_filename` when useful;
- `size_bytes`;
- audio duration when applicable;
- `status`;
- provider/file metadata (`JSONB` where appropriate);
- `created_at`;
- `deleted_at`.

The permanent source-of-truth reference is the storage provider + object key, not a public URL.

## Transcript

Represents the durable transcription result of an audio attachment.

Representative fields:

- `id`;
- `attachment_id`;
- `original_text`;
- `source_language`;
- mixed-language metadata when useful;
- `english_translation` (nullable when source is already English);
- `overall_confidence`;
- `provider`;
- `model`;
- provider metadata;
- processing timestamps.

Phase 1 stores the final transcript, not every partial streaming hypothesis.

## Diary entry

Represents the finalized user-facing diary.

Representative fields:

- `id`;
- `user_id`;
- `capture_id`;
- `diary_date`;
- `recorded_at`;
- `timezone_at_recording`;
- `title` (optional, normally AI-generated);
- `cleaned_english_text`;
- `summary`;
- `finalized_at`;
- `created_at`;
- `deleted_at`;
- purge/recovery metadata as needed.

Finalized diary content is not user-editable in Phase 1.

`diary_date` is an organizational date, not a one-entry-per-day key. Multiple entries may have the same date.

## Covered date range

Represents dates discussed within an entry, independently of when the diary was recorded or where it is shown in the calendar.

Representative fields:

- `id`;
- `diary_entry_id`;
- `date_from`;
- `date_to`;
- `source` (`USER`, later `AI`);
- `confirmed`;
- `confidence` for future inferred values;
- `created_at`.

One entry may have several non-contiguous covered ranges.

## Processing job

Represents asynchronous work and retry state when an external/local processor is used.

Representative fields:

- `id`;
- owning resource reference;
- `job_type`;
- `status`;
- `attempt_count`;
- provider/model metadata;
- failure code/message;
- `created_at`;
- `started_at`;
- `completed_at`;
- retry scheduling metadata when needed.

The exact job implementation may later move to a dedicated queue, but durable domain processing state should remain observable.

## Phase 2 source references

Future memory facts, embeddings, and graph relationships should retain provenance through source IDs such as `diary_entry_id`, `message_id`, or `transcript_id`. A vector is a retrieval representation; provenance explains why a derived memory exists.
