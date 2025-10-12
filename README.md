# Gallstone Disease Prediction for Final Project

## Project Overview
This repository explores supervised learning techniques for predicting gallstone disease from 39 clinical variables collected at Ankara VM Medical Park Hospital (319 patient records). The workflow lives in a Jupyter notebook that walks through exploratory data analysis, feature selection, model benchmarking, and interpretation of risk factors.

## Dataset
- Source: [UC Irvine Machine Learning Repository – Gallstone-1](https://archive.ics.uci.edu/dataset/1150/gallstone-1)
- Target: `Gallstone Status` (0 = no stones, 1 = stones present)
- Feature highlights: age, anthropometrics, metabolic indicators, comorbidities
- Dataset: `data/gallstone-disease.json`

## Repository Structure
```
predict-gallstone-disease/
├── data/                     # Gallstone dataset (JSON format)
├── notebooks/
│   └── gallstone_analysis.ipynb  # Main end-to-end analysis
├── results/
│   ├── figures/              # Saved plots (created by notebook)
│   └── reports/              # Tables and summaries (optional)
├── main.py                   # Placeholder entry point
├── pyproject.toml            # Project metadata and dependencies
└── uv.lock                   # Resolved dependency lock file
```

## Environment Setup
Python 3.13 is specified in `pyproject.toml`. Install dependencies with either [uv](https://docs.astral.sh/uv/) or pip:

```bash
# Using uv (recommended)
uv sync

# Using pip
python -m venv .venv
source .venv/bin/activate
pip install ipykernel matplotlib pandas scikit-learn seaborn statsmodels
```

## Running the Analysis
1. Activate the environment created above.
2. Launch Jupyter: `jupyter notebook` (installed via dependencies).
3. Open `notebooks/gallstone_analysis.ipynb` and execute the cells in order. The notebook covers:
   - data loading and validation
   - exploratory visualizations
   - feature selection comparisons
   - model training (logistic regression, random forest, gradient boosting, SVM, etc.)
   - performance evaluation and clinical interpretation

Artifacts such as figures, trained models, and summary tables are written to the corresponding subdirectories in `results/`.

## Code Quality
Run the Ruff linter to check style and potential issues:

```bash
ruff check .
```

#### AI Citation

"Fix any grammatical issues with the following assignment." prompt. ChatGPT, GPT 5, OpenAI, October 11th, 2025 chat.openai.com/chat
"Summarize the analysis results in the given jupyter notebook." prompt. ChatGPT, GPT 5, OpenAI, October 11th, 2025 chat.openai.com/chat
