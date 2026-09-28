# Setup

## 1. Install

```bash
uv sync                  # Python 3.12, the core LangChain/RAG stack, the local helpers package and dev tools
cp .env.example .env     # names only; fill in the keys for the notebooks you plan to run
uv run pytest            # offline: notebook structure, links, and a smoke test; no API keys, no network
uv run jupyter lab
```

`uv sync` installs `src/helpers` in editable mode, so notebooks can `from helpers import get_llm,
get_embeddings, get_experientiallabs_llm`. The canonical lessons also put `src/` on `sys.path` to import
`rag_paths`, which finds sample files by name under `data/sample/` (and `modules/03_chunking/assets/`).

## 2. Optional dependency groups

The default install stays light. Add a group only when a notebook needs it:

| Group | Command | What it adds | Used by |
|---|---|---|---|
| `hf` | `uv sync --group hf` | `langchain-huggingface`, `sentence-transformers`, `transformers`, `torch`, `pillow` | Hugging Face embeddings and cross-encoders (modules 04, 07, 08, 09, 10), CLIP (11/01) |
| `document-parsing` | `uv sync --group document-parsing` | `unstructured[md,pdf,docx]`, `nltk`, `spacy` | Unstructured loaders (module 02), NLTK/spaCy splitters (03/02) |
| `llamaindex` | `uv sync --group llamaindex` | `llama-index` and its FAISS / file-reader integrations | module 13, `03_chunking/10` |
| `vendors` | `uv sync --group vendors` | `langchain-pinecone`, `langchain-astradb`, `langchain-cohere`, `google-generativeai`, `jrag` | 05/06, 05/07, 11/02, 10/10 |
| `databricks` | `uv sync --group databricks` | `databricks-vectorsearch`, `mlflow` | 04/08, 07/08 (run on a Databricks workspace) |
| `colpali` | `uv sync --no-default-groups --group dev --group colpali` | `byaldi` | 11/03 only |

Groups combine: `uv sync --group hf --group document-parsing`. The `colpali` group pins
`transformers<5` and is declared as conflicting with `hf`, so use a separate sync for it.

Some notebooks also need extra downloads at run time: spaCy/NLTK models (03/02), Hugging Face model
weights, and the few `!wget`/`!pip` cells kept from the original notebooks.

## 3. External services

| Service | Needed by | How |
|---|---|---|
| PostgreSQL + pgvector | module 12, 06/03 | `docker compose up -d` in `modules/12_langchain_rag_implementations/notebooks/` |
| Databricks workspace | 04/08, 07/08, `helpers.get_llm()` default provider | `DATABRICKS_HOST`, `DATABRICKS_TOKEN` |
| Astra DB, Pinecone | 05/06, 05/07 | keys in `.env` |

## 4. Where things are

- `modules/NN_topic/notebooks/` — lessons, run with that folder as the working directory. Python files
  beside a notebook (`helper_functions.py`, `evaluation/`, `utils.py`, runnable `*.py` scripts) are
  imported or run from there.
- `modules/NN_topic/assets/` — data and diagrams used by one module.
- `data/sample/` — corpora shared by several modules (see `data/README.md` and `docs/data-sources.md`).
- `scripts/path_allowlist.txt` — literal file names in notebooks that are metadata labels, runtime
  outputs, or resolved through `rag_paths`, so the notebook check does not expect them on disk.

## 5. Checks

```bash
uv run ruff check .
uv run pytest -q
uv run pre-commit install    # once per clone: strips notebook outputs and runs the checks on commit
```

## 6. Known issue: LangChain 0.x import paths

These lessons were migrated as written (paths repaired, code otherwise unchanged). The files below still
import LangChain 0.x module paths that no longer exist in LangChain 1.x, which this repository pins —
most have a direct replacement in `langchain_classic`, `langchain_community`, `langchain_core` or
`langchain_text_splitters`. The canonical lessons (marked in [curriculum-map.md](curriculum-map.md)) use
current imports and cover the same concepts. Detected statically with `importlib.util.find_spec`; nothing
was executed.

