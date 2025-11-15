# bank-marketing-calibration# 🎓 Well-Calibrated and Interpretable Bank Marketing Models

This repository includes my MSc Data Science dissertation project at **GISMA University of Applied Sciences**.  
The main goal of this work is to build reliable and interpretable machine learning models that can predict whether a bank client will subscribe to a term deposit after a marketing campaign.

---

## 🧠 Project Motivation

Traditional predictive models often focus on accuracy but ignore *probability calibration* — how well predicted probabilities reflect reality.  
In banking and marketing, this can lead to poor targeting decisions and wasted resources.

This project aims to:
- Compare different calibration techniques (Isotonic and Sigmoid)
- Improve reliability and interpretability of predictions
- Provide clear business insights that can guide campaign policy

---

## ⚙️ Methods and Workflow

The analysis is based on the **UCI Bank Marketing Dataset**.  
After cleaning and feature engineering (removing `duration` to avoid leakage and adding features like `was_contacted_before`), several models were trained and calibrated.

**Main models tested:**
- Logistic Regression (baseline)
- CatBoost
- XGBoost
- Stacking (CatBoost + XGBoost)

Each model was evaluated using:
- ROC-AUC  
- Precision-Recall AUC  
- Brier Score (for calibration quality)  
- Calibration Slope and Intercept

Calibration was done with both **Isotonic** and **Sigmoid (Platt)** methods.

---

## 🧩 Key Results

- **Champion model:** Stacking (CatBoost + XGBoost) with Isotonic calibration  
  - ROC-AUC ≈ 0.80  
  - Brier ≈ 0.075  
  - Slope ≈ 1.07  
  - Intercept ≈ 0.10  

- The model shows strong reliability and interpretable SHAP explanations.

- **Contact frequency policy:**  
  Clients contacted three or fewer times had a significantly higher conversion rate  
  (12.1% vs. 7.5%, *Z = 5.15, p < 0.001*).  
  This supports the rule of limiting marketing calls to ≤3 per client.

- **Channel preference:**  
  SHAP results indicate that mobile (cellular) outreach performs better than landline calls.

---


🧭 Policy Insights Summary
Policy	Description
1. Contact Frequency	Limit marketing calls to three per client (≤3). Statistically validated using a Z-test (p < 0.001).
2. Channel Prioritization	Mobile calls outperform landlines. Finding is correlational, not causal.
3. Future Validation	Future work should test results through small A/B experiments across regions.

👩‍💻 Author
Safarkhani, F. M. (2025). Well-Calibrated and Interpretable Propensity Models with Calibration and SHAP for Bank Marketing. MSc Dissertation, GISMA University of Applied Sciences.
Fereshteh Sefarkhani

MSc Data Science — GISMA University of Applied Sciences
📧 [fereshteh.safarkhani@gmail.com]
