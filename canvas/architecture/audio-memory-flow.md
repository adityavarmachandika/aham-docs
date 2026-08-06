# Audio and Conversation Flow

The immediate product must accept audio. The larger goal is a conversational diary that feels natural rather than like a form.

## Version 1 processing flow

```mermaid
sequenceDiagram
    participant User
    participant Interface
    participant Backend
    participant AudioAI as Audio AI provider
    participant Storage

    User->>Interface: Upload or record audio
    Interface->>Backend: Send audio
    Backend->>Storage: Keep original audio
    Backend->>AudioAI: Request transcription
    AudioAI-->>Backend: Original transcript and confidence
    Backend->>AudioAI: Request English translation
    AudioAI-->>Backend: English translation
    Backend->>Storage: Save diary outputs
    Backend-->>Interface: Show saved diary entry
```

## Desired conversational direction

```mermaid
sequenceDiagram
    participant AI
    participant User

    AI->>User: Ask a natural question
    User-->>AI: Answer by voice
    AI->>AI: Understand the answer and uncertainty
    AI->>User: Ask a relevant follow-up
    User-->>AI: Continue the diary conversation
```

## Current AI direction

- Use a Google or other free API for audio processing when a suitable option is available.
- Prefer streaming where it supports the conversational experience.
- Move toward a local model in the future.
- Store or expose transcription confidence and other uncertainties.

## Still open for API design

- Does Version 1 send a completed recording as one upload, or stream live audio?
- If both are supported, which is built first?
- Is processing synchronous, asynchronous, or a mix?
- What are the maximum audio duration and file size?
- Which audio formats are accepted?
- What happens when the provider disconnects or returns a partial result?
- Where exactly is original audio stored?
