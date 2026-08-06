# Database Entities

This page records the shapes now visible before the detailed schema is designed.

## User

Confirmed direction:

- email is mandatory;
- registration uses email OTP;
- login supports username/password or email/password;
- user details are needed to understand the person over time.

Fields mentioned across the notebook:

- `user_id` or `id`;
- `username`;
- `email`;
- `password`;
- `first_name`;
- `last_name`;
- `age` or `date_of_birth`;
- `phone_number`;
- `nickname`;
- `profile_summary`.

The required subset, optional subset, and the relationship between `id` and `user_id` are not yet finalized.

## Diary item

The visible product should call the concept something simple and diary-oriented. A working internal concept may contain:

- owner or user ID;
- input kind: audio or typed;
- created timestamp;
- user-selected diary date;
- one or more covered dates;
- original audio reference;
- original transcript;
- English translation;
- transcription confidence;
- soft-delete timestamp.

A user may add an item for an earlier date. One item may cover multiple days. The exact date fields and automatic date detection rules still need design.

## Text forms

The Version 1 outputs are:

- original transcript;
- English translation.

A future model may also create summaries or corrected versions. Editing is currently disabled, so a user-edited text version is not required for the initial schema unless it is kept for future compatibility.

## Audio record

Original audio is retained. The database needs metadata and a reference to where the file is stored. Exact audio metadata fields are not yet selected.

## Soft deletion

Entries are not removed immediately. A soft-delete mechanism is required. Restore period and permanent purge behavior are still open.

## Attachments

Later fields sketched:

- attachment ID;
- diary item reference;
- attachment reference;
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
