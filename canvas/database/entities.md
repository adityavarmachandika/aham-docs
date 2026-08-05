# Database Entities

This page records the database shapes visible in the notebook without turning them into migrations.

## Users

Fields mentioned across pages:

- `user_id`
- `id`
- `email` or `mail`
- `password`
- `first_name`
- `last_name`
- `name` or `username`
- `age`
- `phone_number`

`id` and `user_id` may mean the same thing or different things. The notebook does not settle it.

## User details

A possible separate area contains:

- nickname;
- summary;
- date of birth;
- extra fields only when required.

Another note suggests keeping commonly fetched data together initially instead of splitting it too early.

## Transcriptions

Fields sketched:

- transcript or transcription ID;
- user ID;
- text;
- created-at time;
- `deleted_at`, crossed out in the notebook.

The notebook also requires original text, English translation, and possibly a summary, but it does not decide whether these are columns, separate records, or files.

## Audio records

Audio must be saved, but no field list or storage model is written.

## Attachments

Future fields sketched:

- attachment ID;
- entry ID;
- attachment;
- type;
- size;
- created-at time.

Examples include links, PDFs, images, and audio.

## Sessions

Fields sketched:

- session ID;
- user ID;
- refresh-token hash;
- expiry;
- device;
- IP address.
