# 🧠 Early Detection of Alzheimer’s Dementia Using Multimodal Clinical & MRI Biomarkers  
### *A Machine Learning Analysis of the OASIS-2 Longitudinal Cohort*  
📄 **Capstone Project – MS Health Data Science, Saint Louis University**  
👩‍🔬 **Author: Vudem Shruthi Reddy**

<p align="center">
  <img src="Alzheimers.png" width="650"/>
</p>

---

⚡ **Multimodal baseline prediction**  
🔍 **Responsible ML: no data leakage, ROC-optimal thresholds, full CV**  
📊 **Explainable AI with SHAP**  
🧬 **Scientific, reproducible, IEEE-grade workflow**

---

# 📌 Overview

This repository implements a fully reproducible, publication-quality machine learning pipeline for **baseline dementia classification** using the **OASIS-2 longitudinal neuroimaging dataset**.  
The project integrates **clinical**, **cognitive**, and **structural MRI biomarkers** to determine whether dementia can be detected **at the first clinical visit**, before longitudinal changes occur.

The repository includes:

- 🧹 Complete preprocessing pipeline  
- 🧠 ML models: Logistic Regression & Random Forest  
- 🎯 ROC-optimal threshold evaluation  
- 🔁 Stratified 5-fold cross-validation  
- 📉 Full visualizations (distributions, ROC, PR, SHAP, correlations)  
- 🔎 SHAP explainability with interaction effects  
- 📑 Summary outputs for research & publication  

This work aligns with the mission of the **OASIS Research Consortium**, supporting high-quality open science in brain aging and dementia.

---

# 🧠 Background

Alzheimer’s disease is the most common cause of dementia and produces measurable changes in **cognition**, **brain structure**, and **functional ability** years before diagnosis.  
Early identification enables:

- 🧭 Earlier, proactive clinical decisions  
- 💊 Improved therapeutic opportunities  
- 🧬 Understanding disease trajectory  
- 🤝 Better support for families  

The OASIS-2 dataset provides a rare combination of **MRI**, **clinical measures**, and **longitudinal follow-up**, making it an exceptional resource for baseline dementia modeling.

---

# 🎯 Goals of the Study

This project aims to build a **transparent, multimodal, reproducible** ML framework to classify dementia status at baseline.  
The primary goals include:

- Characterizing baseline differences in cognition, SES, brain volume, and age  
- Developing multimodal ML models for dementia classification  
- Comparing fixed-threshold vs **ROC-optimal thresholding**  
- Conducting stratified 5-fold CV for generalizable results  
- Using SHAP to reveal early biomarkers  
- Supporting OASIS’s mission of reproducible, clinically relevant ML research

---

# 📂 Dataset Summary

**Dataset:** OASIS-2 Longitudinal Dataset  
**Participants:** 150  
**MRI Sessions:** 373  
**Modeling dataset:** 150 (baseline only)

### Diagnostic distribution  
- 72 **Nondemented**  
- 64 **Demented**  
- 14 **Converted** → counted as “demented” for modeling

### Variables used in modeling
**Demographic:** Age, Sex  
**Cognitive:** MMSE  
**Socioeconomic:** SES, Education  
**MRI Biomarkers:**  
- nWBV (normalized whole-brain volume)  
- eTIV (estimated total intracranial volume)  
- ASF (atlas scaling factor)  

---

# 🛠 Methods

## 1️⃣ Preprocessing
- Baseline-only filtering  
- Numeric scaling  
- SES/MMSE missingness handling  
- Label encoding (sex, dementia group)

## 2️⃣ Machine Learning Models
- Logistic Regression  
- Random Forest Classifier  

## 3️⃣ Evaluation Metrics
- ROC-AUC, PR-AUC  
- Accuracy  
- Sensitivity  
- Specificity  
- Precision  
- Confusion Matrix  

## 4️⃣ Thresholding Strategy
- Default 0.50  
- **ROC-optimal (Youden Index)** → avoids misleading specificity = 1.0  

## 5️⃣ Cross-Validation
- **Stratified 5-fold CV**  
- Mean RF ROC-AUC ≈ **0.829**

