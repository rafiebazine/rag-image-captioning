# RAG Image Captioning: Data Audit & Retrieval Pipeline

---

## 📌 Project Overview
This repository contains the data preparation, preprocessing, metadata enrichment, embedding extraction, and FAISS indexing pipeline for a **Multimodal RAG Image Captioning System**.

The pipeline bridges visual feature extraction via **CLIP** (`openai/clip-vit-base-patch32`) and high-performance vector retrieval via **FAISS**, providing clean context to downstream language models for accurate image description.

---

## 🚀 Completed Pipeline Steps (Steps 5–8)

### 1. Caption Cleaning & Lexical Audit (Step 5)
* Text normalization: Lowercasing, punctuation stripping, and whitespace standardizing.
* Keyword diversity verification across semantic groups (Colors, Shapes, Environments, Lighting).

### 2. COCO Metadata Extraction (Step 6)
* Extraction of object annotations, categories, bounding boxes (`bbox`), and instance area metrics from COCO 2017.

### 3. CLIP Embeddings Generation (Step 7)
* Feature extraction using `openai/clip-vit-base-patch32`.
* $L_2$ normalization applied to all vectors to enable Cosine Similarity matching via inner products.

### 4. FAISS Indexing & Data Audit (Step 8)
* Built `FAISS.IndexFlatIP` indices for both image and caption vectors in `kb_10k`.
* Strict Data Leakage Audit: Confirmed $S_{\text{KB}} \cap S_{\text{Test}} = \emptyset$.

---

## 📂 Repository Structure

```
├── data/
│   ├── raw/                  # Downloaded COCO images & annotations
│   ├── processed/            # Cleaned captions & metadata JSONs
│   └── embeddings/           # CLIP visual & text embedding tensors (.pt / .npy)
├── index/
│   ├── faiss_image.index     # FAISS Index for Image-to-Image retrieval
│   └── faiss_text.index      # FAISS Index for Text-to-Image retrieval
├── notebooks/
│   └── preprocessing_audit.ipynb  # Steps 5-8 Execution Notebook
├── report/
│   └── rag_image_captioning_report.pdf # Formal PDF Report
└── README.md
```

---

## 🛠️ Usage Instructions

### 1. Environment Setup
```bash
pip install torch torchvision transformers faiss-cpu pillow pandas numpy
```

### 2. Running Preprocessing & Indexing
```bash
python scripts/run_pipeline.py --step all
```

### 3. Leakage Verification Test
```bash
python scripts/verify_audit.py
```

---
*Ready for fork and submission.*
