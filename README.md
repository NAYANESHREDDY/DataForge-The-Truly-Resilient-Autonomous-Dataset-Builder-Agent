# DataForge-The-Truly-Resilient-Autonomous-Dataset-Builder-Agent
DataForge turns a single natural-language prompt into a Kaggle-ready CSV + metadata YAML in under 5 minutes — and still succeeds when every real source returns 403/404.
DataForge Artifact — Airbnb Dataset (2025-11-21)

Run ID: dataforge_build_me_a_dataset_for_predicting_airbnb_20251121T184912Z_3614a4
Domain: Short-term rental demand / Airbnb analytics
Purpose: Predicting future Airbnb occupancy, pricing, and guest rating patterns for 2025.

📌 Overview

This folder contains all generated artifacts for a complete DataForge pipeline run triggered by the prompt:

“Build me a dataset for predicting Airbnb in 2025.”

This run showcases DataForge’s multi-agent system, including schema design, synthetic generation (where required), validation, observability, and full reproducibility with metadata, manifest, and baseline model evaluation.

Everything in this folder is self-contained — judges can validate, reproduce, and audit without accessing the internet.

📁 Artifact Contents
1. Main dataset
File	Description
*.csv	The final dataset (tabular, cleaned, validated), ready for ML workflows and Kaggle competitions.
2. Metadata & Provenance
File	Description
*.metadata.yaml	Schema of all columns, datatypes, row count, generation method, fallback usage, seed, timestamp, and ethical provenance.
*.manifest.json	SHA256 checksum, reproducibility info, seed, and model-usage flag (Gemini used or fallback).
3. Validation & Quality Checks
File	Description
*.summary.json	Column-level statistics: mean, std, min/max, missingness, unique values.
*.ks.json	Kolmogorov–Smirnov tests for numeric distribution sanity checks.
*.baseline.json	Baseline LinearRegression performance (R² + bootstrapped 95% confidence interval).
*.human_review.json	Template for manual reviewer notes (for human-in-the-loop validation).
4. Visuals
File	Description
*_heatmap.png	Correlation matrix for numeric features.
*_hist.png files	Distribution histograms for key features (ratings, occupancy rate, etc.).
5. Bundle
File	Description
*.zip	All files zipped together for fast download and offline sharing.
🔁 Reproducibility Instructions
▶️ Regenerate the dataset

Using DataForge:

prompt = "Build me a dataset for predicting Airbnb in 2025"
seed = 42
rows = 5000


Running the DataForge notebook or API with these parameters will produce a bit-identical synthetic dataset (identical SHA256 hash), assuming synthetic fallback mode was used.

▶️ Validate using included utilities

If you're running locally:

python validation_and_eval.py artifacts/airbnb_20251121/*.csv


This will recompute:

R² baseline

Confidence intervals

Distribution tests

Feature statistics

Expected R² (from this run):
~0.72 to 0.76, depending on built-in noise injection.

🔍 Notes on This Run

Real-source scouting failed (403/404): Common on Kaggle/Colab restricted environments.

The system used TaskAwareSyntheticFallback to generate realistic Airbnb data using:

host activity patterns

average guest ratings

occupancy distributions

price curves by season

city-level features modeled using plausible tourism data

All synthetic outputs are clearly marked in metadata.

This is intentional and demonstrates the “resilient fallback” feature — one of DataForge’s key innovations.

🧪 How Judges Can Inspect the Dataset

Recommended steps:

1. Open the metadata file

Check:

Schema

Synthetic flag

Generating seed

Generator model

Value distributions per field

2. Verify CSV integrity

Using manifest SHA256.

3. Load summary.json

Inspect:

missingness

category balance

numeric feature distribution

4. Review baseline.json

Confirms dataset is predictive enough for ML tasks.

5. Examine plots

Heatmap

Histograms
for quality & realism.

⚖️ Licensing and Usage

This artifact is distributed under:
CC-BY-SA 4.0
Synthetic-only; no personal data; compliant with Kaggle Capstone requirements.
