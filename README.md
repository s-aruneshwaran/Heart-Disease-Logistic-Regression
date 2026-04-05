# Heart Disease Prediction — Clinical Risk Analysis & Refit

A comprehensive statistical study using **Logistic Regression** in R to identify critical risk factors for heart disease. This project focuses on rigorous model diagnostics, including **influential outlier removal** and **multicollinearity checks**, to maximize predictive reliability.

---

## 🚀 Overview

* **Goal:** Predict the presence of heart disease (AHD) based on clinical and demographic variables.
* **Scope:** 303 clinical observations featuring diagnostic metrics like Cholesterol, Blood Pressure, and Max Heart Rate.
* **Method:** Data Imputation → Logistic Regression (Logit link) → **Cook's Distance Outlier Removal** → Model Refitting & ROC Evaluation.

---

## 📋 Data

* **Source:** Clinical Heart Disease Dataset (UCI/Open Source).
* **Target:** **AHD** (Binary: Yes/No converted to 1/0).
* **Predictors:** Age, Sex, ChestPain (4 types), RestBP, Chol, and MaxHR.
* **Preprocessing:** Mean imputation for `Ca`; Mode imputation for `Thal`.

---

## 🛠️ Tech Stack

* **Language:** **R**
* **Libraries:** * `pscl`: Pseudo-R² calculation
    * `pROC`: ROC Curve & AUC metrics
    * `car`: VIF for Multicollinearity detection
    * `lmtest`: Durbin-Watson autocorrelation test
    * `ggplot2`: Statistical visualization

---

## 🧪 Method & Model

1. **Model Fitting:** Initial Logistic Regression using the Logit link function:
   $$\ln\left(\frac{P}{1-P}\right) = \beta_0 + \beta_1X_1 + \dots + \beta_kX_k$$
2. **Multicollinearity:** Verified via **VIF** (All values < 2.0); no redundancy issues found.
3. **Autocorrelation:** **Durbin-Watson** test confirmed independent residuals ($DW \approx 2.0$).
4. **Outlier Detection:** Identified influential points using **Cook’s Distance** thresholding ($4/n$).
5. **Optimization:** Refitted the model on the cleaned subset to stabilize coefficients and reduce deviance.

---

## 📈 Results

The **Refit Model** showed significant improvements in predictive power and stability:

| Metric | Initial Model | **Refit Model (Optimized)** |
| :--- | :--- | :--- |
| **McFadden R²** | 0.363 | **0.565** |
| **AIC** | 284.18 | **187.32** |
| **Residual Deviance** | 266.18 | **169.32** |

* **Strongest Predictor:** **Sex (Male)** exhibited the highest odds ratio for heart disease risk.
* **Protective Factor:** **MaxHR** showed a negative coefficient; higher heart rates correlated with lower disease probability.
* **Accuracy:** The refit model correctly classified **246 out of 283** instances in the optimized dataset.

---

## ✅ Clinical Insights

* **Risk Factors:** High Resting Blood Pressure (**RestBP**) and specific **ChestPain** categories are primary drivers for positive diagnosis.
* **Discrimination:** The **ROC Curve** demonstrates high sensitivity and specificity, validating the model as a reliable secondary diagnostic tool.
* **Residual Health:** Post-refit diagnostics showed a consistent residual spread, successfully addressing **heteroscedasticity** found in the initial model.

---

## ⚠️ Limitations & Future Roadmap

* [ ] **Dataset Size:** Expand the study to include larger, multi-hospital datasets.
* [ ] **Missing Features:** Integrate **Fbs** (Fasting Blood Sugar) and **Oldpeak** if higher data confidence is achieved.
* [ ] **Deployment:** Build a **Shiny Dashboard** for real-time risk assessment by medical professionals.
* [ ] **Advanced Models:** Compare Logistic results with Random Forest or XGBoost.

---
