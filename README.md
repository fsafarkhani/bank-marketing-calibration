# 🎓 Well-Calibrated and Interpretable Propensity Models for Bank Marketing

Master’s Dissertation (M598, GISMA University of Applied Sciences)  
Student: **Fereshteh Sefarkhani (FS2025)** · Supervisor: [Add name if known]  
Department: Computer & Data Sciences (CDS) · Year: 2025  

---

## 🔍 Overview

This repository contains the full, reproducible machine learning pipeline developed for my MSc dissertation:  
**“Well-Calibrated and Interpretable Propensity Models with Calibration and SHAP for Bank Marketing.”**

The study explores how **probability calibration** and **explainable AI (SHAP)** can improve both the reliability and interpretability of predictive models for direct marketing campaigns.  
It is based on the **UCI Bank Marketing dataset**, where the goal is to predict whether a client will subscribe to a term deposit.

---

## ✨ Key Contributions

- Developed a **fully reproducible calibration framework** comparing Logistic Regression, CatBoost, XGBoost, and a Stacking ensemble.  
- Introduced **Isotonic and Sigmoid (Platt)** calibration for improved probability reliability.  
- Evaluated models using ROC-AUC, PR-AUC, and **Brier Score** for probability calibration.  
- Integrated **SHAP interpretability** for understanding the most influential behavioral and macroeconomic factors.  
- Validated a **policy recommendation**: limiting campaign contacts to ≤3 significantly improves conversion (12.1% vs 7.5%, *p < 0.001*).

---

## 📦 Dataset

- **Source:** UCI Machine Learning Repository – Bank Marketing Data  
- **Target:** `y` (term deposit subscription: yes/no)  
- **Leakage removed:** `duration`  
- **Added features:** `was_contacted_before`, `poutcome_success`  
- **Preprocessing:** one-hot encoding, scaling, class balancing  

If you reuse this dataset, please cite the original UCI Bank Marketing paper.

---

## 🧪 Methods (Pipeline)

**1. Data Preparation**  
Cleaning, feature selection, and engineered indicators for previous contact and outcome.  

**2. Model Development**  
Compared:
- Logistic Regression (baseline)
- CatBoost
- XGBoost
- Stacking (Cat + XGB)

**3. Calibration**  
Applied **Isotonic** and **Sigmoid** calibration to each model using cross-validation.  

**4. Evaluation Metrics**
- ROC-AUC  
- PR-AUC  
- Brier Score  
- Calibration Slope & Intercept  

**5. Interpretability**
- Global and local SHAP analysis  
- Dependence plots for key variables  
- Subgroup calibration (age-based fairness)

---

## 📈 Results (Summary)

| Model | Calibration | ROC-AUC | Brier | Notes |
|:------|:-------------|:--------|:------|:------|
| Logistic Regression | Isotonic | 0.80 | 0.078 | Baseline |
| CatBoost | Isotonic | 0.80 | 0.076 | Strong calibration |
| XGBoost | Isotonic | 0.78 | 0.080 | Slightly underfit |
| **Stacking (Cat+XGB)** | **Isotonic** | **0.80** | **0.075** | ✅ Champion Model |

**Calibration Slope = 1.07**, **Intercept = 0.10**, **CITL ≈ 0.00**

---

## 🧭 Policy Insights

| Policy | Description |
|:-------|:-------------|
| **Contact Frequency** | Limit marketing calls to ≤3 per client. Conversion significantly higher (*p < 0.001*). |
| **Channel Preference** | Mobile outreach performs better than landline. |
| **Future Validation** | Run small-scale A/B testing to confirm causality across regions. |

---

## 🛠️ Quickstart

1. **Environment setup**
   ```bash
   pip install pandas numpy matplotlib scikit-learn catboost xgboost shap
   
2.**Run notebook**
jupyter notebook bank_marketing_calibration.ipynb

3.**Dataset**
Place bank-additional-full.csv in the root folder.

4.**Output**
Calibration plots, SHAP summary, and statistical validation (Z-test) for campaign contact limit.

📂 **Repository Structure**
├─ data/
│   └─ bank-additional-full.csv
├─ figures/
│   └─ shap_summary.png
├─ results/
│   ├─ calibration_curves.png
│   └─ z_test_contacts.txt
├─ bank_marketing_calibration.ipynb
├─ final_results.html
├─ Dissertation_Fereshteh_Sefarkhani_2025.docx
├─ requirements.txt
└─ README.md

**Ethics & Data Integrity**
Dataset is public (UCI). No personal identifiers are included.

Analysis follows GISMA’s ethics guidance for reproducibility and data handling.

All preprocessing and modeling steps are fully transparent in the notebook.

**🧾 Citation**
If referencing this work:

Sefarkhani, F. M. (2025). Well-Calibrated and Interpretable Propensity Models with Calibration and SHAP for Bank Marketing.
MSc Dissertation, GISMA University of Applied Sciences.

**👩‍💻 Author**
Fereshteh Sefarkhani
MSc Data Science — GISMA University of Applied Sciences
📧 fereshteh.safarkhani@gmail.com
🌍 Berlin, Germany

  
