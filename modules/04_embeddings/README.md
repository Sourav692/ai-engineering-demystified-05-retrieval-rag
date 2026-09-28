# Module 04 — Embeddings

What embeddings are, how to generate them with OpenAI and Hugging Face models, and how to compare and choose an embedding model.

| # | Notebook | You will learn |
|---|---|---|
| 01 | [01_embeddings_and_model_selection.ipynb](notebooks/01_embeddings_and_model_selection.ipynb) | Understand embeddings, similarity metrics and how to select an embedding model (canonical lesson) |
| 02 | [02_embedding_models.ipynb](notebooks/02_embedding_models.ipynb) | Generate and compare embeddings from OpenAI and Hugging Face models |
| 03 | [03_huggingface_embeddings.ipynb](notebooks/03_huggingface_embeddings.ipynb) | Create sentence embeddings with Hugging Face models and visualise similarity |
| 04 | [04_huggingface_embeddings_tutorial.ipynb](notebooks/04_huggingface_embeddings_tutorial.ipynb) | Alternative walkthrough of Hugging Face text embeddings (overlaps 03) |
| 05 | [05_openai_embeddings.ipynb](notebooks/05_openai_embeddings.ipynb) | Use OpenAIEmbeddings: models, dimensions and cosine similarity |
| 06 | [06_openai_embeddings_tutorial.ipynb](notebooks/06_openai_embeddings_tutorial.ipynb) | Alternative OpenAI embeddings walkthrough (overlaps 05) |
| 07 | [07_embeddings_deep_dive.ipynb](notebooks/07_embeddings_deep_dive.ipynb) | Go deeper on embeddings: batching, caching with CacheBackedEmbeddings and similarity behaviour |
| 08 | [08_compare_embedding_models_databricks.ipynb](notebooks/08_compare_embedding_models_databricks.ipynb) | Benchmark several embedding models side by side on Databricks with MLflow tracking |

## Before you run

- 03 and 04 overlap (two Hugging Face walkthroughs), as do 05 and 06 (two OpenAI walkthroughs);
  both are kept because they were written from different sources.
- Hugging Face notebooks need the `hf` group: `uv sync --group hf`.
- `08_compare_embedding_models_databricks.ipynb` runs on a Databricks workspace (Vector Search,
  Spark, MLflow); the `databricks` group installs the client libraries.

## Sources

Extracted from the `AI-ENGINEERING-DEMYSTIFIED` monorepo (tag `pre-multirepo-split-2026-09`). Every notebook's original path is listed in [docs/content-inventory.csv](../../docs/content-inventory.csv).
