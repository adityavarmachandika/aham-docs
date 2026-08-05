# Audio Memory Flow

```mermaid
sequenceDiagram
    participant User
    participant Interface
    participant Backend
    participant AI
    participant Storage

    User->>Interface: Upload or record audio
    Interface->>Backend: Send audio
    Backend->>Storage: Keep source audio
    Backend->>AI: Request transcription
    AI-->>Backend: Original transcript
    AI-->>Backend: English translation
    AI-->>Backend: Optional summary
    Backend->>Storage: Save memory outputs
    Backend-->>Interface: Show saved memory
```

## Inputs mentioned

- Audio files such as MP3 and WAV.
- Possible full-file upload.
- Possible chunks or streaming.

## Outputs mentioned

- Original transcript.
- English translation.
- Quick summary.
- Original audio.

## Still open

- Whether processing is synchronous or asynchronous.
- Whether streaming is needed at the beginning.
- Whether “two text files” means literal files or two stored text forms.
- Where audio files live.
- Which speech model or provider is used.
