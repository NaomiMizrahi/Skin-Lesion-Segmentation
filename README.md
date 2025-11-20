# Skin Lesion Segmentation

This repository contains a complete end-to-end pipeline for **skin-lesion segmentation**, implemented in a Jupyter Notebook.  
The project evaluates how different **preprocessing strategies**, **model architectures**, and a **post-processing refinement module** influence segmentation performance.

> **Note:** Training is still running — results will be added soon.

---

## Project Overview

The notebook performs automatic segmentation of dermoscopic skin lesions using deep learning.  
It compares several preprocessing pipelines and segmentation models to determine the configuration that produces the most accurate lesion masks.

### Included in This Project

#### **Preprocessing**
- Morphology-based hair removal  
- CLAHE contrast enhancement  
- Standard resizing and normalization  

#### **Model Architectures**
- U-Net  
- U-Net with EfficientNet-B0 encoder  
- U-Net++ with EfficientNet-B0 encoder  

#### **Model Variants Compared**
- Raw images (resize + normalization only)  
- Hair removal + CLAHE  

#### **Post-Processing**
- Residual convolutional refinement block to enhance boundary quality  

#### **Training & Evaluation**
- Full training/validation pipeline  
- Dice score, IoU, and additional segmentation metrics  
- Visual error analysis  

The final goal is to develop a robust segmentation model that improves lesion-boundary precision and supports downstream diagnostic tasks.

---

## Results (coming soon)

This section will be updated once all experiments finish running.

---

## Data

This project uses dermoscopic images from the HAM10000 dataset and related research.  
The dataset itself is **not included** in this repository.

**References:**

- Tschandl, P., Rinner, C., Apalla, Z. *et al.*  
  *Human–computer collaboration for skin cancer recognition.* Nat Med (2020).  
  https://doi.org/10.1038/s41591-020-0942-0  

- Tschandl, P., Rosendahl, C. & Kittler, H.  
  *The HAM10000 dataset: a large collection of multi-source dermatoscopic images of common pigmented skin lesions.* Sci Data 5, 180161 (2018).  
  https://doi.org/10.1038/sdata.2018.161  

---
