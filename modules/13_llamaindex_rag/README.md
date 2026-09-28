# Module 13 — LlamaIndex RAG Implementations

The same foundational techniques (simple RAG, CSV RAG, fusion retrieval, reranking, context windows) implemented with LlamaIndex.

| # | Notebook | You will learn |
|---|---|---|
| 01 | [01_simple_rag_with_llamaindex.ipynb](notebooks/01_simple_rag_with_llamaindex.ipynb) | Build a simple PDF RAG pipeline with LlamaIndex and FAISS (RAG Techniques anthology) |
| 02 | [02_simple_csv_rag_with_llamaindex.ipynb](notebooks/02_simple_csv_rag_with_llamaindex.ipynb) | Build a CSV RAG pipeline with LlamaIndex (RAG Techniques anthology) |
| 03 | [03_fusion_retrieval_with_llamaindex.ipynb](notebooks/03_fusion_retrieval_with_llamaindex.ipynb) | Fuse vector and BM25 retrieval with LlamaIndex's QueryFusionRetriever (RAG Techniques anthology) |
| 04 | [04_reranking_with_llamaindex.ipynb](notebooks/04_reranking_with_llamaindex.ipynb) | Rerank with LLM and cross-encoder postprocessors in LlamaIndex (RAG Techniques anthology) |
| 05 | [05_context_enrichment_window_with_llamaindex.ipynb](notebooks/05_context_enrichment_window_with_llamaindex.ipynb) | Sentence-window retrieval with LlamaIndex (RAG Techniques anthology) |

## Before you run

Install the `llamaindex` group: `uv sync --group llamaindex`. These are LlamaIndex versions of
techniques taught with LangChain earlier in this repository:

| LlamaIndex notebook | LangChain counterpart |
|---|---|
| 01 simple RAG | [10_building_rag_systems/05](../10_building_rag_systems/notebooks/05_simple_rag_pdf.ipynb) |
| 02 CSV RAG | [10_building_rag_systems/09](../10_building_rag_systems/notebooks/09_simple_csv_rag.ipynb) |
| 03 fusion retrieval | [07_retrievers_and_hybrid_search/04](../07_retrievers_and_hybrid_search/notebooks/04_fusion_retrieval.ipynb) |
| 04 reranking | [09_post_retrieval_and_reranking/04](../09_post_retrieval_and_reranking/notebooks/04_reranking_methods.ipynb) |
| 05 context window | [09_post_retrieval_and_reranking/06](../09_post_retrieval_and_reranking/notebooks/06_context_enrichment_window.ipynb) |

## Sources

Extracted from the `AI-ENGINEERING-DEMYSTIFIED` monorepo (tag `pre-multirepo-split-2026-09`). Every notebook's original path is listed in [docs/content-inventory.csv](../../docs/content-inventory.csv).

Notebooks marked *RAG Techniques anthology* come from Nir Diamant's [RAG_Techniques](https://github.com/NirDiamant/RAG_Techniques) repository and remain under its non-commercial licence: see [docs/third_party/RAG_Techniques_LICENSE.txt](../../docs/third_party/RAG_Techniques_LICENSE.txt). Changes made here: file names and data/image paths only.
