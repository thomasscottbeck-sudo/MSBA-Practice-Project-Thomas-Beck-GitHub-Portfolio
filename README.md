# Home Credit Default Risk Analysis: The "Turnaround" Strategy

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

## 3. The Technical Narrative: From "Messy" to "Masterpiece"

I joined the project mid-stream to help unify our individual analyses into a single, reproducible production pipeline. This meant auditing our prior work and refactoring the code to ensure it was robust enough for deployment.

### **Phase I: The Hypothesis Audit (File 01)**
My first step was to audit our assumptions. I formulated a specific set of guiding questions to test "Human Intuition" against "Statistical Reality."
* **The Finding:** Common sense was often wrong. While the AI assistant predicted that **Income** would be a primary driver, the statistical evidence (Correlations and Density Plots) proved it was a weak predictor. The real signal came from **External Sources** (credit bureau proxies) and **Employment Stability**. This pivoted our entire feature engineering strategy.

### **Phase II: The "Negative Result" (File 02)**
To test the limits of our data, I built a Python-based **Neural Network (MLP)**. The hypothesis was that deep learning might extract latent features that linear models missed.
* **The Outcome:** It failed (AUC ~0.56). The data was too noisy for a neural net to converge effectively.
* **The Value:** This failure was a crucial strategic win. It stopped us from over-engineering the solution and justified our decision to double down on **Tree-Based Ensembles (XGBoost)** in R.

### **Phase III: The "Fix" (File 04)**
Inheriting the team's initial draft (File 03), I faced a "Frankenstein" code base with mixed syntax and absolute file paths.
* **Engineering:** I implemented the `here` package to make paths relative (solving the "it works on my machine" bug) and added `doParallel` to enable multi-core processing, cutting our training time by **40%**.

### **Phase IV: The Scientific Selection (File 05)**
We moved beyond "trying things" to a rigorous tournament of four algorithms:
* **Logistic Regression:** Good baseline (AUC 0.73) but failed to capture non-linear risk factors.
* **Random Forest:** Failed (AUC 0.65). It struggled with the 92:8 class imbalance because Bagging averages out the minority signal.
* **XGBoost (The Winner):** Champion (AUC 0.74). Boosting sequentially corrected errors on the minority class, effectively "hunting" the defaults that other models missed.

---

## 4. Difficulties Encountered

### **1. The "Frankenstein" Codebase**
**Challenge:** Inheriting a project in mid-flight meant dealing with conflicting variable names, hard-coded file paths (e.g., `C:/Users/Name...`), and mixed coding styles (Base R vs. Tidyverse).
**Solution:** I led the standardization effort, creating a unified data dictionary and implementing a consistent coding standard. This turned a collection of scripts into a cohesive software product.

### **2. Parallel Processing vs. Reproducibility**
**Challenge:** While implementing `doParallel` sped up our Random Forest training, it introduced instability when knitting the final reports. Race conditions occasionally caused chunks to fail or output disordered logs.
**Solution:** I learned to toggle between multi-core processing for training (speed) and single-core execution for final rendering (stability). This hybrid approach saved hours of compute time while ensuring the final report was error-free.

### **3. The Accuracy Trap**
**Challenge:** Our early Decision Trees showed 92% accuracy but failed to predict a single default. The severe class imbalance masked the model's inability to learn the minority class.
**Solution:** We pivoted entirely to **AUC-ROC** as our north star metric. This forced us to abandon models that prioritized the majority class in favor of Gradient Boosting, which could be tuned to penalize false negatives more heavily.

---

## 5. What I Learned

* **Professional Notebook Architecture:** I mastered the **Quarto** framework to transform raw code into executive-ready HTML reports. Learning to control code folding, CSS styling, and tabsets was essential for creating a portfolio that looks as good as the code runs.
* **The Power of "Negative Results":** My failed Python Neural Network experiment (File 02) taught me that more complexity doesn't always mean better performance. Documenting this failure was just as valuable as the success of the XGBoost model because it scientifically justified our architectural choices.
* **Compute Optimization:** I
