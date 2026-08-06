# Things to Think About

The project boundary is now clear:

- **Phase 1 / Version 1:** ADI — Audio Diary Initiative.
- **Phase 2:** second-brain features.

The following choices remain before the Phase 1 database and API contracts can be finalized.

## CRUD update boundary — highest priority

Earlier notes disabled editing, while the latest clarification says Phase 1 includes all CRUD foundations.

Confirm what `UPDATE` means in ADI:

- edit typed diary content;
- edit diary date or title only;
- edit original transcript;
- edit English translation;
- replace audio;
- restore a soft-deleted entry;
- or expose an internal update model while initially hiding editing in the UI.

## Main diary resource

- Final user-facing name: Diary, Diary entry, Journal, or something else?
- Final internal API and table name?

## Audio and processing

- Completed upload, live streaming, or both?
- Which comes first?
- Synchronous, asynchronous, or mixed processing?
- Accepted audio formats?
- Maximum duration and file size?
- Retry, partial transcript, and provider-failure behavior?

## Text outputs

- Is the original transcript verbatim or cleaned?
- Is English a direct translation or a readable rewrite?
- Is confidence stored for the full transcript, segments, or words?
- Is summary definitely outside ADI?

## Dates

- UTC storage plus device-timezone display?
- Separate creation time and diary date?
- Date range or separate covered-date rows for multi-day entries?
- Can automatic date detection be corrected?

## Users and authentication

- Required and optional profile fields?
- Username uniqueness, casing, and character rules?
- Password policy?
- OTP expiry and retry limits?
- Password reset and account recovery?
- Session and refresh-token behavior?

## Soft delete

- Restore period?
- User-visible recycle bin?
- Permanent purge schedule?
- Purge of audio and all derived data together?

## Hosting and privacy

- Can the home host support public TLS, backups, uptime, monitoring, and durable file storage?
- What is the exact cloud fallback?
- What audio or text may leave the host for the external AI API?
- Encryption at rest?
- Full user export?

Once these Phase 1 decisions are made, detailed database design and API contracts can proceed without bringing Phase 2 into the scope.
