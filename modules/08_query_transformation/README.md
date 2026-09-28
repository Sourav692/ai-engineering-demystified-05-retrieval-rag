# Module 08 — Query Transformation

Changing the query before retrieval: multi-query, RAG-Fusion, step-back prompting, HyDE, decomposition, routing and self-querying.

| # | Notebook | You will learn |
|---|---|---|
| 01 | [01_multi_query_retrieval.ipynb](notebooks/01_multi_query_retrieval.ipynb) | Generate several rephrasings of a question and union their retrieved documents |
| 02 | [02_rag_fusion.ipynb](notebooks/02_rag_fusion.ipynb) | Merge the rankings of multiple generated queries with Reciprocal Rank Fusion |
| 03 | [03_step_back_prompting.ipynb](notebooks/03_step_back_prompting.ipynb) | Retrieve with a more general 'step-back' question alongside the original |
| 04 | [04_hyde.ipynb](notebooks/04_hyde.ipynb) | Embed a hypothetical answer (HyDE) instead of the question |
| 05 | [05_query_decomposition.ipynb](notebooks/05_query_decomposition.ipynb) | Break a complex question into sub-questions answered recursively or individually |
| 06 | [06_routing_with_llm_classifier.ipynb](notebooks/06_routing_with_llm_classifier.ipynb) | Route a query to a specialist prompt with a structured-output LLM classifier |
| 07 | [07_semantic_routing.ipynb](notebooks/07_semantic_routing.ipynb) | Route a query by embedding similarity to candidate prompts |
| 08 | [08_self_querying_retrieval.ipynb](notebooks/08_self_querying_retrieval.ipynb) | Let an LLM turn a question into a semantic query plus a metadata filter |
| 09 | [09_query_expansion.ipynb](notebooks/09_query_expansion.ipynb) | Expand a query with an LLM before retrieval |
| 10 | [10_query_decomposition_walkthrough.ipynb](notebooks/10_query_decomposition_walkthrough.ipynb) | Decompose a query into sub-questions and answer each (overlaps 05) |
| 11 | [11_hyde_walkthrough.ipynb](notebooks/11_hyde_walkthrough.ipynb) | Implement HyDE with Hugging Face embeddings and Chroma (overlaps 04) |
| 12 | [12_multiquery_retrieval_walkthrough.ipynb](notebooks/12_multiquery_retrieval_walkthrough.ipynb) | Hand-build a multi-query chain and de-duplicate results (overlaps 01) |
| 13 | [13_better_queries.ipynb](notebooks/13_better_queries.ipynb) | Multi-query plus multi-answer HyDE on the same corpus (near-duplicate of 12 with extra HyDE cells) |
| 14 | [14_query_transformations_rag_techniques.ipynb](notebooks/14_query_transformations_rag_techniques.ipynb) | Query rewriting, step-back prompting and sub-query decomposition (RAG Techniques anthology version) |
| 15 | [15_hyde_rag_techniques.ipynb](notebooks/15_hyde_rag_techniques.ipynb) | HyDE retriever over a PDF (RAG Techniques anthology version) |

Runnable script companions in `notebooks/`: `query_transformations.py`, `HyDe_Hypothetical_Document_Embedding.py`.

## Before you run

- Concept explainers: [Query_Transformation_Techniques_Explained.md](assets/Query_Transformation_Techniques_Explained.md)
  and a standalone HTML version, [Query_Transformation_Techniques.html](assets/Query_Transformation_Techniques.html).
- 01–08 use `helpers.get_experientiallabs_llm()` (`EXPERIENTIALLABS_API_KEY`) and optionally trace to LangSmith.
- Overlapping walkthroughs are kept side by side: 01/12/13 (multi-query), 04/11/15 (HyDE),
  05/10 (decomposition), 03/14 (step-back and rewriting). 13 is 12 plus a few extra HyDE cells.
- Routing here (06, 07) sends a query to a specialist *prompt*; routing between retrieval, web search and
  no retrieval is adaptive RAG and belongs to repository 09 (advanced RAG, not yet published).

## Sources

Extracted from the `AI-ENGINEERING-DEMYSTIFIED` monorepo (tag `pre-multirepo-split-2026-09`). Every notebook's original path is listed in [docs/content-inventory.csv](../../docs/content-inventory.csv).

Notebooks marked *RAG Techniques anthology* come from Nir Diamant's [RAG_Techniques](https://github.com/NirDiamant/RAG_Techniques) repository and remain under its non-commercial licence: see [docs/third_party/RAG_Techniques_LICENSE.txt](../../docs/third_party/RAG_Techniques_LICENSE.txt). Changes made here: file names and data/image paths only.