## 6️⃣ Explainability
- SHAP summary plots  
- SHAP interaction effects  
- Feature importance mapping  

---

# 📊 Key Results

## 🔹 Baseline Differences
- Demented subjects:  
  - **Higher age**  
  - **Lower MMSE scores**  
  - **Lower nWBV**  
  - MRI measures supported known dementia atrophy patterns  

## 🔹 Model Performance (Test Set)

| Model | ROC-AUC | PR-AUC | Accuracy | Sensitivity | Specificity |
|------|---------|--------|----------|-------------|-------------|
| Logistic Regression (ROC-opt) | 0.705 | 0.798 | 0.633 | 0.625 | 0.643 |
| **Random Forest (ROC-opt)** | **0.714** | **0.812** | **0.733** | 0.562 | **0.929** |

## 🔹 Cross-Validation Summary (Random Forest)
- Mean ROC-AUC: **0.829 ± 0.026**  
- Stable performance across folds  
- PR-AUC ≈ 0.867  

## 🔹 SHAP Insights
Top global predictors:

1. **MMSE**  
2. **Age**  
3. **nWBV**  
4. **eTIV & ASF (scaling factors)**  

Important interactions include:

- MMSE × Age  
- MMSE × nWBV  

These reflect clinically meaningful dementia mechanisms.

---

# 📈 Visualizations Included

All figures are saved in the `figures/` directory:

- Class balance plot  
- Kernel density plots for all features  
- Correlation heatmap  
- ROC curve (Logistic & RF)  
- Precision–Recall curve  
- SHAP Summary Plot  
- SHAP Interaction Plot  
- CV Performance Tables  

All visualizations use clean color palettes optimized for publication.

---

# 💡 Interpretation & Impact

### 🌟 Clinical Importance
Baseline multimodal prediction supports early decision-making and diagnostic clarity during the first clinic visit.

### 🌐 Scientific Innovation
This study demonstrates that **multimodal machine learning** outperforms single-modality approaches and reveals biologically consistent structures in dementia prediction.

### 📘 Methodological Rigor
The pipeline enforces:

- Proper CV  
- No leakage  
- ROC-optimal thresholding  
- Thorough explainability  

### 🏛 Organizational Benefit
OASIS Consortium and similar groups can use this pipeline to:

- Benchmark dementia prediction algorithms  
- Support reproducible ML  
- Generate research hypotheses  
- Guide dataset enhancement  

---

# 📁 Repository Structure

```
📦 Alzheimer-Dementia-ML
│
├── data/
│   └── oasis_longitudinal_demographics.xlsx
│
├── src/
│   ├── preprocessing.py
│   ├── modeling.py
│   ├── evaluation.py
│   └── explainability.py
│
├── notebooks/
│   └── ALZHEIMERS.ipynb
│
├── figures/
│   ├── roc_curve_rf.png
│   ├── pr_curve_rf.png
│   ├── feature_dists.png
│   ├── correlation_heatmap.png
│   ├── shap_summary.png
│   └── shap_interaction.png
│
└── README.md
```

---

# ▶️ How to Run

### Install dependencies
```bash
pip install -r requirements.txt
```

### Run the notebook
```bash
jupyter notebook ALZHEIMERS.ipynb
```

### Run the script
```bash
python main.py
```

---

# 🔬 References (Verified Scientific Sources)

- Marcus et al. (2007). OASIS longitudinal MRI dataset.  
- Buckner et al. (2004). Unified morphometric analysis.  
- Morris (1993). CDR scoring system.  
- Fotenos et al. (2005). Brain volume decline norms.  
- Lundberg & Lee (2017). SHAP methodology.  
- Pedregosa et al. (2011). Scikit-learn ML library.  
- Pini et al. (2016). Brain atrophy in aging & AD.  
- Tustison et al. (2010). N4ITK MRI correction.  

---

# ⭐ Acknowledgements
Thanks to the **OASIS Research Consortium**, faculty mentors, and contributors who support open, transparent neuroscience.

