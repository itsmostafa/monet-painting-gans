# Use GANS to paint like Monet

**Kaggle Competition**: [I’m Something of a Painter Myself](https://www.kaggle.com/competitions/gan-getting-started/overview)

## Dataset

The dataset consists of two domains:

- **Monet paintings**: 300 images at 256x256 pixels
- **Photographs**: 7,028 images at 256x256 pixels

Data is available from the [Kaggle competition page](https://www.kaggle.com/competitions/gan-getting-started/data) and should be extracted to `kaggle/input/gan-getting-started/`

## Approach

This project uses a **CycleGAN** (Cycle-Consistent Generative Adversarial Network) for unpaired image-to-image translation.

**Architecture:**
- **Two Generators**: ResNet-based with 9 residual blocks and Instance Normalization
  - G_AB: Photo → Monet (used for submission)
  - G_BA: Monet → Photo
- **Two Discriminators**: PatchGAN (70x70 receptive field)
  - D_A: Distinguishes real from fake Monet
  - D_B: Distinguishes real from fake Photo

**Loss Functions:**
- Adversarial loss (LSGAN)
- Cycle consistency loss (L1) - ensures photo→monet→photo ≈ photo
- Identity loss (L1) - helps preserve color composition

**Training:**
- Batch size: 1
- Learning rate: 2e-4 with linear decay after epoch 25
- Optimizer: Adam (β1=0.5, β2=0.999)
- Replay buffer for discriminator stability

**Evaluation:** MiFID (Memorization-informed Fréchet Inception Distance) - lower is better, competitive scores are 50-100

## Project Structure

```
.
├── monet-cyclegan.ipynb    # Main notebook with full implementation
├── kaggle/input/           # Dataset directory (download from Kaggle)
│   └── gan-getting-started/
│       ├── monet_jpg/      # 300 Monet paintings
│       └── photo_jpg/      # 7,028 photographs
├── outputs/                # Training outputs
│   ├── checkpoints/        # Model checkpoints during training
│   ├── cyclegan_final.pth  # Final trained model
│   ├── images.zip          # Submission file (7,028 generated images)
│   └── *.png               # Sample images and training plots
├── pyproject.toml          # Project dependencies
└── README.md
```

## Setup

```bash
# Install dependencies (requires uv package manager)
uv sync

# Download dataset from Kaggle
kaggle competitions download -c gan-getting-started
unzip gan-getting-started.zip -d kaggle/input/gan-getting-started/

# Run the notebook
uv run jupyter notebook monet-cyclegan.ipynb
```

## AI Citation

- "Fix any grammatical issues with the following assignment." prompt. ChatGPT, GPT 5, OpenAI, November 25th, 2025 chat.openai.com/chat
