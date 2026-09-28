# Module 03 — Chunking

Splitting documents into retrievable units: character/recursive/token splitters, semantic chunking, proposition chunking and choosing a chunk size.

| # | Notebook | You will learn |
|---|---|---|
| 01 | [01_document_splitting_and_chunking.ipynb](notebooks/01_document_splitting_and_chunking.ipynb) | Split documents with character, recursive, token and structure-aware splitters and measure the result (canonical lesson) |
| 02 | [02_document_splitters_and_chunkers.ipynb](notebooks/02_document_splitters_and_chunkers.ipynb) | Tour LangChain's text splitters (character, recursive, token, NLTK, spaCy, Markdown/HTML/code) |
| 03 | [03_text_splitters_and_chunking_strategies.ipynb](notebooks/03_text_splitters_and_chunking_strategies.ipynb) | Compare chunking strategies and chunk-size/overlap trade-offs on a PDF |
| 04 | [04_semantic_chunking.ipynb](notebooks/04_semantic_chunking.ipynb) | Chunk on meaning boundaries with embedding-distance breakpoints and compare against fixed-size chunks (canonical lesson) |
| 05 | [05_semantic_chunking_walkthrough.ipynb](notebooks/05_semantic_chunking_walkthrough.ipynb) | Implement semantic chunking by hand with sentence embeddings and with LangChain's SemanticChunker |
| 06 | [06_semantic_chunking_rag_techniques.ipynb](notebooks/06_semantic_chunking_rag_techniques.ipynb) | Build a semantic-chunked retriever over a PDF (RAG Techniques anthology version) |
| 07 | [07_proposition_chunking.ipynb](notebooks/07_proposition_chunking.ipynb) | Turn text into atomic, self-contained propositions and index those instead of raw chunks (canonical lesson) |
| 08 | [08_proposition_chunking_rag_techniques.ipynb](notebooks/08_proposition_chunking_rag_techniques.ipynb) | Generate and quality-check propositions with an LLM (RAG Techniques anthology version) |
| 09 | [09_choosing_chunk_size.ipynb](notebooks/09_choosing_chunk_size.ipynb) | Choose a chunk size empirically by measuring retrieval quality across sizes (canonical lesson) |
| 10 | [10_choose_chunk_size_llamaindex.ipynb](notebooks/10_choose_chunk_size_llamaindex.ipynb) | Evaluate response time, faithfulness and relevancy across chunk sizes with LlamaIndex evaluators (RAG Techniques anthology) |

Runnable script companions in `notebooks/`: `semantic_chunking.py`, `choose_chunk_size.py`.

## Before you run

- Canonical lessons are 01, 04, 07 and 09; the others are alternative walkthroughs of the same ideas,
  kept side by side (01/02/03 all tour splitters, 04/05/06 all teach semantic chunking, 07/08 both
  teach proposition chunking, 09/10 both choose a chunk size).
- `02_document_splitters_and_chunkers.ipynb` uses NLTK and spaCy splitters (`document-parsing` group).
- `10_choose_chunk_size_llamaindex.ipynb` needs the `llamaindex` group.
- `semantic_chunking.py` and `choose_chunk_size.py` are runnable script versions of the anthology
  notebooks; `helper_functions.py` and `evaluation/` are the anthology's support modules.

## Sources

Extracted from the `AI-ENGINEERING-DEMYSTIFIED` monorepo (tag `pre-multirepo-split-2026-09`). Every notebook's original path is listed in [docs/content-inventory.csv](../../docs/content-inventory.csv).

Notebooks marked *RAG Techniques anthology* come from Nir Diamant's [RAG_Techniques](https://github.com/NirDiamant/RAG_Techniques) repository and remain under its non-commercial licence: see [docs/third_party/RAG_Techniques_LICENSE.txt](../../docs/third_party/RAG_Techniques_LICENSE.txt). Changes made here: file names and data/image paths only.
