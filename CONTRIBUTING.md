# Contributing

1. `uv sync` then `uv run pre-commit install` — the hooks strip notebook outputs and run the structural checks.
2. Keep every lesson inside the topic this repository owns. The boundary rules are listed under **Out of scope** in the README; content owned by a later repository goes there, not here.
3. Notebooks: first markdown cell is a `# Title`, outputs cleared, and any file a notebook reads sits inside this repository at a path relative to the notebook.
4. New sample data needs an entry in `docs/data-sources.md` (source, license, SHA-256).
5. Before opening a PR: `uv run pytest` must pass offline, with no API keys set.
