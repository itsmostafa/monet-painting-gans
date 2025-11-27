# Histopathologic Cancer Detection

Binary image classification to detect metastatic cancer in histopathologic scans of lymph node sections.

**Kaggle Competition**: https://www.kaggle.com/c/histopathologic-cancer-detection/

## Dataset

The dataset is derived from the PatchCamelyon (PCam) benchmark:

- **Training images**: 220,025 patches (96×96 pixels, RGB)
- **Test images**: 57,458 patches
- **Labels**: Binary classification based on the central 32×32 region
  - `0`: No tumor tissue
  - `1`: Tumor tissue present
- **Class distribution**: ~59.5% negative, ~40.5% positive

## Approach

The notebook implements a custom CNN with:
- 4 convolutional blocks (32 → 64 → 128 → 256 filters)
- Batch normalization and dropout regularization
- Data augmentation (flips, rotations, color jitter)
- Adam optimizer with ReduceLROnPlateau scheduler

**Evaluation metric**: AUC-ROC

## Project Structure

```
├── notebooks/
│   └── cancer_detection.ipynb   # EDA, training, and evaluation
├── data/                        # Competition data (gitignored)
│   ├── train/                   # Training images (.tif)
│   ├── test/                    # Test images (.tif)
│   ├── train_labels.csv
│   └── sample_submission.csv
└── pyproject.toml
```

## Setup

```bash
# Install dependencies
uv sync

# Start Jupyter
uv run jupyter notebook
```

Download the competition data from Kaggle and extract to `data/`.

## AI Citation

- "Fix any grammatical issues with the following assignment." prompt. ChatGPT, GPT 5, OpenAI, November 25th, 2025 chat.openai.com/chat
