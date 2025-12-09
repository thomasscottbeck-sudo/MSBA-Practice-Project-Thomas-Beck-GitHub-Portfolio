# Home Credit Default Risk Analysis
**Role:** Integration Lead & Data Scientist  
**Date:** Fall 2025  
**Status:** Complete (Champion Model AUC: 0.742)  

---

## 1. Executive Summary
**The Mission:** Home Credit aims to broaden financial inclusion for unbanked populations by providing positive borrowing experiences. The core challenge is **Information Asymmetry**: predicting repayment capability without traditional credit histories.

**The Analytic Constraint:** Standard accuracy is a misleading metric for this project due to a severe **92:8 class imbalance** (only 8% of applicants default). A naive model predicting "all repay" would be 92% accurate but would fail to mitigate any financial risk.

**The Solution:** This repository documents a production-grade data science pipeline that optimizes for **Risk Ranking (AUC-ROC)**. By identifying "invisible" high-risk applicants, the model enables a "Top Decile" strategy—flagging the riskiest 10% of applicants for manual review, capturing the majority of defaults without slowing down approval for safe borrowers.

---

## 2. Project Dashboard
*Click "Source" to view code logic or "Report" for the rendered executive summary.*

| Phase | Deliverable | Source Code | Executive Report |
| :--- | :--- | :---: | :---: |
| **I. Discovery** | **01. Independent Analysis**<br>*(Hypothesis Validation)* | [View .qmd](./01_ThomasBeck_Individual_EDA.qmd) | [View HTML](https://thomasscottbeck-sudo.github.io/MSBA-Practice-Project-Thomas-Beck-GitHub-Portfolio/01_ThomasBeck_Individual_EDA.html) |
| **II. R&D** | **02. Neural Network PoC**<br>*(Python Experimentation)* | [View .ipynb](./02_Individual_PoC_Models.ipynb) | [View HTML](https://thomasscottbeck-sudo.github.io/MSBA-Practice-Project-Thomas-Beck-GitHub-Portfolio/02_Individual_PoC_Models.html) |
| **III. Baseline** | **03. Team Draft (Legacy)**<br>*(Initial Collaboration)* | [View .Rmd](./03_Team_Model_Frankenstein_Draft.Rmd) | [View HTML](https://thomasscottbeck-sudo.github.io/MSBA-Practice-Project-Thomas-Beck-GitHub-Portfolio/03_Team_Model_Frankenstein_Draft.html) |
| **IV. Engineering** | **04. Pipeline Standardization**<br>*(Refactoring & Speed)* | [View .qmd](./04_Team_Model_Polishing.qmd) | [View HTML](https://thomasscottbeck-sudo.github.io/MSBA-Practice-Project-Thomas-Beck-GitHub-Portfolio/04_Team_Model_Polishing.html) |
| **V. Validation** | **05. Model Bake-Off**<br>*(Scientific Selection)* | [View .qmd](./05_Comprehensive_Model_Development.qmd) | [View HTML](https://thomasscottbeck-sudo.github.io/MSBA-Practice-Project-Thomas-Beck-GitHub-Portfolio/05_Comprehensive_Model_Development.html) |
| **VI. Solution** | **06. Final Report**<br>*(The Champion Model)* | [View .qmd](./06_Final_Report_Home_Credit.qmd) | [View HTML](https://thomasscottbeck-sudo.github.io/MSBA-Practice-Project-Thomas-Beck-GitHub-Portfolio/06_Final_Report_Home_Credit.html) |

---

## 3. My Contributions: Integration & Standardization

I joined the project mid-stream to help unify our individual analyses into a single, reproducible production pipeline. My primary focus was auditing our prior work, refactoring code, and ensuring robust model selection.

### **Key Contributions:**
* **Bilingual Implementation (R & Python):** I demonstrated flexibility across data science ecosystems by managing the main pipeline in **R (Quarto/RMarkdown)** while simultaneously conducting deep learning experiments in **Python (Jupyter/Scikit-Learn)**.
* **Workflow Unification:** I merged disparate scripts into a standardized **Quarto** framework. This ensured consistent visual styling (Teal/Orange palette) and report formatting across the entire project lifecycle.
* **Reproducibility Engineering:** I refactored the codebase to implement robust file paths using `here::here()`, resolving environmental dependencies so the code runs reliably on any machine.
* **Model Comparison Framework:** I designed and executed the "Model Bake-Off" (File 05), a rigorous comparative analysis that scientifically validated our move from Logistic Regression to Gradient Boosting (XGBoost).

---

## 4. Difficulties Encountered

### **1. Integrating Diverse Workflows**
**Challenge:** Our team used a mix of tools (R and Python) and different coding styles (Base R vs. Tidyverse), which made it difficult to combine work into a single document.
**Solution:** I led the standardization effort (File 04), creating a unified data dictionary and standardizing syntax. This allowed us to merge our individual strengths into a single, seamless narrative.

### **2. Parallel Processing Trade-offs**
**Challenge:** Implementing `doParallel` sped up model training significantly, but it introduced instability when knitting the final reports. Race conditions occasionally caused chunks to fail or output disordered logs.
**Solution:** I learned to toggle between multi-core processing for training (speed) and single-core execution for final rendering (stability). This hybrid approach saved hours of compute time while ensuring the final report was error-free.

### **3. The Accuracy Trap**
**Challenge:** Early models showed 92% accuracy but failed to predict defaults. The severe class imbalance masked the model's inability to learn the minority class.
**Solution:** We pivoted entirely to **AUC-ROC** as our north star metric. This forced us to abandon simple decision trees (which prioritized the majority class) in favor of Gradient Boosting, which could be tuned to penalize false negatives more heavily.

---

## 5. What I Learned

* **Professional Notebook Architecture:** I mastered the **Quarto** framework to transform raw code into executive-ready HTML reports. Learning to control code folding, CSS styling, and tabsets was essential for creating a portfolio that looks as good as the code runs.
* **The Power of "Negative Results":** My failed Python Neural Network experiment (File 02) taught me that more complexity doesn't always mean better performance. Documenting this failure was just as valuable as the success of the XGBoost model because it scientifically justified our architectural choices.
* **Compute Optimization:** I gained a deep appreciation for hardware resource management. Learning to detect logical cores and assign parallel backends allowed me to train complex Random Forest ensembles in minutes rather than hours.
* **The "Accuracy Trap":** I learned that 92% accuracy is meaningless when 92% of the classes are the same. Pivoting to **AUC-ROC** shifted our focus to ranking risk rather than just predicting the majority class.
* **Reproducibility Engineering:** I moved beyond "it works on my machine" by implementing robust file paths (using `here::here()`) and standardizing our code environment to ensure anyone could run our analysis.

---

## 6. Business Value of the Solution

Our final XGBoost model (File 06) delivers tangible ROI by solving the "Cost vs. Risk" trade-off:

1.  **Operational Efficiency:** The model allows Home Credit to **automate approval for 90% of applicants** (the "Safe" deciles), drastically reducing manual underwriting costs.
2.  **Risk Mitigation:** By flagging the top 10% of applicants by risk score, the model captures the majority of likely defaults *before* funds are disbursed.
3.  **Financial Inclusion:** The precise risk ranking allows the business to offer tailored products (lower amounts or different terms) to "borderline" applicants who would otherwise be rejected outright.

---

## 7. Technical Stack
* **Languages:** R (Quarto, RMarkdown), Python (Jupyter).
* **Modeling:** `tidymodels`, `xgboost`, `caret`, `scikit-learn`, `ranger`.
* **Data Ops:** `tidyverse`, `here`, `doParallel` (CPU Optimization).
