# Module 09 — Post-Retrieval and Reranking

Refining retrieved candidates before generation: cross-encoder and LLM reranking, contextual compression, context-enrichment windows and relevant segment extraction.

| # | Notebook | You will learn |
|---|---|---|
| 01 | [01_cross_encoder_reranking.ipynb](notebooks/01_cross_encoder_reranking.ipynb) | Re-score retrieved documents with a cross-encoder before generation |
| 02 | [02_two_stage_reranking.ipynb](notebooks/02_two_stage_reranking.ipynb) | Retrieve broadly, then rerank with an LLM for a precise top-k |
| 03 | [03_reranking_cross_encoder_walkthrough.ipynb](notebooks/03_reranking_cross_encoder_walkthrough.ipynb) | Cross-encoder reranking inside a LangChain RAG chain (overlaps 01) |
| 04 | [04_reranking_methods.ipynb](notebooks/04_reranking_methods.ipynb) | Compare LLM-based and cross-encoder reranking (RAG Techniques anthology version) |
| 05 | [05_contextual_compression.ipynb](notebooks/05_contextual_compression.ipynb) | Compress retrieved chunks to only the query-relevant parts with an LLM extractor (RAG Techniques anthology) |
| 06 | [06_context_enrichment_window.ipynb](notebooks/06_context_enrichment_window.ipynb) | Return neighbouring chunks around each hit to restore surrounding context (RAG Techniques anthology) |
| 07 | [07_relevant_segment_extraction.ipynb](notebooks/07_relevant_segment_extraction.ipynb) | Reconstruct contiguous relevant segments from chunk-level relevance scores (RAG Techniques anthology) |

Runnable script companions in `notebooks/`: `reranking.py`, `contextual_compression.py`, `context_enrichment_window_around_chunk.py`.

## Before you run

- 01 and 03 both teach cross-encoder reranking (different sources); the cross-encoder models need the `hf` group.
- `07_relevant_segment_extraction.ipynb` uses Cohere reranking (`CO_API_KEY`).
- `reranking.py`, `contextual_compression.py` and `context_enrichment_window_around_chunk.py` are
  runnable script versions of the anthology notebooks.

## Sources

Extracted from the `AI-ENGINEERING-DEMYSTIFIED` monorepo (tag `pre-multirepo-split-2026-09`). Every notebook's original path is listed in [docs/content-inventory.csv](../../docs/content-inventory.csv).

Notebooks marked *RAG Techniques anthology* come from Nir Diamant's [RAG_Techniques](https://github.com/NirDiamant/RAG_Techniques) repository and remain under its non-commercial licence: see [docs/third_party/RAG_Techniques_LICENSE.txt](../../docs/third_party/RAG_Techniques_LICENSE.txt). Changes made here: file names and data/image paths only.
