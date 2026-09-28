# Module 10 — Building RAG Systems

Assembling complete, non-agentic RAG pipelines over PDFs, CSV and JSON, with sources, citations and explainable retrieval, ending in a research-assistant lab.

| # | Notebook | You will learn |
|---|---|---|
| 00 | [00_setup.ipynb](notebooks/00_setup.ipynb) | Install the packages and load the environment used by the notebooks in this module |
| 01 | [01_build_a_simple_rag_system.ipynb](notebooks/01_build_a_simple_rag_system.ipynb) | Build an end-to-end RAG system over JSONL and PDF sources with Chroma |
| 02 | [02_contextual_retrieval_rag_system.ipynb](notebooks/02_contextual_retrieval_rag_system.ipynb) | Add LLM-generated chunk context before embedding (contextual retrieval) |
| 03 | [03_rag_system_with_sources.ipynb](notebooks/03_rag_system_with_sources.ipynb) | Return the source documents alongside each answer |
| 04 | [04_rag_system_with_citations.ipynb](notebooks/04_rag_system_with_citations.ipynb) | Attach structured, per-claim citations to answers |
| 05 | [05_simple_rag_pdf.ipynb](notebooks/05_simple_rag_pdf.ipynb) | Build a simple FAISS-based RAG retriever over a PDF (RAG Techniques anthology version) |
| 06 | [06_local_rag_huggingface_faiss.ipynb](notebooks/06_local_rag_huggingface_faiss.ipynb) | Run a fully local RAG pipeline with Hugging Face models and FAISS (RAG Techniques anthology) |
| 07 | [07_explainable_retrieval.ipynb](notebooks/07_explainable_retrieval.ipynb) | Explain why each retrieved chunk is relevant to the query (RAG Techniques anthology) |
| 08 | [08_structured_data_rag.ipynb](notebooks/08_structured_data_rag.ipynb) | Apply RAG to tabular and JSON data by choosing a row/record representation (canonical lesson) |
| 09 | [09_simple_csv_rag.ipynb](notebooks/09_simple_csv_rag.ipynb) | Build a RAG pipeline over a CSV file (RAG Techniques anthology version) |
| 10 | [10_json_rag.ipynb](notebooks/10_json_rag.ipynb) | Turn JSON records into embeddable text and search them semantically (RAG Techniques anthology) |
| 11 | [11_ai_research_assistant.ipynb](notebooks/11_ai_research_assistant.ipynb) | Module lab: package ingestion, retrieval, structured answers and session history into one research-assistant class |

Runnable script companions in `notebooks/`: `simple_rag.py`, `explainable_retrieval.py`.

## Before you run

- Start with `00_setup.ipynb`. `03_rag_system_with_sources.ipynb` and `04_rag_system_with_citations.ipynb`
  `%run` `02_contextual_retrieval_rag_system.ipynb` first, so run them from this folder.
- 01 and 02 embed every PDF directly in `data/sample/` — expect a noticeable embedding cost.
- `06_local_rag_huggingface_faiss.ipynb` needs the `hf` group; `10_json_rag.ipynb` needs `jrag`
  (`vendors` group) and downloads a public Nobel-prize JSON file.
- `11_ai_research_assistant.ipynb` is the module lab. It keeps a per-session chat history so the
  assistant can answer follow-ups; durable and long-term memory are taught in
  repository 08 (advanced agent systems, not yet published).
- `simple_rag.py` and `explainable_retrieval.py` are runnable script versions of the anthology notebooks.

## Sources

Extracted from the `AI-ENGINEERING-DEMYSTIFIED` monorepo (tag `pre-multirepo-split-2026-09`). Every notebook's original path is listed in [docs/content-inventory.csv](../../docs/content-inventory.csv).

Notebooks marked *RAG Techniques anthology* come from Nir Diamant's [RAG_Techniques](https://github.com/NirDiamant/RAG_Techniques) repository and remain under its non-commercial licence: see [docs/third_party/RAG_Techniques_LICENSE.txt](../../docs/third_party/RAG_Techniques_LICENSE.txt). Changes made here: file names and data/image paths only.
