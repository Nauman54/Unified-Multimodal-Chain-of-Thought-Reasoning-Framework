# Multimodal-Chain-of-Thought-Reasoning-via-Vision-Language-Fusion-Using-ViT-and-T5-on-ScienceQA
Multimodal Chain-of-Thought reasoning framework for ScienceQA using Vision Transformer (ViT) and T5. The system performs image-text fusion, rationale generation, and answer prediction through a two-stage reasoning pipeline with embedding-level multimodal fusion, mixed precision training, and interpretable AI reasoning.

This project implements a lightweight multimodal fusion architecture inspired by:

**Multimodal Chain-of-Thought Reasoning in Language Models**  
https://arxiv.org/abs/2302.00923

---

# 📌 Overview

This project combines:

- 👁️ Vision Transformer (ViT) for image understanding
- 🧠 T5 for language reasoning and generation
- 🔗 Embedding-level multimodal fusion
- 🧩 Two-stage Chain-of-Thought reasoning
- 📊 ScienceQA benchmark dataset

The system first generates a rationale (reasoning explanation) and then predicts the final answer using multimodal context.

---

# 🏗️ System Pipeline

```text
Input Image + Question + Context + Options
                │
                ▼
      Vision Transformer (ViT)
                │
        Visual Embeddings
                │
                ▼
      Linear Projection Layer
                │
                ▼
      T5 Text Embeddings
                │
                ▼
      Embedding-Level Fusion
                │
                ▼
      Stage 1: Rationale Generation
                │
                ▼
      Stage 2: Final Answer Prediction
