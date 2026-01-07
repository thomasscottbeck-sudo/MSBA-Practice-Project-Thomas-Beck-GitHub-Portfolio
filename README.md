# Home Credit Default Risk Analysis
**University of Utah | MSBA Practice Project**

**Role:** Integration Lead & Data Scientist  
**Scope:** End-to-End Predictive Pipeline  
**Status:** Production Ready (Champion Model AUC: 0.742)  

---

## 1. Executive Summary
The primary objective of this project is to solve the problem of **Information Asymmetry** for Home Credit. Many potential borrowers lack traditional credit histories, leading to financial exclusion. This project develops a robust predictive framework to evaluate repayment capability using alternative data sources.

**The Analytic Constraint:** Standard accuracy is a deceptive metric in this context due to a **92:8 class imbalance** (only 8% default rate). A baseline model predicting "no default" for every applicant achieves 92% accuracy while providing zero business value. 

**The Solution:** This repository documents a production-grade data science pipeline optimized for **Risk Ranking (AUC-ROC)**. By implementing a "Top Decile" strategy, the model identifies the riskiest 10% of applicants for manual underwriting, capturing the majority of potential defaults without impeding the automated approval process for creditworthy borrowers.

---

## 2. Project Dashboard
*A comprehensive lifecycle of the analysis, from discovery to the final champion model.*

| Phase | Deliverable | Source Code | Executive Report |
| :--- | :--- | :---: | :---: |
| **I. Discovery** | **01. Independent Analysis**<br>*(Hypothesis Validation)* | [View .qmd](./01_ThomasBeck_Individual_EDA.qmd) | [View HTML](https://thomasscottbeck-sudo.github.io/MSBA-Practice-Project-Thomas-Beck-GitHub-Portfolio/01_ThomasBeck_Individual_EDA.html) |
| **II. R&D** | **02. Neural Network PoC**<br>*(Python Experimentation)* | [View .ipynb](./02_Individual_PoC_Models.ipynb) | [View HTML](https://thomasscottbeck-sudo.github.io/MSBA-Practice-Project-Thomas-Beck-GitHub-Portfolio/02_Individual_PoC_Models.html) |
| **III. Baseline** | **03. Team Draft (Legacy)**<br>*(Initial Collaboration)* | [View .Rmd](./03_Team_Model_Frankenstein_Draft.Rmd) | [View HTML](https://thomasscottbeck-sudo.github.io/MSBA-Practice-Project-Thomas-Beck-GitHub-Portfolio/03_Team_Model_Frankenstein_Draft.html) |
| **IV. Engineering** | **04. Pipeline Standardization**<br>*(Refactoring & Speed)* | [View .qmd](./04_Team_Model_Polishing.qmd) | [View HTML](https://thomasscottbeck-sudo.github.io/MSBA-Practice-Project-Thomas-Beck-GitHub-Portfolio/04_Team_Model_Polishing.html) |
| **V. Validation** | **05. Model Bake-Off**<br>*(Scientific Selection)* | [View .qmd](./05_Comprehensive_Model_Development.qmd) | [View HTML](https://thomasscottbeck-sudo.github.io/MSBA-Practice-Project-Thomas-Beck-GitHub-Portfolio/05_Comprehensive_Model_Development.html) |
| **VI. Solution** | **06. Final Report**<br>*(The Champion Model)* | [View .qmd](./06_Final_Report_Home_Credit.qmd) | [View HTML](https://thomasscottbeck-sudo.github.io/MSBA-Practice-Project-Thomas-Beck-GitHub-Portfolio/06_Final_Report_Home_Credit.html) |

---

## 3. Professional Contributions: Systems Integration

I spearheaded the integration of disparate analyses into a unified, reproducible production pipeline. My focus was on technical auditing, code refactoring, and establishing a rigorous model selection framework within the MSBA program curriculum.

### **Core Competencies Demonstrated:**
* **Cross-Functional Implementation:** Managed a bilingual pipeline, utilizing **R (Quarto)** for the primary production environment and **Python (Scikit-Learn)** for deep learning experimentation.
* **Workflow Standardization:** Unified heterogeneous coding styles into a standardized Quarto framework, ensuring consistent visual aesthetics and data dictionaries across all project phases.
* **Reproducibility Engineering:** Eliminated environmental dependencies by implementing the `here::here()` protocol for robust file path management.
* **Scientific Model Validation:** Engineered a "Model Bake-Off" framework to objectively compare performance across Logistic Regression, Random Forests, and Gradient Boosting (XGBoost).

---

## 4. Engineering Challenges & Strategic Solutions

### **Metric Optimization (The Accuracy Trap)**
* **Challenge:** Initial models yielded high accuracy (92%) but failed to distinguish between default and non-default cases due to class imbalance.
* **Solution:** Pivoted the evaluation metric to **AUC-ROC**. This strategic shift moved the project away from simplistic decision trees toward Gradient Boosting, which allows for finer tuning of the probability threshold to minimize false negatives.

### **Computational Resource Management**
* **Challenge:** Training complex ensemble models introduced high latency and potential instability during the document knitting process.
* **Solution:** Integrated `doParallel` for multi-core processing. I developed a hybrid execution strategy: utilizing parallel backends for intensive training and switching to single-core execution for stable report rendering.

### **Codebase Unification**
* **Challenge:** Merging diverse technical approaches (Base R vs. Tidyverse) from multiple contributors into a coherent narrative.
* **Solution:** Led a refactoring effort to standardize syntax and visual formatting, resulting in a professional, "executive-ready" document suite.

---

## 5. Technical Insights

* **Model Architecture vs. Feature ROI:** Testing algorithms ranging from linear baselines to Deep Learning (Neural Networks) revealed that for tabular financial data, feature engineering and ensemble tree methods (XGBoost) consistently outperformed more complex neural architectures.
* **Advanced Notebook Architecture:** Leveraged the Quarto framework to implement professional features such as code folding, custom CSS, and interactive tabsets, ensuring the analysis is accessible to both technical and executive stakeholders.
* **Hardware Optimization:** Gained expertise in logical core detection and parallel backend assignment, reducing model training cycles from hours to minutes.

---

## 6. Business Value & ROI

The final XGBoost solution provides a data-driven path to optimizing the "Cost vs. Risk" trade-off:

1.  **Operational Scalability:** Enables the automation of approvals for 90% of applicants, significantly reducing manual underwriting overhead.
2.  **Strategic Risk Mitigation:** Identifies high-risk segments prior to disbursement, protecting the portfolio from significant capital loss.
3.  **Expanded Market Reach:** Precise risk ranking allows Home Credit to extend credit to underserved but creditworthy individuals by substituting traditional history with predictive alternative data.

---

## 7. Technical Stack
* **Languages:** R (Quarto, RMarkdown), Python (Jupyter).
* **Modeling Frameworks:** `tidymodels`, `xgboost`, `caret`, `scikit-learn`, `ranger`.
* **Utilities:** `tidyverse`, `here`, `doParallel` (CPU Optimization).
