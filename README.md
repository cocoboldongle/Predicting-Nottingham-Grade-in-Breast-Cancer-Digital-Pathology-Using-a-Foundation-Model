# Predicting Nottingham Grade in Breast Cancer Digital Pathology Using a Foundation Model

This repository contains the source code for a deep learning pipeline to predict Nottingham histologic grades (Grade 1, 2, and 3) from breast cancer whole-slide images (WSIs).  
The implementation is based on the **Advanced Composite Multiple Instance Learning (ACMIL)** framework, adapted for histopathology applications.

---

## 📊 Dataset

We use the following publicly available datasets in this study:

| Dataset | Description | Link |
|--------|---------------------------|------|
| TCGA-BRCA | Whole-slide images and clinical metadata from The Cancer Genome Atlas (TCGA) Breast Invasive Carcinoma cohort | [TCGA Portal](https://portal.gdc.cancer.gov/) |
| BRACS | External validation dataset containing various annotated breast carcinoma WSIs | [BRACS Dataset](https://www.bracs.icar.cnr.it/) |

> 📌 **Note:** This pipeline is not limited to TCGA-BRCA or BRACS datasets and can be applied to any custom histopathology dataset.  
For detailed dataset preparation and patch extraction, please refer to the preprocessing guidelines in [CLAM](https://github.com/mahmoodlab/CLAM).

---

## 📥 Feature Extraction

This code supports flexible feature extraction options, including:
- **UNI model (ViT-L/16 pretrained via DINOv2)** — [UNI GitHub](https://github.com/mahmoodlab/UNI)
- **Vision Transformer ViT-S/16 (ImageNet pretraining)**
- **ResNet-18 (ImageNet pretraining)**

> Patch-wise feature extraction and tiling pipelines follow the method used in [CLAM](https://github.com/mahmoodlab/CLAM).

---

## 🧠 Multiple Instance Learning (MIL) Methods

This repository supports various MIL algorithms for histologic grading tasks.  
You can choose from the following implementations:

| MIL Method | Description | Code Link |
|------------|----------------------------|-----------|
| CLAM-SB | Clustering-constrained Attention MIL (single branch) | [CLAM](https://github.com/mahmoodlab/CLAM) |
| CLAM-MB | Clustering-constrained Attention MIL (multi-branch) | [CLAM](https://github.com/mahmoodlab/CLAM) |
| TransMIL | Transformer-based MIL | [TransMIL](https://github.com/binli123/dsmil-wsi) |
| DSMIL | Dual-stream MIL | [DSMIL](https://github.com/binli123/dsmil-wsi) |
| DTFD-MIL | Double-tier feature distillation MIL | [DTFD-MIL](https://github.com/winycg/DTFD-MIL) |
| ABMIL | Attention-based MIL | [CLAM (ABMIL)](https://github.com/mahmoodlab/CLAM) |
| **ACMIL** | Advanced Composite MIL with attention regularization | [ACMIL](https://github.com/dazhangyu123/ACMIL) |

---

## 🧪 Slide Preprocessing

- WSIs were tiled into patches (e.g., 256x256 px).
- Tissue detection used Otsu thresholding and morphological operations.
- Features extracted using selected backbone (UNI / ViT / ResNet).

> For preprocessing scripts, see [CLAM Preprocessing Pipeline](https://github.com/mahmoodlab/CLAM).

---

## 💻 Requirements

- Python ≥ 3.8  
- PyTorch ≥ 1.13  
- OpenSlide  
- scikit-learn, pandas, numpy, tqdm

```bash
pip install -r requirements.txt