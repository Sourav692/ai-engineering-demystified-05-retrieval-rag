# Module 05 — Vector Stores

Storing and searching embeddings in Chroma, FAISS, Astra DB, Pinecone and others, and the index operations (add, update, delete, persist) a vector store supports.

| # | Notebook | You will learn |
|---|---|---|
| 01 | [01_vector_stores_and_index_operations.ipynb](notebooks/01_vector_stores_and_index_operations.ipynb) | Create, query, update, delete and persist a vector store index (canonical lesson) |
| 02 | [02_vector_database_operations.ipynb](notebooks/02_vector_database_operations.ipynb) | Perform core vector database operations with LangChain + Chroma |
| 03 | [03_chromadb.ipynb](notebooks/03_chromadb.ipynb) | Build, persist and query a Chroma vector store end to end |
| 04 | [04_faiss.ipynb](notebooks/04_faiss.ipynb) | Build, save and search a FAISS index |
| 05 | [05_other_vector_stores.ipynb](notebooks/05_other_vector_stores.ipynb) | Use LangChain's InMemoryVectorStore and the common vector store interface |
| 06 | [06_astra_db.ipynb](notebooks/06_astra_db.ipynb) | Use DataStax Astra DB as a managed vector store |
| 07 | [07_pinecone.ipynb](notebooks/07_pinecone.ipynb) | Use Pinecone as a managed vector store |
| 08 | [08_vector_stores_in_practice.ipynb](notebooks/08_vector_stores_in_practice.ipynb) | Ingest, persist, reload and search Chroma collections, including metadata filters |

## Before you run

- `06_astra_db.ipynb` needs an Astra DB database (`ASTRA_DB_API_ENDPOINT`, `ASTRA_DB_APPLICATION_TOKEN`)
  and `07_pinecone.ipynb` a Pinecone key; both libraries are in the `vendors` group.
- `03_chromadb.ipynb` writes sample files to `notebooks/data/` and a `chroma_db/` store; both are
  git-ignored.

## Sources

Extracted from the `AI-ENGINEERING-DEMYSTIFIED` monorepo (tag `pre-multirepo-split-2026-09`). Every notebook's original path is listed in [docs/content-inventory.csv](../../docs/content-inventory.csv).
