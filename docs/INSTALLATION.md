# ⚙️ Installation Guide

This guide explains how to set up the **Unified Multimodal Chain-of-Thought Reasoning Framework** for training and inference.

---

# 📋 Prerequisites

Before installing the project, ensure you have the following:

| Requirement | Version |
|-------------|----------|
| Python | 3.10+ |
| Git | Latest |
| CUDA (Optional) | 11.8+ |
| NVIDIA GPU (Recommended) | 16 GB VRAM or higher |
| pip | Latest |

> **Recommended Hardware**
>
> - NVIDIA RTX 3080 / 3090 / 4090
> - NVIDIA A100
> - Google Colab Pro / Kaggle GPU
> - At least **16 GB GPU memory** for training BLIP-2 with LoRA.

---

# 1️⃣ Clone the Repository

```bash
git clone https://github.com/Nauman54/Unified-Multimodal-Chain-of-Thought-Reasoning-Framework.git

cd Unified-Multimodal-Chain-of-Thought-Reasoning-Framework
```

---

# 2️⃣ Create a Virtual Environment

### Windows

```bash
python -m venv venv

venv\Scripts\activate
```

### Linux / macOS

```bash
python3 -m venv venv

source venv/bin/activate
```

---

# 3️⃣ Upgrade pip

```bash
python -m pip install --upgrade pip
```

---

# 4️⃣ Install Project Dependencies

Install all required Python packages.

```bash
pip install -r requirements.txt
```

---

# 5️⃣ Verify PyTorch Installation

Run:

```bash
python
```

Then execute:

```python
import torch

print(torch.__version__)
print(torch.cuda.is_available())
```

Expected output:

```text
2.x.x
True
```

If `False` is returned, CUDA is not configured correctly.

---

# 6️⃣ Download the Datasets

The project automatically downloads the datasets from Hugging Face.

### ScienceQA

```python
from datasets import load_dataset

scienceqa = load_dataset("derek-thomas/ScienceQA")
```

### A-OKVQA

```python
from datasets import load_dataset

aokvqa = load_dataset("HuggingFaceM4/A-OKVQA")
```

Datasets will be cached locally after the first download.

---

# 7️⃣ Authenticate with Hugging Face (Optional)

Some pretrained models require authentication.

Install the Hugging Face CLI:

```bash
pip install huggingface_hub
```

Login:

```bash
huggingface-cli login
```

Paste your Hugging Face access token when prompted.

---

# 8️⃣ Launch Jupyter Notebook

```bash
jupyter notebook
```

or

```bash
jupyter lab
```

Open the notebooks from the `notebooks/` directory.

---

# 📂 Recommended Execution Order

Run the notebooks in the following order:

1. **Baseline Notebook**
   - Reproduces the original Multimodal-CoT architecture.

2. **Modernized Pipeline Notebook**
   - BLIP-2
   - Q-Former
   - LoRA
   - 4-bit Quantization
   - Label Masking
   - Unified Dataset Training

3. **Inference & Evaluation**
   - Generate Chain-of-Thought reasoning
   - Predict answers
   - Evaluate model performance

---

# 🔧 Troubleshooting

## CUDA Not Detected

Check GPU availability:

```python
import torch

torch.cuda.is_available()
```

If it returns `False`:

- Install the CUDA-enabled version of PyTorch.
- Update NVIDIA GPU drivers.
- Verify CUDA installation.

---

## Out of Memory (OOM)

If training fails due to GPU memory limitations:

- Reduce batch size.
- Increase gradient accumulation steps.
- Enable 4-bit quantization.
- Use LoRA instead of full fine-tuning.

---

## Dataset Download Issues

Update the Hugging Face datasets library:

```bash
pip install --upgrade datasets
```

Clear the cache if necessary:

```bash
huggingface-cli scan-cache
```

---

# ✅ Verify Installation

Run the following command:

```bash
python -c "import torch, transformers, datasets, peft; print('Installation Successful!')"
```

If no errors are displayed, the environment has been configured successfully.

---

# 🚀 Next Steps

After installation:

- Read the **Architecture Guide** (`docs/ARCHITECTURE.md`)
- Explore the **Datasets Guide** (`docs/DATASETS.md`)
- Follow the **Training Guide** (`docs/TRAINING.md`)
- Run the notebooks to reproduce the experiments.
