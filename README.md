# Skin Lesion Segmentation

This repository contains an end-to-end pipeline for **skin-lesion segmentation**, implemented in a Jupyter Notebook.  
The project evaluates how different **preprocessing strategies**, **model architectures**, and an **attention-based refinement module** influence segmentation performance.

> **Note:** Training is still running — detailed quantitative results will be added once all experiments finish.

---

## Project Overview

The notebook performs automatic segmentation of dermoscopic skin lesions using deep learning.  
It compares several preprocessing pipelines and segmentation models to determine which configuration produces the most accurate lesion masks.

The experiments are organized as follows:

### **Experiment 1 – Baseline Preprocessing (Resize + Normalize)**

- **Preprocessing:**
  - Resize to a fixed input size  
  - Standard normalization  

- **Models:**
  - U-Net  
  - EfficientNet-B0 encoder + U-Net decoder  
  - EfficientNet-B0 encoder + U-Net++ decoder  

---

### **Experiment 2 – Advanced Preprocessing (Hair Removal + CLAHE)**

- **Preprocessing:**
  - Morphology-based hair removal  
  - CLAHE contrast enhancement  
  - Resize + normalization  

- **Models:**
  - U-Net  
  - EfficientNet-B0 encoder + U-Net decoder  
  - EfficientNet-B0 encoder + U-Net++ decoder  

This experiment tests whether adding hair removal and contrast enhancement improves performance over the baseline from Experiment 1.

---

### **Experiment 3 – Attention-Based Refinement (CBAM)**

- **Preprocessing:**
  - Resize + normalization  

- **Model:**
  - EfficientNet-B0 encoder + U-Net decoder  

- **Post-processing / Refinement:**
  - A CBAM-based refinement head applied **after** the main segmentation logits  
    - The base model outputs a segmentation map  
    - A lightweight CBAM module refines this map to improve lesion boundaries and reduce small artifacts  

This experiment isolates the effect of the CBAM refinement compared to the baseline EfficientNet+U-Net configuration from Experiment 1.

---

## Metrics & Evaluation

Across all experiments, the following are computed:

- **Dice score**
- **Intersection-over-Union (IoU)**
- Precision
- Recall
- Qualitative **visualizations of predictions** (overlay of masks on the original images)

The final goal is to develop a robust segmentation model that improves lesion-boundary precision and can support downstream diagnostic tasks.

---

---

## Results

The following tables summarize the performance of all models across the three experiments.  
Fill in the Dice / IoU / Precision / Recall values once training finishes.

---

### **Experiment 1 – Baseline Preprocessing (Resize + Normalize)**

| Model                                | Dice | IoU  | Precision | Recall |
|--------------------------------------|------|------|-----------|--------|
| U-Net                                |88.33%|79.10%|  82.01%   | 95.71% |
| EfficientNet-B0 + U-Net              |92.08%|85.33%|  86.90%   | 97.93% |
| EfficientNet-B0 + U-Net++            |92.13%|85.41%|  87.84%   | 96.87% |

---

### **Experiment 2 – Advanced Preprocessing (Hair Removal + CLAHE)**

| Model                                | Dice | IoU  | Precision | Recall |
|--------------------------------------|------|------|-----------|--------|
| U-Net                                |      |      |           |        |
| EfficientNet-B0 + U-Net              |      |      |           |        |
| EfficientNet-B0 + U-Net++            |      |      |           |        |

---

### **Experiment 3 – Attention-Based Refinement (CBAM)**

| Model                                | Dice | IoU  | Precision | Recall |
|--------------------------------------|------|------|-----------|--------|
| EfficientNet-B0 + U-Net (no CBAM)    |92.08%|85.33%|  86.90%   | 97.93% |
| EfficientNet-B0 + U-Net + CBAM       |92.83%|86.61%|  88.62%   | 97.46% |

---

### **Summary Comparison**


| Experiment |             Best Model                | Dice | IoU  |
|------------|---------------------------------------|------|------|
| Exp 1      | EfficientNet-B0 + U-Net++             |92.03%|85.41%|
| Exp 2      | EfficientNet-B0 + U-Net++ + PreProcessing|92.83%|86.61%|
| Exp 3      | EfficientNet-B0 + U-Net + CBAM        |92.83%|86.61%| 

---



## Data

This project uses dermoscopic images from the **HAM10000** dataset and related research sources.  
The dataset itself is **not included** in this repository.  

**References:**

- Tschandl, P., Rinner, C., Apalla, Z. *et al.*  
  *Human–computer collaboration for skin cancer recognition.* Nat Med (2020).  
  https://doi.org/10.1038/s41591-020-0942-0  

- Tschandl, P., Rosendahl, C. & Kittler, H.  
  *The HAM10000 dataset: a large collection of multi-source dermatoscopic images of common pigmented skin lesions.* Sci Data 5, 180161 (2018).  
  https://doi.org/10.1038/sdata.2018.161  

---
