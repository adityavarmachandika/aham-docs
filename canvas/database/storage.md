# Storage Options

## PostgreSQL

The notebook names PostgreSQL for structured data. It may also be able to support some vector or JSON needs, but the notebook does not define the final setup.

## Vector storage

A vector database or vector capability is part of the direction for semantic memory search.

Open choice:

- dedicated vector product;
- vector support inside PostgreSQL;
- a later-stage addition.

## Knowledge graph storage

A graph database or knowledge-graph layer is part of the longer-term design.

Open choice:

- dedicated graph database;
- graph-like tables in relational storage;
- external graph service;
- staged introduction after the base diary works.

## Audio and attachments

Possible homes include:

- local filesystem;
- object storage;
- storage provided by a hosted platform.

The notebook mentions Supabase and local Docker as hosting or database options. Neither is selected here.

## Local-first thought

“Everything local” appears as a strong note. This canvas treats it as an important direction to discuss, not as an implementation fact, because remote access and hosted options also appear in the notebook.
