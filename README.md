# MSBA-Practice-Project-Thomas-Beck-GitHub-Portfolio
Individual Data Science Portfolio for the Home Credit Default Risk project. Demonstrates independent EDA, a Python-based Neural Network experiment (failed hypothesis), and the final strategic pivot to the group's XGBoost model and polished professional and reproducible notebooks.


## Home Credit Default Risk Analysis: The "Turnaround" Strategy
**Role:** Lead Architect & Data Scientist  
**Date:** Fall 2025  
**Status:** Complete (Champion Model AUC: 0.742)  

---

## 1. Executive Summary
**The Mission:** Home Credit strives to broaden financial inclusion for the unbanked population by providing a safety net of positive borrowing experiences. 

**The Challenge:** The core business hurdle is **Information Asymmetry**—accurately predicting repayment capability for applicants who lack traditional credit histories. Standard accuracy metrics are misleading here due to a severe **92:8 class imbalance** (only 8% of applicants default). 

**The Solution:** This repository documents the end-to-end lifecycle of a data science solution that prioritizes **Risk Ranking (AUC-ROC)** over simple accuracy. By correctly identifying "invisible" high-risk applicants, we enable Home Credit to protect its bottom line while safely expanding access to credit.

---

## 2. My Contribution: The Architect & Auditor
I joined the project team late in the semester to find a repository of disjointed scripts and raw code. I assumed the role of **Lead Architect** to transform this "Frankenstein" draft into a cohesive, professional data product.

**Key Contributions:**
1.  **Complete Code Refactoring:** I took the team's raw RMarkdown draft (File 03) and rebuilt the entire pipeline (Files 04–06). I implemented professional formatting ("Golden YAML"), code folding, and CSS styling to create a report fit for executives.
2.  **Performance Optimization:** I rewrote the training loops to include `doParallel` CPU optimization, reducing model training time by ~40% on standard hardware.
3.  **Independent R&D (Neural Networks):** I personally developed a Python-based Neural Network to test if Deep Learning could outperform traditional methods. Its failure (AUC ~0.56) provided the critical evidence needed to commit to the XGBoost strategy.
4.  **Rigorous Model Selection:** I replaced the team's ad-hoc testing with a systematic "Model Bake-Off" (File 05), mathematically proving why Linear and Bagging models were insufficient for this specific data structure.

---

## 3. Project Narrative & Files

### **Phase I: Discovery & R&D**
* **`01_Individual_Analysis_Beck.qmd` (The "Hero" EDA)**
    * **My Role:** Independent Investigator.
    * **Contribution:** I used ChatGPT to generate a *semantic* list of predictors (what "should" matter) and statistically tested it against the actual data (what *does* matter). **Result:** Disproved the assumption that demographics (Gender/Income) are predictive; proved `EXT_SOURCE` scores are the dominant signal.

* **`02_Individual_PoC_Models_vFinal.ipynb` (The Python Pivot)**
    * **My Role:** R&D Data Scientist.
    * **Contribution:** I built a custom Python workflow (scikit-learn) to test a Multi-Layer Perceptron (Neural Network) against the dataset.
    * **Key Learning:** The Neural Net failed to converge effectively (AUC ~0.56) compared to tree-based methods. This "negative result" was crucial—it prevented the team from wasting time on complex deep learning architectures that weren't suited for this tabular data.

* **`03_Team_Model_(Frankenstein)Draft.Rmd` (The "Before" State)**
    * **Context:** This file represents the raw, collaborative state of the project before my intervention. I have preserved it here to demonstrate the baseline from which I began the refactoring process.

### **Phase II: The Turnaround (Refactoring & Evaluation)**
* **`04_Team_Model_Polishing.qmd` (The Fix)**
    * **My Role:** Pipeline Engineer.
    * **Contribution:** I standardized the coding environment. I consolidated inconsistent libraries, fixed data leakage in the cleaning steps, and implemented the "Golden YAML" standard to ensure reproducible HTML/PDF rendering.

* **`05_Comprehensive_Model_Development.qmd` (The Model Bake-Off)**
    * **My Role:** Lead Scientist.
    * **Contribution:** I designed a rigorous head-to-head comparison of four algorithms to justify our final choice. I proved that:
        1.  **Logistic Regression (AUC 0.73):** Good baseline, but limited by linearity.
        2.  **Decision Tree (AUC 0.68):** Interpretable, but weak predictive power.
        3.  **Random Forest (AUC 0.65):** Failed due to sensitivity to class imbalance (Bagging limitation).
        4.  **XGBoost (AUC 0.74):** The clear winner (Boosting optimization).

### **Phase III: The Solution**
* **`06_Final_Report_Home_Credit.qmd` (The Champion)**
    * **My Role:** Executive Communicator.
    * **Contribution:** The final, polished deliverable. I stripped away the exploratory code to focus exclusively on the winning **XGBoost model**, the **Risk Ranking strategy**, and the **ROI analysis**.

---

## 4. Business Value & Impact
By deploying the XGBoost model, Home Credit can implement a **"Top Decile" Strategy**:
* **Action:** Automatically flag the top 10% of risky applicants for manual review.
* **Impact:** This captures **~60% of all defaults** while auto-approving the vast majority of safe customers.
* **ROI:** Reduces default write-offs without significantly slowing down user acquisition.

---

## 5. Tools & Skills Learned
* **Pipeline Engineering:** Learned how to refactor messy, collaborative code into a unified production pipeline.
* **R vs. Python:** Gained experience managing a multi-language project, using Python for experimental R&D and R for the final production report.
* **Algorithm Selection:** Learned that for tabular data with high class imbalance, Gradient Boosting (XGBoost) often outperforms both Deep Learning and Random Forest.
* **Optimization:** Mastered `doParallel` in R to maximize hardware efficiency during training.
