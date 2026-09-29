# 05 — Retrieval and RAG

Everything needed to build standard, non-agentic retrieval-augmented generation: loading, chunking, embeddings, vector stores, indexing, retrievers and hybrid search, query transformation, reranking, citations and multimodal retrieval.

**You are here:** [← 04 LangGraph fundamentals](https://github.com/Sourav692/ai-engineering-demystified-04-langgraph-fundamentals) · **05 Retrieval and RAG** · [06 Agent fundamentals →](https://github.com/Sourav692/ai-engineering-demystified-06-agent-fundamentals) — full sequence in [docs/learning-path.md](docs/learning-path.md)

## Prerequisites

You should already be comfortable with the following (see [docs/prerequisites.md](docs/prerequisites.md)):

- Python, notebooks, environment variables and calling an LLM provider API (repository 01).
- Writing prompts and structured prompts (repository 02).
- LangChain models, messages, prompt templates, output parsers and LCEL `|` composition (repository 03).
- LangGraph is recommended but not required; nothing here builds a graph.

## Learning outcomes

After this repository you can:

1. Explain the RAG lifecycle and build a measured baseline pipeline end to end.
2. Load text, Markdown, CSV, JSON, PDF, Word, web and custom sources into documents with useful metadata.
3. Choose a chunking strategy (recursive, token, semantic, proposition) and pick a chunk size by measurement.
4. Generate, compare and choose embedding models, and operate Chroma, FAISS and managed vector stores.
5. Change what is indexed (parent-document, multi-representation, hierarchical, HyPE, contextual headers).
6. Select candidates with dense, sparse, hybrid, fusion, MMR and metadata-filtered retrieval.
7. Transform queries before retrieval (multi-query, RAG-Fusion, step-back, HyDE, decomposition, routing, self-query).
8. Refine results after retrieval (cross-encoder and LLM reranking, compression, context windows, segment extraction).
9. Assemble complete RAG systems with sources and citations, including over structured data and images.
10. Recognise the same techniques in LangChain-specific features and in LlamaIndex.

## Modules

| # | Module | What it covers | Notebooks |
|---|---|---|---|
| 01 | [Introduction to RAG](modules/01_introduction_to_rag/README.md) | From a from-scratch index to the full RAG lifecycle | 4 |
| 02 | [Document loading](modules/02_document_loading/README.md) | Loaders for every common format, and metadata | 13 |
| 03 | [Chunking](modules/03_chunking/README.md) | Splitters, semantic and proposition chunking, chunk size | 10 |
| 04 | [Embeddings](modules/04_embeddings/README.md) | OpenAI and Hugging Face embeddings, model selection | 8 |
| 05 | [Vector stores](modules/05_vector_stores/README.md) | Chroma, FAISS, Astra DB, Pinecone, index operations | 8 |
| 06 | [Indexing strategies](modules/06_indexing_strategies/README.md) | Parent-document, multi-representation, hierarchical, HyPE | 7 |
| 07 | [Retrievers and hybrid search](modules/07_retrievers_and_hybrid_search/README.md) | BM25 + vector, fusion, MMR, metadata filtering | 8 |
| 08 | [Query transformation](modules/08_query_transformation/README.md) | Multi-query, RAG-Fusion, step-back, HyDE, routing | 15 |
| 09 | [Post-retrieval and reranking](modules/09_post_retrieval_and_reranking/README.md) | Rerankers, compression, context windows | 7 |
| 10 | [Building RAG systems](modules/10_building_rag_systems/README.md) | End-to-end pipelines, sources, citations, structured data | 12 |
| 11 | [Multimodal RAG](modules/11_multimodal_rag/README.md) | CLIP, image captioning, ColPali | 3 |
| 12 | [LangChain RAG implementations](modules/12_langchain_rag_implementations/README.md) | PGVector filtered search, the Indexing API | 2 |
| 13 | [LlamaIndex RAG implementations](modules/13_llamaindex_rag/README.md) | The same techniques in LlamaIndex | 5 |

Each module README lists its notebooks in order; [docs/curriculum-map.md](docs/curriculum-map.md) gives the one-line objective of every notebook. Where two notebooks teach the same thing (they came from different source courses) both are kept side by side and the overlap is noted.

## Setup and quick start

Requires [uv](https://docs.astral.sh/uv/) and Python 3.12.

```bash
git clone https://github.com/Sourav692/ai-engineering-demystified-05-retrieval-rag.git
cd ai-engineering-demystified-05-retrieval-rag
uv sync                  # core LangChain/RAG stack + dev tools
cp .env.example .env     # then fill in the keys you need
uv run pytest            # offline checks: notebooks, links, smoke test (no API keys needed)
uv run jupyter lab
```

Heavier or vendor-specific stacks are optional dependency groups (details in [docs/setup.md](docs/setup.md)):

| Group | Install | Needed by |
|---|---|---|
| `hf` | `uv sync --group hf` | Hugging Face embeddings, cross-encoders, CLIP (torch) |
| `document-parsing` | `uv sync --group document-parsing` | Unstructured loaders, NLTK/spaCy splitters |
| `llamaindex` | `uv sync --group llamaindex` | Module 13 and `03_chunking/10` |
| `vendors` | `uv sync --group vendors` | Pinecone, Astra DB, Cohere (LangChain), Gemini, `jrag` |
| `databricks` | `uv sync --group databricks` | Databricks Vector Search / MLflow notebooks |
| `colpali` | `uv sync --no-default-groups --group dev --group colpali` | `11_multimodal_rag/03` (conflicts with `hf`) |

Notebooks run with the kernel's working directory set to their own folder and reach shared data through relative paths such as `../../../data/sample/`. The canonical lessons locate data with `src/rag_paths.py` instead.

## Environment variables

All names are in [.env.example](.env.example) with a comment saying what uses each. The ones most notebooks need:

| Variable | Used for |
|---|---|
| `OPENAI_API_KEY` | Embeddings and chat models in most notebooks |
| `EXPERIENTIALLABS_API_KEY` | Chat model behind `helpers.get_experientiallabs_llm()` (canonical lessons, module 08) |
| `GROQ_API_KEY` | Groq chat models in several notebooks |
| `DATABRICKS_HOST`, `DATABRICKS_TOKEN` | `helpers.get_llm()` default provider and the Databricks notebooks |
| `CO_API_KEY` / `COHERE_API_KEY`, `GOOGLE_API_KEY`, `HUGGINGFACEHUB_API_TOKEN` | Specific notebooks, named in their module README |
| `ASTRA_DB_*`, `PINECONE_API_KEY` | Managed vector store notebooks |
| `LANGSMITH_*` | Optional tracing |

## Out of scope

- Agentic, corrective, adaptive and self-RAG, retrieval grading loops, RAG as an agent tool, GraphRAG/knowledge graphs, RAPTOR and other advanced retrieval architectures — [repository 09 (advanced RAG)](https://github.com/Sourav692/ai-engineering-demystified-09-advanced-rag).
- Tool calling and the agent loop — [repository 06 (agent fundamentals)](https://github.com/Sourav692/ai-engineering-demystified-06-agent-fundamentals).
- Durable conversation and long-term memory — [repository 08 (advanced agent systems)](https://github.com/Sourav692/ai-engineering-demystified-08-advanced-agent-systems).
- Serving RAG behind an API, tracing, cost control and other production concerns — [repository 13 (production and observability)](https://github.com/Sourav692/ai-engineering-demystified-13-production-observability).
- Measuring RAG quality — the separate `Agent_Evaluation_Demystified` repository.

## Licence and acknowledgements

MIT — see [LICENSE](LICENSE), except the notebooks marked *RAG Techniques anthology*, which come from Nir Diamant's [RAG_Techniques](https://github.com/NirDiamant/RAG_Techniques) and remain under its non-commercial licence ([docs/third_party/RAG_Techniques_LICENSE.txt](docs/third_party/RAG_Techniques_LICENSE.txt)).

Extracted from [`Sourav692/AI-ENGINEERING-DEMYSTIFIED`](https://github.com/Sourav692/AI-ENGINEERING-DEMYSTIFIED) at tag `pre-multirepo-split-2026-09`; the origin of every file is in [docs/content-inventory.csv](docs/content-inventory.csv) and [docs/data-sources.md](docs/data-sources.md). Several notebooks follow public courses (*Ultimate RAG Bootcamp*, *LangChain in Action*, *Advanced LangChain Techniques* on Udemy) and the LangChain documentation; sample papers are from arXiv.