| File | Missing module(s) |
|---|---|
| [`03_chunking/notebooks/02_document_splitters_and_chunkers.ipynb`](../modules/03_chunking/notebooks/02_document_splitters_and_chunkers.ipynb) | `langchain.text_splitter` |
| [`03_chunking/notebooks/05_semantic_chunking_walkthrough.ipynb`](../modules/03_chunking/notebooks/05_semantic_chunking_walkthrough.ipynb) | `langchain.document_loaders, langchain.prompts, langchain.schema, langchain.schema.runnable, langchain.vectorstores` |
| [`03_chunking/notebooks/08_proposition_chunking_rag_techniques.ipynb`](../modules/03_chunking/notebooks/08_proposition_chunking_rag_techniques.ipynb) | `langchain.text_splitter, langchain_core.pydantic_v1` |
| [`05_vector_stores/notebooks/03_chromadb.ipynb`](../modules/05_vector_stores/notebooks/03_chromadb.ipynb) | `langchain.chains, langchain.chains.combine_documents, langchain.schema, langchain.text_splitter` |
| [`05_vector_stores/notebooks/04_faiss.ipynb`](../modules/05_vector_stores/notebooks/04_faiss.ipynb) | `langchain.chains, langchain.chains.combine_documents` |
| [`06_indexing_strategies/notebooks/03_parent_document_retriever_postgres.ipynb`](../modules/06_indexing_strategies/notebooks/03_parent_document_retriever_postgres.ipynb) | `langchain.retrievers, langchain.schema, langchain.storage, langchain.text_splitter` |
| [`06_indexing_strategies/notebooks/04_hierarchical_indices.ipynb`](../modules/06_indexing_strategies/notebooks/04_hierarchical_indices.ipynb) | `langchain.chains.summarize.chain, langchain.docstore.document` |
| [`06_indexing_strategies/notebooks/06_document_augmentation.ipynb`](../modules/06_indexing_strategies/notebooks/06_document_augmentation.ipynb) | `langchain.docstore.document, langchain.embeddings.openai, langchain.vectorstores` |
| [`06_indexing_strategies/notebooks/07_contextual_chunk_headers.ipynb`](../modules/06_indexing_strategies/notebooks/07_contextual_chunk_headers.ipynb) | `langchain.text_splitter` |
| [`06_indexing_strategies/notebooks/hierarchical_indices.py`](../modules/06_indexing_strategies/notebooks/hierarchical_indices.py) | `langchain.chains.summarize.chain, langchain.docstore.document` |
| [`07_retrievers_and_hybrid_search/notebooks/01_retrievers.ipynb`](../modules/07_retrievers_and_hybrid_search/notebooks/01_retrievers.ipynb) | `langchain.retrievers, langchain.retrievers.document_compressors, langchain.retrievers.multi_query` |
| [`07_retrievers_and_hybrid_search/notebooks/02_dense_sparse_hybrid_retrieval.ipynb`](../modules/07_retrievers_and_hybrid_search/notebooks/02_dense_sparse_hybrid_retrieval.ipynb) | `langchain.chains.combine_documents, langchain.chains.retrieval, langchain.prompts, langchain.retrievers, langchain.schema` |
| [`07_retrievers_and_hybrid_search/notebooks/04_fusion_retrieval.ipynb`](../modules/07_retrievers_and_hybrid_search/notebooks/04_fusion_retrieval.ipynb) | `langchain.docstore.document` |
| [`07_retrievers_and_hybrid_search/notebooks/05_maximal_marginal_relevance.ipynb`](../modules/07_retrievers_and_hybrid_search/notebooks/05_maximal_marginal_relevance.ipynb) | `langchain.chains.combine_documents, langchain.chains.retrieval, langchain.document_loaders, langchain.prompts, langchain.text_splitter` |
| [`08_query_transformation/notebooks/09_query_expansion.ipynb`](../modules/08_query_transformation/notebooks/09_query_expansion.ipynb) | `langchain.chains.combine_documents, langchain.chains.retrieval, langchain.document_loaders, langchain.prompts, langchain.text_splitter` |
| [`08_query_transformation/notebooks/10_query_decomposition_walkthrough.ipynb`](../modules/08_query_transformation/notebooks/10_query_decomposition_walkthrough.ipynb) | `langchain.chains.combine_documents, langchain.document_loaders, langchain.prompts, langchain.text_splitter` |
| [`08_query_transformation/notebooks/11_hyde_walkthrough.ipynb`](../modules/08_query_transformation/notebooks/11_hyde_walkthrough.ipynb) | `langchain.chains.combine_documents, langchain.chains.hyde.base, langchain.document_loaders, langchain.prompts, langchain.prompts.chat, langchain.text_splitter, langchain.vectorstores` |
| [`08_query_transformation/notebooks/12_multiquery_retrieval_walkthrough.ipynb`](../modules/08_query_transformation/notebooks/12_multiquery_retrieval_walkthrough.ipynb) | `langchain.prompts, langchain.text_splitter` |
| [`08_query_transformation/notebooks/13_better_queries.ipynb`](../modules/08_query_transformation/notebooks/13_better_queries.ipynb) | `langchain.chains, langchain.docstore.document, langchain.llms, langchain.prompts, langchain.text_splitter, langchain.vectorstores.faiss` |
| [`08_query_transformation/notebooks/14_query_transformations_rag_techniques.ipynb`](../modules/08_query_transformation/notebooks/14_query_transformations_rag_techniques.ipynb) | `langchain.prompts` |
| [`09_post_retrieval_and_reranking/notebooks/01_cross_encoder_reranking.ipynb`](../modules/09_post_retrieval_and_reranking/notebooks/01_cross_encoder_reranking.ipynb) | `langchain.retrievers, langchain.retrievers.document_compressors, langchain.text_splitter` |
| [`09_post_retrieval_and_reranking/notebooks/02_two_stage_reranking.ipynb`](../modules/09_post_retrieval_and_reranking/notebooks/02_two_stage_reranking.ipynb) | `langchain.document_loaders, langchain.prompts, langchain.schema, langchain.text_splitter` |
| [`09_post_retrieval_and_reranking/notebooks/03_reranking_cross_encoder_walkthrough.ipynb`](../modules/09_post_retrieval_and_reranking/notebooks/03_reranking_cross_encoder_walkthrough.ipynb) | `langchain.prompts, langchain.schema, langchain.text_splitter` |
| [`09_post_retrieval_and_reranking/notebooks/04_reranking_methods.ipynb`](../modules/09_post_retrieval_and_reranking/notebooks/04_reranking_methods.ipynb) | `langchain.chains, langchain.docstore.document` |
| [`09_post_retrieval_and_reranking/notebooks/05_contextual_compression.ipynb`](../modules/09_post_retrieval_and_reranking/notebooks/05_contextual_compression.ipynb) | `langchain.chains, langchain.retrievers, langchain.retrievers.document_compressors` |
| [`09_post_retrieval_and_reranking/notebooks/06_context_enrichment_window.ipynb`](../modules/09_post_retrieval_and_reranking/notebooks/06_context_enrichment_window.ipynb) | `langchain.docstore.document` |
| [`09_post_retrieval_and_reranking/notebooks/contextual_compression.py`](../modules/09_post_retrieval_and_reranking/notebooks/contextual_compression.py) | `langchain.chains, langchain.retrievers, langchain.retrievers.document_compressors` |
| [`09_post_retrieval_and_reranking/notebooks/reranking.py`](../modules/09_post_retrieval_and_reranking/notebooks/reranking.py) | `langchain.chains` |
| [`10_building_rag_systems/notebooks/01_build_a_simple_rag_system.ipynb`](../modules/10_building_rag_systems/notebooks/01_build_a_simple_rag_system.ipynb) | `langchain.docstore.document, langchain.document_loaders, langchain.text_splitter` |
| [`10_building_rag_systems/notebooks/02_contextual_retrieval_rag_system.ipynb`](../modules/10_building_rag_systems/notebooks/02_contextual_retrieval_rag_system.ipynb) | `langchain.docstore.document, langchain.document_loaders, langchain.prompts, langchain.schema, langchain.text_splitter` |
| [`10_building_rag_systems/notebooks/05_simple_rag_pdf.ipynb`](../modules/10_building_rag_systems/notebooks/05_simple_rag_pdf.ipynb) | `langchain.document_loaders, langchain.text_splitter, langchain.vectorstores` |
| [`10_building_rag_systems/notebooks/06_local_rag_huggingface_faiss.ipynb`](../modules/10_building_rag_systems/notebooks/06_local_rag_huggingface_faiss.ipynb) | `langchain.prompts, langchain.text_splitter` |
| [`10_building_rag_systems/notebooks/09_simple_csv_rag.ipynb`](../modules/10_building_rag_systems/notebooks/09_simple_csv_rag.ipynb) | `langchain.chains, langchain.chains.combine_documents` |
| [`11_multimodal_rag/notebooks/01_multimodal_rag_with_clip.ipynb`](../modules/11_multimodal_rag/notebooks/01_multimodal_rag_with_clip.ipynb) | `langchain.prompts, langchain.schema.messages, langchain.text_splitter` |
| [`11_multimodal_rag/notebooks/02_multimodal_rag_with_captioning.ipynb`](../modules/11_multimodal_rag/notebooks/02_multimodal_rag_with_captioning.ipynb) | `langchain.text_splitter` |
| [`12_langchain_rag_implementations/notebooks/01_filtered_search_pgvector.ipynb`](../modules/12_langchain_rag_implementations/notebooks/01_filtered_search_pgvector.ipynb) | `langchain.schema, langchain.text_splitter` |
| [`12_langchain_rag_implementations/notebooks/02_indexing_api.ipynb`](../modules/12_langchain_rag_implementations/notebooks/02_indexing_api.ipynb) | `langchain.indexes, langchain.schema, langchain.text_splitter` |
