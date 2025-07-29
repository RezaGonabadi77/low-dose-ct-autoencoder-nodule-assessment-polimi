# Attention-Enhanced U-Net for Low-Dose CT Simulation and Lung Nodule Malignancy Classification

This repository contains the full implementation of the research project developed as part of the Master's thesis titled:

> **"Attention-enhanced U-net autoencoder for Low-dose CT simulation and lung nodule malignancy assessment"**

📍 *Master of Science in Biomedical Engineering, Politecnico di Milano (2024–2025)*  
👨‍💻 **Author:** Reza Gonabadi  
📘 **Advisor:** Prof. Luca Mainardi  
🤝 **Co-advisor:** Jiaying Liu

---

## 🚀 Project Overview

Computed Tomography (CT) is a critical tool for early detection of lung cancer, but its radiation exposure limits its safe use in screening programs. This project tackles two major challenges:

1. **Low-Dose CT (LDCT) Simulation**: Using deep learning to simulate realistic LDCT images from standard-dose CT (FDCT) while preserving anatomical detail and noise characteristics.
2. **Lung Nodule Malignancy Assessment**: Radiomics-based classification of lung nodules using features extracted from both simulated and real LDCT scans.

---

## 🧱 Methodology

### 🔄 1. Low-Dose CT Simulation Pipeline

- **Input**: FDCT images from the 2016 AAPM Low-Dose CT Grand Challenge.
- **Models**:
  - Simple Autoencoder
  - U-Net with skip connections
  - ⚡ Attention-Enhanced U-Net *(final model)*

- **Loss Functions**:
  - AE: Mean Absolute Error (MAE)
  - U-Net: MAE + SSIM (30% / 70%)
  - Attention U-Net: MAE + SSIM (16% / 84%)

- **Evaluation Metrics**:
  - **PSNR**: up to 32.02 dB
  - **SSIM**: up to 0.9311
  - **NPS (Noise Power Spectrum)**: MAD = 0.0672

---

### 🩻 2. Lung Nodule Classification using Radiomics

- **Dataset**: LIDC-IDRI (1010 CT scans)
- **Features Extracted**: 851 radiomic features (shape, intensity, texture, wavelet)
- **Feature Selection**:
  - Stability (ICC > 0.75)
  - Positional robustness
  - Correlation filtering (|ρ| > 0.85)

- **Final Features**: 79
  - Shape-only (3)
  - Non-shape (76)
  - Combined (79)

- **Class Imbalance Handling**:
  - Augmentation for malignant class (dilation, erosion, noise injection, superpixels)

- **Classifiers Tested**:
  - Logistic Regression, MLP, Random Forest, AdaBoost, XGBoost, etc.

- **Best Results**:
  | Feature Set     | Best Model     | Balanced Accuracy | ROC AUC |
  |-----------------|----------------|-------------------|---------|
  | Shape-only      | Logistic Reg.  | 80.0%              | 0.839   |
  | Non-shape       | AdaBoost       | 78.3%              | 0.807   |
  | All features    | Random Forest  | 79.2%              | 0.831   |

---


