# Things to Think About

Most of the base product direction is now clearer. These are the remaining choices that affect database design, API contracts, or the first public deployment.

## Name and resource shape

- What simple user-facing word should represent one saved diary item: **Diary**, **Diary entry**, **Journal**, or another word?
- What stable internal resource name should the database and API use?

## Conversation and audio

- Is the conversational follow-up experience part of Version 1, or the next increment after the base diary flow?
- Does Version 1 upload a completed recording, stream live audio, or support both?
- Is audio processing synchronous, asynchronous, or mixed?
- What are the accepted formats, maximum file size, and maximum duration?
- How are partial transcripts, retries, provider failure, and disconnected streams handled?

## Text outputs

- Is the original transcript verbatim or cleaned?
- Is the English output a direct translation or a rewritten readable form?
- Is summary generation explicitly excluded from Version 1?
- Where is transcription confidence stored: whole transcript, segment, or word level?
- Which store owns the canonical English text, and what do vector or graph stores copy?

## Dates and time

- Store timestamps in UTC and display them in the device timezone, or store another representation?
- Does a diary item need a separate user-selected diary date in addition to creation time?
- How should one item covering multiple days be represented?
- Can automatic date detection be corrected when it is wrong?

## Users and authentication

- Which profile fields are required at registration and which are optional later?
- Must usernames be unique, and are they case-sensitive?
- What are the password, OTP expiry, retry, and account-recovery rules?
- Which session model is used for the public product?

## Editing and deletion

- Editing is disabled now, but should the schema reserve text-version history for later?
- How long can a soft-deleted item be restored?
- When and how is permanent purge performed?
- Does purge remove audio, text, search indexes, and future graph data together?

## Hosting and privacy

- Can the friend's home system provide reliable public networking, TLS, backups, uptime, and storage durability?
- What is the cloud fallback provider?
- What personal data may be sent to the current external audio API?
- Are audio and diary text encrypted at rest?
- How can a user export all diary data?

## Later graph design

The knowledge graph can wait until the base diary and keyword search are proven. Before it starts, define the first node types, relationship types, correction flow, and confidence rules.
