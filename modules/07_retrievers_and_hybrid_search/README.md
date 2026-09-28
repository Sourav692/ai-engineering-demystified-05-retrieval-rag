# Module 07 — Retrievers and Hybrid Search

How candidates are selected: retriever interfaces, dense + sparse (BM25) hybrid search, fusion retrieval, MMR and metadata filtering.

| # | Notebook | You will learn |
|---|---|---|
| 01 | [01_retrievers.ipynb](notebooks/01_retrievers.ipynb) | Use LangChain retrievers on Chroma: similarity, threshold, MMR, multi-query, compression and ensemble |
| 02 | [02_dense_sparse_hybrid_retrieval.ipynb](notebooks/02_dense_sparse_hybrid_retrieval.ipynb) | Combine a dense (vector) and sparse (BM25) retriever with EnsembleRetriever |
| 03 | [03_hybrid_search_rag.ipynb](notebooks/03_hybrid_search_rag.ipynb) | Build a RAG chain on top of BM25 + vector hybrid search |
| 04 | [04_fusion_retrieval.ipynb](notebooks/04_fusion_retrieval.ipynb) | Fuse normalised vector and BM25 scores into one ranking (RAG Techniques anthology) |
| 05 | [05_maximal_marginal_relevance.ipynb](notebooks/05_maximal_marginal_relevance.ipynb) | Trade relevance against diversity with Maximal Marginal Relevance |
| 06 | [06_multi_faceted_filtering.ipynb](notebooks/06_multi_faceted_filtering.ipynb) | Filter retrieval by metadata, similarity threshold, keywords and diversity (RAG Techniques anthology) |
| 07 | [07_advanced_retriever_patterns.ipynb](notebooks/07_advanced_retriever_patterns.ipynb) | Compare multi-query, contextual-compression, ensemble and parent-document retrievers in one chain |
| 08 | [08_hybrid_search_and_reranking_databricks.ipynb](notebooks/08_hybrid_search_and_reranking_databricks.ipynb) | Compare semantic, hybrid and hybrid + reranked search on Databricks Vector Search |

Runnable script companions in `notebooks/`: `fusion_retrieval.py`, `multi_faceted_filtering.py`.

## Before you run

- Several notebooks use Hugging Face embeddings (`hf` group).
- `08_hybrid_search_and_reranking_databricks.ipynb` runs on Databricks Vector Search (`databricks` group).
- `fusion_retrieval.py` and `multi_faceted_filtering.py` are runnable script versions of the
  anthology notebooks.

## Sources

Extracted from the `AI-ENGINEERING-DEMYSTIFIED` monorepo (tag `pre-multirepo-split-2026-09`). Every notebook's original path is listed in [docs/content-inventory.csv](../../docs/content-inventory.csv).

Notebooks marked *RAG Techniques anthology* come from Nir Diamant's [RAG_Techniques](https://github.com/NirDiamant/RAG_Techniques) repository and remain under its non-commercial licence: see [docs/third_party/RAG_Techniques_LICENSE.txt](../../docs/third_party/RAG_Techniques_LICENSE.txt). Changes made here: file names and data/image paths only.
