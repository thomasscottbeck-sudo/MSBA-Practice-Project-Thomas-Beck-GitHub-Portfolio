# Home Credit Default Risk Analysis: The "Turnaround" Strategy

**Role:** Lead Architect & Data Scientist  
**Date:** Fall 2025  
**Status:** Complete (Champion Model AUC: 0.742)  

---

## 1. Executive Summary
**The Mission:** Home Credit aims to broaden financial inclusion for unbanked populations by providing positive borrowing experiences. The core challenge is **Information Asymmetry**: predicting repayment capability without traditional credit histories.

**The Problem:** Standard accuracy metrics fail due to a severe **92:8 class imbalance** (only 8% default). A model predicting "all repay" would be 92% accurate but useless.

**The Solution:** This repository documents a production-grade data science pipeline that optimizes for **Risk Ranking (AUC-ROC)**. By identifying "invisible" high-risk applicants, the model enables a "Top Decile" strategy—flagging the riskiest 10% of applicants to capture ~60% of defaults without stalling user acquisition.

---

## 2. Project Dashboard
*Click "Source" to view code logic or "Report" for the rendered executive summary.*

| Phase | Deliverable | Source Code | Executive Report |
| :--- | :--- | :---: | :---: |
| **I. Discovery** | **01. Independent Analysis**<br>*(Hypothesis Validation)* | [View .qmd](./01_ThomasBeck_Individual_EDA.qmd) | [View HTML](https://thomasscottbeck-sudo.github.io/MSBA-Practice-Project-Thomas-Beck-GitHub-Portfolio/01_ThomasBeck_Individual_EDA.html) |
| **II. R&D** | **02. Neural Network PoC**<br>*(Python Experimentation)* | [View .ipynb](./02_Individual_PoC_Models.ipynb) | [View HTML](https://thomasscottbeck-sudo.github.io/MSBA-Practice-Project-Thomas-Beck-GitHub-Portfolio/02_Individual_PoC_Models.html) |
| **III. Baseline** | **03. Legacy Team Draft**<br>*(The "Before" State)* | [View .Rmd](./03_Team_Model_(Frankenstein)Draft.Rmd) | [View HTML](https://thomasscottbeck-sudo.github.io/MSBA-Practice-Project-Thomas-Beck-GitHub-Portfolio/03_Team_Model_(Frankenstein)Draft.html) |
| **IV. Engineering** | **04. Pipeline Polish**<br>*(Refactoring & Speed)* | [View .qmd](./04_Team_Model_Polishing.qmd) | [View HTML](https://thomasscottbeck-sudo.github.io/MSBA-Practice-Project-Thomas-Beck-GitHub-Portfolio/04_Team_Model_Polishing.html) |
| **V. Validation** | **05. Model Bake-Off**<br>*(Scientific Selection)* | [View .qmd](./05_Comprehensive_Model_Development.qmd) | [View HTML](https://thomasscottbeck-sudo.github.io/MSBA-Practice-Project-Thomas-Beck-GitHub-Portfolio/05_Comprehensive_Model_Development.html) |
| **VI. Solution** | **06. Final Report**<br>*(The Champion Model)* | [View .qmd](./06_Final_Report_Home_Credit.qmd) | [View HTML](https://thomasscottbeck-sudo.github.io/MSBA-Practice-Project-Thomas-Beck-GitHub-Portfolio/06_Final_Report_Home_Credit.html) |

---

## 3. Technical Architecture & Contributions

I joined the project mid-stream to find a disorganized code base. I assumed the role of **Lead Architect** to refactor the work into a reproducible pipeline.

### **Phase I: Discovery (Hypothesis Testing)**
* **Action:** Conducted an independent "AI vs. Data" audit using ChatGPT to generate semantic predictors (e.g., Income, Gender) and testing them against the data.
* **Finding:** Statistical analysis disproved the "Income" hypothesis. `EXT_SOURCE` scores (external credit bureau proxies) were identified as the dominant signal (Correlation > 0.15), confirming the need for non-linear modeling.

### **Phase II: Experimentation (The Neural Net Failure)**
* **Action:** Built a Python-based Multi-Layer Perceptron (MLP) using `scikit-learn` to test if Deep Learning could extract latent features from the tabular data.
* **Result:** The Neural Net (AUC ~0.56) failed to converge effectively compared to tree-based methods.
* **Strategic Value:** This "negative result" prevented the team from over-engineering the solution, justifying a pivot back to efficient Ensemble Tree methods in R.

### **Phase III: Standardization (The "Fix")**
* **Refactoring:** Converted raw RMarkdown scripts into a unified **Quarto** framework with consistent CSS styling ("Thomas Beck" Palette: Teal/Orange).
* **Optimization:** Implemented `doParallel` backend with dynamic core detection, reducing model training time by **~40%** on standard hardware.
* **Reproducibility:** Enforced the "Golden YAML" standard and `here::here()` relative paths to ensure code runs on any machine without modification.

### **Phase IV: Rigorous Selection (The "Bake-Off")**
I replaced ad-hoc testing with a systematic comparison of four architectures to mathematically justify the final choice:

| Model | AUC | Outcome | Technical Insight |
| :--- | :--- | :--- | :--- |
| **Logistic Regression** | 0.730 | Baseline | Linearity constraint limits performance despite strong predictors. |
| **Decision Tree** | 0.685 | Rejected | High interpretability but high variance; effectively a weak learner. |
| **Random Forest** | 0.651 | Rejected | **Failed due to Bagging limitations.** RF struggles with severe (92:8) class imbalance without heavy synthetic oversampling. |
| **XGBoost** | **0.742** | **Champion** | **Gradient Boosting** sequentially corrected errors on the minority class, capturing the non-linear risk signals others missed. |

---

## 4. Final Solution: The Top-Decile Strategy
The final XGBoost model (File 06) is not just a predictor; it is a decision engine.

* **Strategy:** Automated approval for the bottom 90% of risk scores. Manual review for the top 10%.
* **Business Impact:** This segmentation captures the majority of defaults while reducing manual workload by 90%, directly solving the "Cost vs. Risk" trade-off.

---

## 5. Technical Stack
* **Core:** R (Quarto), Python (Jupyter).
* **Modeling:** `tidymodels`, `xgboost`, `caret`, `scikit-learn`, `ranger`.
* **Data Ops:** `tidyverse`, `here`, `doParallel` (CPU Optimization).