# Module 06 — Indexing Strategies

Changing *what* is indexed: multi-representation and parent-document indexing, hierarchical indices, hypothetical prompt embeddings, document augmentation and contextual chunk headers.

| # | Notebook | You will learn |
|---|---|---|
| 01 | [01_multi_representation_indexing.ipynb](notebooks/01_multi_representation_indexing.ipynb) | Embed a summary of each document but return the full document (multi-vector retriever) |
| 02 | [02_parent_document_retrieval.ipynb](notebooks/02_parent_document_retrieval.ipynb) | Embed small child chunks but return their larger parent chunk |
| 03 | [03_parent_document_retriever_postgres.ipynb](notebooks/03_parent_document_retriever_postgres.ipynb) | Run a parent-document retriever with a persistent Postgres docstore |
| 04 | [04_hierarchical_indices.ipynb](notebooks/04_hierarchical_indices.ipynb) | Index summaries and detailed chunks in two tiers and search top-down (RAG Techniques anthology) |
| 05 | [05_hypothetical_prompt_embeddings.ipynb](notebooks/05_hypothetical_prompt_embeddings.ipynb) | Pre-generate hypothetical questions per chunk at index time (HyPE) (RAG Techniques anthology) |
| 06 | [06_document_augmentation.ipynb](notebooks/06_document_augmentation.ipynb) | Augment the index with generated questions per document/fragment (RAG Techniques anthology) |
| 07 | [07_contextual_chunk_headers.ipynb](notebooks/07_contextual_chunk_headers.ipynb) | Prepend document-level context headers to chunks before embedding (RAG Techniques anthology) |

Runnable script companions in `notebooks/`: `hierarchical_indices.py`, `HyPE_Hypothetical_Prompt_Embeddings.py`, `document_augmentation.py`.

## Before you run

- Concept explainer: [Indexing_Techniques_Explained.md](assets/Indexing_Techniques_Explained.md).
- `03_parent_document_retriever_postgres.ipynb` uses the restaurant corpus in `data/sample/restaurant/`
  and PostgreSQL with pgvector (start one with the `docker-compose.yaml` in module 12).
- `07_contextual_chunk_headers.ipynb` uses Cohere reranking (`CO_API_KEY`).
- `hierarchical_indices.py`, `HyPE_Hypothetical_Prompt_Embeddings.py` and `document_augmentation.py`
  are runnable script versions of the anthology notebooks.

## Sources

Extracted from the `AI-ENGINEERING-DEMYSTIFIED` monorepo (tag `pre-multirepo-split-2026-09`). Every notebook's original path is listed in [docs/content-inventory.csv](../../docs/content-inventory.csv).

Notebooks marked *RAG Techniques anthology* come from Nir Diamant's [RAG_Techniques](https://github.com/NirDiamant/RAG_Techniques) repository and remain under its non-commercial licence: see [docs/third_party/RAG_Techniques_LICENSE.txt](../../docs/third_party/RAG_Techniques_LICENSE.txt). Changes made here: file names and data/image paths only.
