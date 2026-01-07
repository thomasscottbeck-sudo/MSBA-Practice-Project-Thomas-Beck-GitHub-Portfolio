# Home Credit: Alternative Data & Risk Analytics
**University of Utah | MSBA Practice Project**

**Author:** Thomas Beck  
**Project Role:** Lead Data Scientist & System Architect  
**Core Technologies:** R (Quarto), Python (Scikit-Learn), XGBoost, Tidymodels  
**Business Impact:** Development of a high-precision risk ranking system to enable financial inclusion for unbanked populations.

---

## 1. The Business Problem: Financial Inclusion vs. Risk
Home Credit is a global lender focused on expand financial inclusion for underserved, unbanked populations. The primary barrier is **Information Asymmetry**: standard credit scoring relies on traditional histories (credit cards, mortgages) that these populations lack. 

**The Objective:** Build a predictive framework that leverages alternative data to identify creditworthy individuals who are typically rejected by legacy banking algorithms.

### **The Strategic Constraint: The "Accuracy Trap"**
A critical discovery in this project was the extreme **92:8 class imbalance** (only 8% of applicants default). 
* **The Problem:** A naive model could predict "No Default" for 100% of applicants and achieve **92% accuracy**, yet it would provide zero business value and expose the company to massive financial risk.
* **The Pivot:** I moved the project's "North Star" metric from accuracy to **AUC-ROC** and **Precision-Recall**. This forced the models to prioritize the *ranking* of risk rather than simple classification, allowing the business to capture defaults in the "Top Decile" of risky scores.

---

## 2. Integrated Research & Development Lifecycle
I architected this repository to demonstrate the full lifecycle of a data science product—from raw hypothesis testing to a production-ready ensemble model.

| Phase | Milestone | Methodology | Technical Documentation |
| :--- | :--- | :--- | :---: |
| **I. Discovery** | **Exploratory Data Analysis** | Identifying signals in "External Source" features and demographic noise. | [View Report](https://thomasscottbeck-sudo.github.io/MSBA-Practice-Project-Thomas-Beck-GitHub-Portfolio/01_ThomasBeck_Individual_EDA.html) |
| **II. R&D** | **Deep Learning PoC** | Prototyping Neural Networks in Python to test non-linear complexity. | [View Report](https://thomasscottbeck-sudo.github.io/MSBA-Practice-Project-Thomas-Beck-GitHub-Portfolio/02_Individual_PoC_Models.html) |
| **III. Baseline** | **Legacy Refactoring** | Standardizing disparate logic into a clean, reproducible framework. | [View Report](https://thomasscottbeck-sudo.github.io/MSBA-Practice-Project-Thomas-Beck-GitHub-Portfolio/03_Team_Model_Frankenstein_Draft.html) |
| **IV. Validation** | **The Model Bake-Off** | Rigorous head-to-head testing: Logit vs. Random Forest vs. XGBoost. | [View Report](https://thomasscottbeck-sudo.github.io/MSBA-Practice-Project-Thomas-Beck-GitHub-Portfolio/05_Comprehensive_Model_Development.html) |
| **V. Solution** | **The Champion Model** | Deployment of the final XGBoost pipeline with optimized hyperparameters. | [View Report](https://thomasscottbeck-sudo.github.io/MSBA-Practice-Project-Thomas-Beck-GitHub-Portfolio/06_Final_Report_Home_Credit.html) |

---

## 3. Engineering & Decision Logic
A recruiter or hiring manager can look at my work to see the following professional competencies:

### **Critical Reasoning: Feature ROI vs. Complexity**
My experiments (specifically File 02) proved that for tabular financial data, **Feature Engineering** provides a higher ROI than model complexity. I found that simpler models with engineered features often outperformed raw Deep Learning architectures, leading to the selection of a Gradient Boosting (XGBoost) approach for final deployment.

### **Technical Versatility (Bilingual Stack)**
This portfolio demonstrates my ability to work across ecosystems. I utilized **R (Tidymodels/Quarto)** for robust statistical reporting and pipeline management, while leveraging **Python (Jupyter/Scikit-Learn)** for algorithmic prototyping.

### **Production-Grade Reproducibility**
I eliminated the "environment dependency" problem by:
* Implementing the `here::here()` protocol for absolute file pathing.
* Utilizing `doParallel` to optimize compute resources, reducing model training time by 400%.
* Standardizing a "Golden YAML" format for all Quarto outputs to ensure executive-ready HTML/PDF reporting.

---

## 4. Key Performance Insights
The final **Champion Model (XGBoost)** delivers tangible value by solving the "Cost vs. Risk" trade-off:

1.  **Automation:** The model enables **Automated Approval for ~90% of applicants** (the safe deciles).
2.  **Risk Mitigation:** The "Top Decile" strategy flags the highest-risk 10% of applicants, which historically contains over 50% of the total defaults.
3.  **Financial Growth:** By moving beyond traditional credit scores, Home Credit can safely expand its loan book into new, underserved market segments.

---

## 5. Technical Stack Summary
* **Languages:** R, Python, SQL
* **Environment:** Quarto (Advanced Reporting), Jupyter, VS Code
* **Modeling:** `xgboost`, `tidymodels`, `caret`, `scikit-learn`, `ranger`
* **Ops:** `doParallel` (CPU Optimization), `tidyverse`, `here` (Reproducibility)
