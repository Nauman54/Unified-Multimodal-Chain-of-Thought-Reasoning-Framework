# 📚 Datasets

This project evaluates the proposed multimodal reasoning framework on two widely used benchmark datasets for scientific and visual question answering.

---

## 1. ScienceQA

**Source:** https://huggingface.co/datasets/derek-thomas/ScienceQA

ScienceQA is a large-scale multimodal benchmark designed for scientific question answering. Each sample may contain:

- 🖼️ Images and diagrams
- ❓ Multiple-choice questions
- 📖 Lecture explanations
- 💡 Hint information
- ✅ Ground-truth answers
- 🧠 Scientific reasoning context

The lecture and hint fields are incorporated into the prompt construction stage to improve contextual reasoning and Chain-of-Thought generation.

### Load Dataset

```python
from datasets import load_dataset

scienceqa = load_dataset("derek-thomas/ScienceQA")
```

---

## 2. A-OKVQA

**Source:** https://huggingface.co/datasets/HuggingFaceM4/A-OKVQA

A-OKVQA is a knowledge-based visual question answering benchmark that requires models to combine image understanding with commonsense reasoning.

Each sample contains:

- 🖼️ Real-world images
- ❓ Open-ended visual questions
- 🧠 Commonsense reasoning
- ✅ Multiple-choice answers
- 📚 External world knowledge

Unlike ScienceQA, A-OKVQA focuses on implicit visual understanding and commonsense inference rather than educational content.

### Load Dataset

```python
from datasets import load_dataset

aokvqa = load_dataset("HuggingFaceM4/A-OKVQA")
```

---

# 🔄 Dataset Unification

To create a generalized multimodal reasoning framework, both datasets are transformed into a common schema before training.

```
                 ScienceQA
                      │
                      │
                      ▼
             Dataset Preprocessing
                      ▲
                      │
                      │
                 A-OKVQA
                      │
                      ▼
      Unified Multimodal Representation
                      │
                      ▼
           Prompt Construction Engine
                      │
                      ▼
             BLIP-2 + Flan-T5 XL
```

The unified schema standardizes the following fields:

| Field | Description |
|--------|-------------|
| Image | Visual input |
| Question | Natural language question |
| Context | Lecture and hint information (when available) |
| Choices | Multiple-choice options |
| Answer | Ground-truth label |
| Rationale | Chain-of-Thought supervision |

This preprocessing pipeline enables the model to learn from both scientific and commonsense reasoning tasks using a consistent multimodal representation.
