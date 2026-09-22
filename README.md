# RootsAcademy 2026 — NMBS Hands-On End-to-End ML

Predict Brussels↔Leuven train delays, working through the full ML
lifecycle in order: data understanding → feature engineering → modeling →
evaluation & storytelling.

## Requirements

- [Git LFS](https://git-lfs.com) — the historical delay data is too large for a plain git clone
- [uv](https://docs.astral.sh/uv/) — manages the Python version and environment for you, no separate Python install needed

## Setup

1. Install Git LFS and uv, if you don't have them already:

   **macOS:**
   ```bash
   brew install git-lfs
   curl -LsSf https://astral.sh/uv/install.sh | sh
   ```

   **Windows (PowerShell):**
   ```powershell
   powershell -ExecutionPolicy ByPass -c "irm https://astral.sh/uv/install.ps1 | iex"
   ```
   Git LFS on Windows doesn't have a one-line install — download and run the installer from [git-lfs.com](https://git-lfs.com).

   **Linux:** install Git LFS via your package manager (e.g. `apt install git-lfs` / `dnf install git-lfs`), then:
   ```bash
   curl -LsSf https://astral.sh/uv/install.sh | sh
   ```

2. Initialize Git LFS (one-time, any OS) and clone the repo:

   ```bash
   git lfs install
   git clone https://github.com/datarootsio/rootsacademy-2026-nmbs-hands-on.git
   cd rootsacademy-2026-nmbs-hands-on
   ```

   Already cloned without Git LFS installed? Run `git lfs pull` now to fetch the real file instead of a pointer stub.

3. Create the environment and install dependencies (pinned exactly via `uv.lock`, so everyone gets identical versions):

   ```bash
   uv sync
   ```

4. Verify the data actually downloaded — `data/raw/infrabel_historical_2026.csv` should be about 150MB:

   ```bash
   uv run python -c "import os; print(os.path.getsize('data/raw/infrabel_historical_2026.csv') / 1e6, 'MB')"
   ```

   Only a fraction of a MB? Git LFS didn't run — go back to step 2.

5. Launch Jupyter and open the first notebook:

   ```bash
   uv run jupyter notebook notebooks/assignment_notebooks/01_data_understanding_DIY.ipynb
   ```

Work through the four notebooks **in order** — each stage saves what the next one needs.
