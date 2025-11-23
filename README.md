

Create or replace README.md in the repo root with the following content (it includes links, license & citation blocks and points judges will look for):

# DataForge — The Resilient Autonomous Dataset Builder Agent

**Short description:**  
DataForge turns a single natural-language prompt into a Kaggle-ready CSV + metadata YAML in under 5 minutes — and still succeeds when every real source returns 403/404.

---

## Quick links
- Notebook / Demo: `notebooks/dataforge.ipynb` *(add if available)*
- Artifacts (example run): `artifacts/airbnb_20251121/`
- Architecture diagram: `architecture.png`
- Kaggle submission writeup: *(link to your Kaggle writeup once published)*

---

## What this project does
DataForge is a multi-agent pipeline (TopicExpander → SourceScout → EthicalGatekeeper → DataHarvester/Cleaner → ValidatorEnricher → SyntheticFallback) that automates dataset creation from a single prompt. It either harvests and merges public sources or, if no safe sources are available, generates realistic domain-aware synthetic data — annotated with full provenance, validation metrics, and reproducibility metadata.

---

## Included artifacts (example run)
The example run `artifacts/airbnb_20251121/` contains:
- `*.csv` — final dataset  
- `*.metadata.yaml` — schema + provenance + seed  
- `*.manifest.json` — sha256 checksums + reproduction info  
- `*.summary.json` — column statistics  
- `*.ks.json` — distribution sanity checks  
- `*.baseline.json` — baseline model performance (R² + CI)  
- `*_heatmap.png`, `*_hist.png` — quick visuals  
- `*.zip` — full bundle for judges

---

## How to reproduce (local / Kaggle)
1. Clone this repo:
```bash
git clone https://github.com/NAYANESHREDDY/DataForge-The-Truly-Resilient-Autonomous-Dataset-Builder-Agent.git
cd DataForge-The-Truly-Resilient-Autonomous-Dataset-Builder-Agent


(Optional) Create virtualenv:

python -m venv venv
source venv/bin/activate
pip install -r requirements.txt


Run the main notebook or script (example):

# if using the notebook: open in Colab or Kaggle and click "Run all".
# or run a script:
python src/run_dataforge.py --prompt "Build me dataset for predicting Airbnb occupancy 2025" --rows 5000


Inspect artifacts in artifacts/<run_id>/.

Quick evaluation checklist for judges

✅ Does *.metadata.yaml include "synthetic": true or "fallback_used"?

✅ Does manifest.json include a SHA256 and seed?

✅ baseline.json shows R² and CI.

✅ Visuals show reasonable distributions.

✅ human_review.json present for human sign-off.

Technology & key concepts

Gemini (google-genai) for schema proposals and prompt expansion (if API key provided)

Pandas / Numpy / SciPy / scikit-learn for harvesting, cleaning and baseline modeling

Faker for high-quality text/categorical values in synthetic mode

Session-based state & provenance saved in metadata and manifest

License

Code: MIT License — see LICENSE.
Generated datasets in artifacts/ are released under CC-BY-SA 4.0 (see dataset metadata.yaml entries).

Citation

If you use DataForge, please cite:

Chennareddy, Nayanesh Reddy (2025).
DataForge: The Resilient Autonomous Dataset Builder Agent.
https://github.com/NAYANESHREDDY/DataForge-The-Truly-Resilient-Autonomous-Dataset-Builder-Agent

Next additions (planned)

Add notebooks/dataforge.ipynb (single-run "Run All")

Add src/ module files & a requirements.txt (already prepared)

Add deployment/ containing Dockerfile and api.py for Cloud Run demo

Add unit tests under tests/ and a GitHub Actions workflow

Contact

Nayanesh Reddy Chennareddy — GitHub: NAYANESHREDDY


---

### After adding the files
1. `git add LICENSE CITATION.cff README.md`  
2. `git commit -m "Add license, citation and polished README"`  
3. `git push`

---

## What you *still* likely need (from the sample repo checklist)
You now have the highest-priority items. After pushing the above, consider adding next:

- `requirements.txt` (I provided content earlier) — **if you haven’t yet, add it.**
- `notebooks/dataforge.ipynb` (single “Run all” notebook).
- `src/` code files (move notebook code into modular source).
- `CITATION`/BibTeX or `CITATION.txt` (we added CFF already).
- `deployment/` (Dockerfile + `api.py`) if you want the bonus points for deployment.
- `tests/` and optionally a simple GitHub Actions CI.

If you want, I can now *automatically generate* the `src/` skeleton and `deployment/Dockerfile + api.py` and `tests/` for you — ready to paste. Say **“generate src + deployment + tests”** and I will output them immediately.
::contentReference[oaicite:0]{index=0}
