# Memory Search

Memory search is a Phase 2 step from keeping a diary to building a useful memory system.

```mermaid
flowchart LR
    Q[User question or search phrase] --> S[Search service]
    S --> K[Keyword search]
    S --> V[Vector similarity]
    S --> G[Graph connections]
    K --> R[Ranked memories]
    V --> R
    G --> R
    R --> H[Relevant entry or highlighted passage]
```

## Search experiences in the notebook

- Search across stored memories.
- Retrieve a related memory from any day.
- Return transcripts for a calendar query.
- Open one full transcript.
- Highlight the paragraph most related to a search string.

## Future vector flow

The latest notebook adds the basic vector-store lifecycle:

```mermaid
flowchart LR
    T[Transcript or text chunk] --> E[Embedding model]
    E --> I[Insert vector]
    I --> V[(Vector store)]
    Q[Search query] --> QE[Query embedding]
    QE --> V
    V --> R[Related memory references]
    D[Delete source memory] --> X[Delete related vectors]
    X --> V
```

Each stored vector needs metadata that can point back to the owning user and source transcript. The exact metadata schema and chunking rules are not fixed yet.

## Spaces — future idea

A later notebook idea proposes optional **spaces** for separating contexts inside one person's memory system. A user could keep a focused space for something like exam preparation, a project, or another important area instead of mixing every subject into one mental model.

This is a future organizational idea, not an ADI requirement. It still needs decisions about whether spaces are manual, AI-created, isolated search scopes, graph partitions, or simply labels.
