# Diabetes-Prediction-Model
# Diabetes Risk Prediction Using Machine Learning

**Author:** Onifade Yemi Mubaraqat

**Role:** Data Scientist

---

# Project Overview

This project develops a machine learning solution for predicting diabetes risk using patient clinical data. The goal is to support early identification of individuals at risk of diabetes, enabling timely intervention and improved healthcare outcomes.

The project follows an end-to-end machine learning workflow, beginning with data preprocessing and exploratory analysis, followed by baseline model development, model optimization, evaluation, and interpretation of results.

### Workflow

* Data Cleaning & Preprocessing
* Exploratory Data Analysis (EDA)
* Baseline Logistic Regression Model
* Model Optimization (StandardScaler + SMOTE + GridSearchCV)
* Model Evaluation
* Model Comparison
* Clinical Interpretation

---

# Business Problem

Diabetes is a chronic disease that affects millions of people worldwide and often remains undiagnosed until complications develop.

Healthcare providers require predictive models that can:

* Identify patients at risk of diabetes
* Support preventive healthcare strategies
* Reduce delayed diagnosis
* Assist clinicians during early screening

The objective of this project is to classify patients as:

* **0 → Non-Diabetic**
* **1 → Diabetic**

---

# Dataset Information

## Dataset Summary

| Attribute       |   Value |
| :-------------- | ------: |
| Total Records   |     768 |
| Total Features  |       8 |
| Target Variable | Outcome |
| Total Columns   |       9 |

---

## Features

* Pregnancies
* Glucose
* Blood Pressure
* Skin Thickness
* Insulin
* BMI
* Diabetes Pedigree Function
* Age

---

## Target Variable

| Value | Meaning      |
| :---: | :----------- |
|   0   | Non-Diabetic |
|   1   | Diabetic     |

---

# Exploratory Data Analysis

Exploratory Data Analysis was performed to understand the distribution of the data and identify important predictors of diabetes.

### Key Findings

* The dataset contains **500 non-diabetic (65.1%)** and **268 diabetic (34.9%)** patients.
* Glucose showed the strongest separation between diabetic and non-diabetic patients.
* BMI and Age also exhibited positive relationships with diabetes.
* Correlation analysis confirmed that Glucose, BMI, and Age were the strongest predictors.

Although the dataset was only moderately imbalanced, techniques to improve minority class detection were explored during model optimization.

---

# Data Preprocessing

Several preprocessing steps were performed before model training.

### Missing Value Treatment

The following variables contained physiologically impossible zero values and were treated as missing:

* Glucose
* Blood Pressure
* Skin Thickness
* Insulin
* BMI

Median imputation was used because it is robust to outliers and preserves the overall distribution of the data.

### Data Splitting

The dataset was divided using an **80:20 train-test split**.

| Dataset  | Size |
| :------- | ---: |
| Training |  614 |
| Testing  |  154 |

Stratified sampling was applied to preserve the class distribution in both datasets.

---

# Machine Learning Models

## Baseline Model

A Logistic Regression model was initially trained using standardized features to establish a benchmark for comparison.

### Baseline Performance

| Metric    |   Score |
| :-------- | ------: |
| Accuracy  | **82%** |
| Precision | **77%** |
| Recall    | **69%** |
| F1-score  | **73%** |

### Baseline Confusion Matrix

|                     | Predicted Healthy | Predicted Diabetic |
| :------------------ | ----------------: | -----------------: |
| **Actual Healthy**  |            **89** |                 11 |
| **Actual Diabetic** |                17 |             **37** |

The baseline model demonstrated strong overall performance but missed 17 diabetic patients, highlighting the need to improve sensitivity.

---

# Model Optimization

To improve the model's ability to detect diabetic patients, several optimization techniques were applied.

### Optimization Techniques

* StandardScaler
* SMOTE (Synthetic Minority Oversampling Technique)
* GridSearchCV
* 5-Fold Cross Validation

GridSearchCV optimized the following Logistic Regression hyperparameters:

* Regularization strength (C)
* Solver
* Penalty

Recall was selected as the optimization metric because minimizing false negatives is particularly important in healthcare screening.

---

# Optimized Model Performance

| Metric    |   Score |
| :-------- | ------: |
| Accuracy  | **80%** |
| Precision | **69%** |
| Recall    | **76%** |
| F1-score  | **73%** |

### Optimized Confusion Matrix

|                     | Predicted Healthy | Predicted Diabetic |
| :------------------ | ----------------: | -----------------: |
| **Actual Healthy**  |            **82** |                 18 |
| **Actual Diabetic** |                13 |             **41** |

The optimized model correctly identified four additional diabetic patients while reducing false negatives from 17 to 13. Although false positives increased slightly, the model became more effective as a diabetes screening tool.

---

# Model Comparison

| Metric    | Baseline | Optimized |
| :-------- | -------: | --------: |
| Accuracy  |  **82%** |       80% |
| Precision |  **77%** |       69% |
| Recall    |      69% |   **76%** |
| F1-score  |      73% |       73% |

### Key Takeaways

* The baseline model achieved the highest overall accuracy.
* The optimized model substantially improved recall.
* False negatives decreased from **17** to **13**.
* The optimized model is more suitable for healthcare screening because it identifies more diabetic patients.

---

# Feature Importance

The Logistic Regression coefficients identified the following variables as the strongest predictors of diabetes:

| Rank | Feature |
| :--: | :------ |
|   1  | Glucose |
|   2  | BMI     |
|   3  | Age     |

These findings align with established clinical evidence that elevated glucose levels, obesity, and increasing age are major risk factors for diabetes.

---

# Conclusion

This project successfully developed and evaluated two Logistic Regression models for diabetes risk prediction.

The baseline model achieved higher overall accuracy, while the optimized model improved recall by reducing the number of missed diabetic patients. Since early detection is critical in healthcare, the optimized model was selected as the preferred model for diabetes screening.

The project demonstrates how preprocessing, feature scaling, class balancing, and hyperparameter tuning can improve machine learning performance while maintaining model interpretability.

---

# Future Improvements

Potential enhancements include:

* Random Forest
* XGBoost
* LightGBM
* Probability Threshold Optimization
* Explainable AI (SHAP)
* Additional clinical variables such as HbA1c and family history
* Streamlit deployment for interactive prediction

---

# Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Scikit-learn
* Imbalanced-learn (SMOTE)
* Jupyter Notebook
* VS Code

---

# License

This project is intended for educational, research, and portfolio purposes.

---

⭐ **If you found this project helpful, consider giving the repository a Star!**
