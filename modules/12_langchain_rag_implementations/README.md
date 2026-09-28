# Module 12 — LangChain RAG Implementations

LangChain-specific retrieval features on PGVector: metadata-filtered search and the Indexing API with a record manager.

| # | Notebook | You will learn |
|---|---|---|
| 01 | [01_filtered_search_pgvector.ipynb](notebooks/01_filtered_search_pgvector.ipynb) | Combine semantic search with metadata filters on PGVector |
| 02 | [02_indexing_api.ipynb](notebooks/02_indexing_api.ipynb) | Keep a vector store in sync with its sources using the LangChain Indexing API and a record manager |

## Before you run

Both notebooks need PostgreSQL with pgvector. From this module's `notebooks/` folder:

```bash
docker compose up -d      # builds postgres/ (pgvector) and listens on localhost:5433
```

Check the connection string in each notebook against the port you expose. The corpus is
`data/sample/bella_vista.txt`.

Source acknowledgement: these notebooks follow the Udemy course *LangChain in Action: Develop
LLM-Powered Applications*.

## Sources

Extracted from the `AI-ENGINEERING-DEMYSTIFIED` monorepo (tag `pre-multirepo-split-2026-09`). Every notebook's original path is listed in [docs/content-inventory.csv](../../docs/content-inventory.csv).
