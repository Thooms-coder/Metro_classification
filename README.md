# Predicting Metropolitan Status from Structural Cost Shares Using Machine Learning

This repository contains the full implementation, analysis, and research paper for a machine learning study investigating whether U.S. county metropolitan status can be predicted solely from structural household expenditure shares and minimal demographic indicators. The research demonstrates that cost-share compositions encode strong geographic and socioeconomic signals, enabling accurate metro classification even when explicit geographic identifiers are missing.

---

## Project Overview

The central research question is:

**Can structural cost-share patterns alone reliably classify counties as metropolitan or non-metropolitan?**

To answer this, the project uses normalized expenditure shares for:
- Housing  
- Transportation  
- Healthcare  
- Food  
- Childcare  
- Taxes  
- Other necessities  

Along with:
- SNAP participation rate  
- Family type  
- State abbreviation  

A complete machine-learning pipeline was constructed, including:
- Feature normalization and engineering  
- Imputation, scaling, and one-hot encoding using a unified preprocessing pipeline  
- SMOTE oversampling for class balance  
- PCA for structural dimensionality analysis  
- Comparative evaluation of six classifiers  
- Aggregated feature importance across model families  

The best-performing model, a Neural Network (MLP), achieved:

- **Test ROC AUC:** 0.9528  
- **Test Weighted F1 Score:** 0.8864  

These results confirm that cost-share structures alone provide a strong and interpretable signal of metropolitan economic conditions.

---

## Repository Structure

📁 project-folder
│
├── 📄 metro_classification.ipynb
│      └─ Full analysis: EDA, PCA, modeling pipeline, evaluation
│
├── 📄 metro_status_paper.pdf
│      └─ Final IEEE-style research paper
│
├── 📄 README.md
│      └─ Project overview and documentation
│
└── 📁 data
       └── data.csv   # County-level cost-share and demographic dataset


---

## Methods Summary

### Preprocessing Pipeline
A unified preprocessing pipeline was implemented using:

- Median imputation for numeric variables  
- Standardization via `StandardScaler`  
- Most-frequent imputation for categorical variables  
- One-hot encoding with `handle_unknown='ignore'`  

This ensures consistent, leakage-free transformations across all models.

### Models Evaluated
A diverse set of classifiers was compared:

- Logistic Regression  
- Decision Tree  
- Random Forest  
- Gradient Boosting  
- Support Vector Classifier  
- Neural Network (MLP)  

### Handling Class Imbalance  
SMOTE oversampling was applied inside an `ImbPipeline` to ensure oversampling occurred only on training folds, preserving the integrity of validation and test sets.

### Evaluation Metrics  
The models were compared using:

- ROC AUC (primary metric)  
- Weighted F1 score  
- Confusion matrix  
- Balanced vs. unbalanced performance comparison  
- Combined feature importance across three model families  

---

## Key Findings

- Structural expenditure shares convey rich socioeconomic information that aligns closely with metro–non-metro distinctions.
- Housing and other-necessities shares were the strongest positive predictors of metro status.
- Transportation and healthcare shares were the strongest negative predictors.
- PCA revealed clear clustering structure aligned with metropolitan status, despite no geographic inputs.
- Neural Networks provided the most accurate and generalizable decision boundary across nonlinear feature interactions.
- The final test performance confirms strong predictive capability in unseen county data.

---

## How to Use This Repository

### 1. Open the Notebook
Run the complete analysis using:

metro_classification.ipynb


It includes:

- Data loading  
- Feature engineering  
- Exploratory data analysis  
- PCA projection  
- Model training and validation  
- SMOTE balancing  
- Final model evaluation  
- Confusion matrix and ROC curve  

### 2. View the Research Paper
The camera-ready IEEE-style report is available here:

metro_status_paper.pdf


This document contains full methodological detail, figures, analysis, interpretation, discussion, and references.

---

## Citation

If you use or reference this project, please cite:

M. J. Mungoshi, "Predicting Metropolitan Status from Structural Cost Shares Using Machine Learning,"
Clarkson University, 2025.


---

## Author

**Mutsa Jonah Mungoshi**  
Applied Data Science  
Clarkson University  
Email: mungosmj@clarkson.edu
