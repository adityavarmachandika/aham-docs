# Things to Think About

These are weak or unclear areas visible from the notebook. They are discussion notes, not automatic redesigns.

## Scope

- Is memory search part of the first version or the next step?
- Is summary generation essential at the beginning?
- Is typed diary part of the base or a later feature?
- Does “everything local” mean mandatory local-only operation?

## Audio

- Whole-file upload, chunking, or streaming?
- Synchronous or asynchronous processing?
- Where is the source audio stored?
- Which Telugu-English speech model is intended?

## Authentication

- Email and password, email OTP, Gmail sign-in, or more than one?
- Is login by email, user ID, or both?
- Which profile fields are required?

## Database

- Should voice and typed memories share one common entry concept?
- Are original transcript, English translation, and summary versions of one text or separate records?
- Should `user_details` exist immediately?
- What did the crossed-out `deleted_at` mean?
- What does attachment `entry_id` point to?
- Which relational, vector, graph, and file-storage products work together?

## Knowledge graph

- Which entity and relationship types exist?
- How is connection strength calculated?
- When does confidence require approval?
- Who or what can change the graph schema?

## Privacy and safety

- How are deeply personal memories protected?
- What is the retention and deletion model?
- How should health or mental-health insights avoid false confidence?
- What data can leave a local device when external AI services are used?
