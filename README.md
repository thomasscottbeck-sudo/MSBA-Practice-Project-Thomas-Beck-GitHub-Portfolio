# Home Credit Default Risk Analysis
**University of Utah | MSBA Practice Project**

**Role:** Lead Data Scientist & System Architect  
**Technical Focus:** Predictive Modeling & Pipeline Engineering  
**Performance:** Champion Model AUC: 0.742  

---

## 1. Executive Summary
This project represents a comprehensive end-to-end data science solution I developed to address **Information Asymmetry** within the consumer lending sector. The objective was to create a robust predictive framework for Home Credit to evaluate the creditworthiness of unbanked populations using alternative data.

**The Analytic Challenge:** I identified a significant **92:8 class imbalance** in the primary dataset. Standard accuracy metrics were discarded as they would fail to mitigate financial risk. 

**The Solution:** I engineered a production-grade pipeline optimized for **Risk Ranking (AUC-ROC)**. My implementation utilizes a "Top Decile" strategy, specifically flagging the riskiest 10% of applicants for manual review. This approach captures the majority of potential defaults while maintaining high-velocity automated approvals for the low-risk majority.

---

## 2. Project Architecture & Development Lifecycle
*I managed the full development lifecycle, from initial exploratory analysis to the final deployment of the champion model.*

| Phase | Module | Logic & Source | Technical Documentation |
| :--- | :--- | :---: | :---: |
| **I. Discovery** | **Individual EDA**<br>*(Hypothesis Validation)* | [View .qmd](./01_ThomasBeck_Individual_EDA.qmd) | [View HTML](https://thomasscottbeck-sudo.github.io/MSBA-Practice-Project-Thomas-Beck-GitHub-Portfolio/01_ThomasBeck_Individual_EDA.html) |
| **II. R&D** | **Deep Learning PoC**<br>*(Python Experimentation)* | [View .ipynb](./02_Individual_PoC_Models.ipynb) | [View HTML](https://thomasscottbeck-sudo.github.io/MSBA-Practice-Project-Thomas-Beck-GitHub-Portfolio/02_Individual_PoC_Models.html) |
| **III. Baseline** | **Legacy Integration**<br>*(Draft Refactoring)* | [View .Rmd](./03_Team_Model_Frankenstein_Draft.Rmd) | [View HTML](https://thomasscottbeck-sudo.github.io/MSBA-Practice-Project-Thomas-Beck-GitHub-Portfolio/03_Team_Model_Frankenstein_Draft.html) |
| **IV. Engineering** | **Pipeline Optimization**<br>*(System Standardization)* | [View .qmd](./04_Team_Model_Polishing.qmd) | [View HTML](https://thomasscottbeck-sudo.github.io/MSBA-Practice-Project-Thomas-Beck-GitHub-Portfolio/04_Team_Model_Polishing.html) |
| **V. Validation** | **Comprehensive Bake-Off**<br>*(Model Selection)* | [View .qmd](./05_Comprehensive_Model_Development.qmd) | [View HTML](https://thomasscottbeck-sudo.github.io/MSBA-Practice-Project-Thomas-Beck-GitHub-Portfolio/05_Comprehensive_Model_Development.html) |
| **VI. Solution** | **The Champion Model**<br>*(Final Deployment)* | [View .qmd](./06_Final_Report_Home_Credit.qmd) | [View HTML](https://thomasscottbeck-sudo.github.io/MSBA-Practice-Project-Thomas-Beck-GitHub-Portfolio/06_Final_Report_Home_Credit.html) |

---

## 3. Core Technical Contributions

I architected the entire repository to serve as a gold-standard example of reproducible data science. While some phases involved legacy inputs from a group setting, I was responsible for the technical auditing, refactoring, and scientific validation of the final product.

### **Strategic Deliverables:**
* **Bilingual Pipeline Execution:** I demonstrated technical versatility by building the primary production pipeline in **R (Quarto/RMarkdown)** while developing specific deep learning proof-of-concepts in **Python (Scikit-Learn/Jupyter)**.
* **System Standardization:** I personally refactored all disparate scripts into a unified **Quarto** framework. I established the primary data dictionary and enforced a consistent visual system (Teal/Orange palette) across all reports.
* **Computational Engineering:** To handle the scale of the data, I implemented multi-core processing using `doParallel`. This optimized the training time for complex ensembles from hours to minutes.
* **Robust Reproducibility:** I eliminated the "it works on my machine" problem by implementing the `here::here()` protocol for all file path management, ensuring the codebase is environment-agnostic.

---

## 4. Engineering Solutions for Complex Challenges

### **Overcoming the "Accuracy Trap"**
In my early modeling phases, I noted that models were defaulting to the majority class. I successfully pivoted the project strategy to focus on **AUC-ROC** and **Precision-Recall curves**. This shift allowed for the successful deployment of Gradient Boosting models that prioritize the detection of high-risk applicants over simple accuracy.

### **Model Refactoring & Performance Tuning**
The "Model Bake-Off" I designed served as a rigorous comparative analysis. I tested a range of architectures—from Logistic Regression and Weighted Decision Trees to Random Forests and XGBoost—to scientifically determine the highest ROI model. My testing confirmed that tree-based boosting provided the most significant lift for this specific business problem.

### **System Stability & Parallelization**
Managing parallel compute tasks often leads to instability during document rendering. I engineered a modular approach to toggle between high-performance training and stable, single-core report knitting, ensuring that the executive-ready HTML outputs remained consistent and error-free.

---

## 5. Professional Insights & Competencies

* **Architecture ROI:** My experimentation (specifically File 02) proved that feature engineering and domain-specific preprocessing yield a higher return on investment than simply increasing model complexity. My linear models often out-performed deep learning architectures when trained on engineered features.
* **Advanced Reporting:** I mastered the **Quarto** framework to produce professional-grade technical documentation. I implemented advanced features including code folding, CSS styling, and tabset layouts to make complex data accessible to non-technical stakeholders.
* **Hardware Lifecycle Management:** I gained deep experience in resource allocation, specifically in detecting logical cores and assigning parallel backends to maximize compute efficiency.

---

## 6. Business Value Delivery

The final XGBoost model (File 06) I developed delivers significant business impact through three primary channels:

1.  **Cost Reduction:** Automates approval for 90% of applicants, allowing human underwriters to focus exclusively on the high-risk "Top Decile."
2.  **Portfolio Protection:** Proactively identifies likely defaults, significantly reducing the capital loss ratio for Home Credit.
3.  **Financial Inclusion:** By utilizing alternative data sources, my model allows Home Credit to responsibly serve a market segment that traditional banking models reject by default.

---

## 7. Technical Stack
* **Primary Tools:** R (Quarto, RMarkdown), Python (Jupyter).
* **Core Libraries:** `tidymodels`, `xgboost`, `caret`, `scikit-learn`, `ranger`.
* **Infrastructure:** `tidyverse`, `here`, `doParallel` (CPU Optimization).
