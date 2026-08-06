# Current Direction

The latest notebook pages clear up much of the base product direction.

## Product shape

- Version 1 is the base project setup.
- Development will be incremental.
- The product is intended to become public as it matures.
- The user-facing experience should feel like a diary or a trusted friend, not like a technical “second brain.”
- The internal database or API name can be different from the simple name shown to users.

## Version 1 promise

- Upload or record audio.
- Add a typed diary entry.
- Store the original transcript.
- Store an English translation.
- Keep the original audio.
- Browse diary entries by date.
- Open and view one diary entry.
- Search by keyword.

Editing is disabled for now. Opening and editing an entry may be added later if it becomes necessary.

## Conversation direction

The long-term interaction should feel like a real conversation:

1. The AI asks a natural question.
2. The user answers by voice.
3. The AI asks a relevant follow-up based on the answer.
4. The conversation becomes the diary material.

Streaming appears important for this experience, but the exact Version 1 transport is not yet fixed.

## Audio and AI direction

- For the current stage, a Google or other free API may process audio when a suitable streaming option is available.
- The future aim is to use a local model.
- Generated output should retain uncertainty information such as transcription confidence.

## Authentication direction

- Email is mandatory.
- Registration uses email OTP verification.
- Login may use either username and password or email and password.
- Login and registration will be built after the main diary functionality during Version 1 development.

## Diary time behavior

- A user can add a diary entry for an earlier date.
- Entries are stored with timestamps.
- Times should be displayed in the timezone of the user's device.
- One diary entry may cover multiple days.
- Detecting the covered dates automatically is preferred; explicit user-provided dates are the fallback. The exact input and storage shape still needs to be designed.

## Data behavior

- Editing diary entries is disabled at the current stage.
- Entries are not deleted immediately; soft delete is used.
- User information is needed because AHAM is intended to understand the person over time. The exact required profile fields are still to be selected.
- The notebook asks for an English representation to be available across the database or memory layers because it may help future ideas. The canonical source and duplication strategy still need to be chosen during database design.

## Hosting direction

The preferred first host is a friend's home system if practical. Cloud hosting is the fallback.
