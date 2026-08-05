# Diagrams

This page collects the key visual views in one place.

## Whole system

```mermaid
flowchart LR
    U[User] --> C[Capture]
    C --> P[Process]
    P --> S[Store]
    S --> R[Retrieve]
    S --> X[Connect]
    X --> I[Insights later]
```

## Memory pipeline

```mermaid
flowchart LR
    A[Audio or text] --> O[Original form]
    A --> E[English form]
    A --> Q[Summary]
    O --> M[Memory entry]
    E --> M
    Q --> M
    M --> D[Date view]
    M --> F[Search]
```

## Storage map

```mermaid
flowchart TB
    ENTRY[Memory entry]
    ENTRY --> SQL[(PostgreSQL)]
    ENTRY --> AUDIO[(Audio storage)]
    ENTRY --> VECTOR[(Vector index)]
    ENTRY --> GRAPH[(Knowledge graph)]
```

## Incremental view

```mermaid
flowchart LR
    V1[Version 1: capture and browse]
    N[Next: search and summaries]
    L[Later: graph and patterns]
    F[Farther ideas: assistant and health insights]
    V1 --> N --> L --> F
```

The detailed versions of these diagrams live in the architecture and database pages.
