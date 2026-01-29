# Takaku Lab – cfDNA Project

Welcome to the **cfDNA Project** repository.  
This repository contains the machine learning pipeline used to identify cancer-specific chromatin features from cell-free DNA (cfDNA), as published in [Nature Communications Biology (2025)](https://www.nature.com/articles/s42003-025-08920-0).

---

## cfDNA Project Members

- **Dr. Motoki Takaku** – Principal Investigator  
- **Sakuntha Gunarathna** – Graduate Researcher
- **Nazim Belabbaci** - Graduate Researcher

---

🛠 Pipeline Overview

We developed the end-to-end processing and classification framework, which transforms raw genomic signal data into interpretable diagnostic insights.
1. Feature Engineering & Signal Extraction

    Signal Processing: Utilized deepTools (v3.5.6) and multiBigwigSummary to extract normalized signal values from .bigWig files.

    Dimensionality Reduction: Converted high-resolution genomic data into numerical feature matrices using 10kb bins.

    Targeted Regions: Engineered features across whole-genome scales and specific loci (EdgeR-derived peaks and ATAC-seq peaks from CD4+ T, T47D, PANC1, and PEO1 cell lines).

2. Model Architecture: XGBoost Classification

    Model: Gradient Boosted Trees (XGBoost) with binary:logistic objective.

    Optimization: Implemented a hybrid approach using Randomized Search and Hyperparameter Grid Search (tuning learning_rate, reg_lambda, and scale_pos_weight).

    Robustness: Utilized early_stopping (15-round patience) and k-fold cross-validation (k=3–10) to prevent overfitting and ensure model stability.

3. Performance Metrics

    Primary Metric: Area Under the Precision-Recall Curve (AUC-PR).

    Validation: Balanced Accuracy (scikit-learn v1.3.2), ROC-AUC, and confusion matrix-derived sensitivity/specificity
