# Module 02 — Document Loading

Turning text, Markdown, CSV, JSON, PDF, Word, web, YouTube and custom sources into LangChain `Document` objects with useful metadata.

| # | Notebook | You will learn |
|---|---|---|
| 01 | [01_document_loading_and_metadata.ipynb](notebooks/01_document_loading_and_metadata.ipynb) | Load many source formats into Documents and design the metadata later stages rely on (canonical lesson) |
| 02 | [02_text_loader.ipynb](notebooks/02_text_loader.ipynb) | Load plain-text files with TextLoader |
| 03 | [03_markdown_loader.ipynb](notebooks/03_markdown_loader.ipynb) | Load Markdown in single and element mode with UnstructuredMarkdownLoader |
| 04 | [04_csv_loader.ipynb](notebooks/04_csv_loader.ipynb) | Load CSV rows as Documents with CSVLoader and UnstructuredCSVLoader |
| 05 | [05_json_loader.ipynb](notebooks/05_json_loader.ipynb) | Load JSON and JSON Lines with jq schemas and metadata functions |
| 06 | [06_pdf_loader.ipynb](notebooks/06_pdf_loader.ipynb) | Compare PyPDF, PyMuPDF and Unstructured PDF loaders, including element-level parsing |
| 07 | [07_ms_word_loader.ipynb](notebooks/07_ms_word_loader.ipynb) | Load .docx files with UnstructuredWordDocumentLoader, including section-based parsing |
| 08 | [08_directory_loader.ipynb](notebooks/08_directory_loader.ipynb) | Bulk-load a folder of mixed files with DirectoryLoader |
| 09 | [09_youtube_transcript_loader.ipynb](notebooks/09_youtube_transcript_loader.ipynb) | Load YouTube transcripts as Documents |
| 10 | [10_url_loader.ipynb](notebooks/10_url_loader.ipynb) | Scrape and clean web pages with RecursiveUrlLoader and BeautifulSoup |
| 11 | [11_research_paper_loader.ipynb](notebooks/11_research_paper_loader.ipynb) | Load research papers from arXiv with ArxivLoader |
| 12 | [12_custom_loader.ipynb](notebooks/12_custom_loader.ipynb) | Write a custom document loader by subclassing BaseLoader (lazy_load) |
| 13 | [13_document_loaders_overview.ipynb](notebooks/13_document_loaders_overview.ipynb) | Survey text, directory, web and PDF loaders and hand-built Documents in one notebook |

## Before you run

- Notebooks 02–12 each demonstrate one loader against the shared corpus in `data/sample/`
  (`dummy.txt`, `data.csv`, `chat_data.json`, `layoutparser_paper.pdf`, `Intel Strategy.docx`, …).
  `langchain_README.markdown` is a copy of LangChain's own README used as a sample Markdown file.
- The Unstructured-based loaders (Markdown, PDF element mode, Word) need the optional
  `document-parsing` group: `uv sync --group document-parsing`.
- `09_youtube_transcript_loader.ipynb`, `10_url_loader.ipynb` and `11_research_paper_loader.ipynb`
  fetch from the internet.
- `01_document_loading_and_metadata.ipynb` is the canonical lesson and needs no API key.

## Sources

Extracted from the `AI-ENGINEERING-DEMYSTIFIED` monorepo (tag `pre-multirepo-split-2026-09`). Every notebook's original path is listed in [docs/content-inventory.csv](../../docs/content-inventory.csv).
