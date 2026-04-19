# Copilot / AI agent instructions for this repo

This repository is a small learning workspace for LLM engineering (not a production app). Primary artifacts are notebooks and short scripts. Use these notes to be immediately productive when editing, refactoring, or extending the project.

- **Big picture:** This is a personal learning repo. The canonical entrypoints are `week1day5.ipynb` (experiments and examples) and `main.py` (simple script). Most development happens in notebooks; library usage is declared in `requirements.txt`.

- **Where to look first:**
  - `week1day5.ipynb` — primary experiment notebook using LangChain / OpenAI / other libs.
  - `requirements.txt` — list of packages the notebooks expect (OpenAI, LangChain, transformers, chromadb, etc.).
  - `.env` and `git_token.txt` — contain secrets; **do not commit or leak**. `.gitignore` already excludes `git_token.txt`.

- **Development / run workflow (typical):**
  1. Create and activate a venv: `python -m venv .venv && source .venv/bin/activate`.
  2. Install deps: `pip install -r requirements.txt`.
  3. Start JupyterLab: `jupyter lab` and open `week1day5.ipynb` for interactive work.
  4. Quick script run: `python main.py`.

- **Secrets and tokens:**
  - Environment secrets live in `.env`. Never add keys to source control. If you need to run actions that require API keys, load them from `.env` (the repo already includes one locally for convenience but it is sensitive).
  - `git_token.txt` exists locally and is ignored — do not attempt to move it into the repo.

- **Project conventions & patterns discovered here:**
  - Experiments are notebook-first. When a helper function becomes stable, extract it to a small `.py` module and import it from the notebook.
  - Add new dependencies to `requirements.txt` (one per line). After editing, run `pip install -r requirements.txt` in the venv.
  - Prefer reproducible, minimal examples in notebooks: small cells that can be re-run independently.

- **Integration points / external services used:**
  - OpenAI (`openai`), Anthropic (`anthropic`), Google Generative AI, Ollama — code in notebooks will reference these client libraries.
  - Local/embedded databases for vector stores: `chromadb` and commented `faiss-cpu` — tests/examples may expect a local vector DB.

- **For the AI agent (you): specific guidance**
  - When editing: preserve notebook cell intent; if adding non-trivial code prefer creating `utils.py` or `llm_helpers.py` and import it into the notebook.
  - When adding code that uses an external API, reference `.env` for credentials and add instructions to update `.env.example` if you create one.
  - Avoid committing secrets. If you see an API key in tracked files, flag it to the user immediately.
  - Keep changes small and notebook-friendly: add a short new notebook cell demonstrating usage rather than large in-place rewrites.

If anything here is unclear or you'd like the instructions to emphasize tests, CI, or packaging workflows, tell me which area to expand and I'll iterate.
