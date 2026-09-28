# Module 11 — Multimodal RAG

Retrieval over documents that contain images: CLIP-style multimodal embeddings, image captioning and ColPali page retrieval.

| # | Notebook | You will learn |
|---|---|---|
| 01 | [01_multimodal_rag_with_clip.ipynb](notebooks/01_multimodal_rag_with_clip.ipynb) | Embed PDF text and images in one space with CLIP and answer with a multimodal LLM |
| 02 | [02_multimodal_rag_with_captioning.ipynb](notebooks/02_multimodal_rag_with_captioning.ipynb) | Caption PDF images with a Gemini vision model and index captions alongside text (Cohere embeddings) (RAG Techniques anthology) |
| 03 | [03_multimodal_rag_with_colpali.ipynb](notebooks/03_multimodal_rag_with_colpali.ipynb) | Retrieve whole PDF pages as images with ColPali (RAG Techniques anthology) |

## Before you run

- `01_multimodal_rag_with_clip.ipynb` needs the `hf` group (CLIP via `transformers`/`torch`).
- `02_multimodal_rag_with_captioning.ipynb` needs `GOOGLE_API_KEY` and Cohere (`vendors` group).
- `03_multimodal_rag_with_colpali.ipynb` needs the `colpali` group, which pins an older
  `transformers` and therefore cannot be installed alongside `hf`:
  `uv sync --no-default-groups --group dev --group colpali`.
- 02 and 03 read the "Attention Is All You Need" paper from `data/sample/1706.03762v7.pdf`.

## Sources

Extracted from the `AI-ENGINEERING-DEMYSTIFIED` monorepo (tag `pre-multirepo-split-2026-09`). Every notebook's original path is listed in [docs/content-inventory.csv](../../docs/content-inventory.csv).

Notebooks marked *RAG Techniques anthology* come from Nir Diamant's [RAG_Techniques](https://github.com/NirDiamant/RAG_Techniques) repository and remain under its non-commercial licence: see [docs/third_party/RAG_Techniques_LICENSE.txt](../../docs/third_party/RAG_Techniques_LICENSE.txt). Changes made here: file names and data/image paths only.
