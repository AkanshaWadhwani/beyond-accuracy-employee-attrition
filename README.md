# Beyond Accuracy: A Robustness Study of Employee Attrition Prediction

## Overview

Machine learning models are often evaluated on clean, carefully prepared datasets. However, real-world organizational data is rarely perfect. Employee records may contain missing values, inaccurate entries, and unusual observations that can affect model reliability.

This project investigates how common data quality issues influence employee attrition prediction. Instead of focusing solely on predictive accuracy, the study evaluates how robust machine learning models remain when data quality deteriorates.

The project compares Logistic Regression and Random Forest under controlled degradation scenarios involving missing values, noise, and outliers.

---

## Research Questions

* Which type of data quality issue causes the greatest performance degradation?
* Which machine learning model is most robust under degraded conditions?
* Which employee attributes contribute most strongly to attrition prediction?
* How does predictive reliability change as data corruption increases?

---

## Dataset

**IBM HR Analytics Employee Attrition Dataset**

### Target Variable

* Attrition (Yes / No)

### Features

The dataset contains demographic, compensation, career progression, and workplace-related variables, including:

* Age
* Monthly Income
* Total Working Years
* Job Role
* Overtime
* Distance From Home
* Job Satisfaction
* Years at Company
* Work-Life Balance

---

## Methodology

### 1. Data Preprocessing

* Removed irrelevant identifiers
* Handled missing values using median imputation
* Encoded categorical variables
* Standardized numerical features
* Performed train-test split

### 2. Baseline Models

Two classification algorithms were trained on clean data:

* Logistic Regression
* Random Forest

### 3. Data Degradation Experiments

Three controlled degradation scenarios were implemented:

#### Missing Value Injection

Randomly introduced missing values into employee records.

#### Noise Injection

Added Gaussian noise to numerical variables to simulate inaccurate measurements and data-entry errors.

#### Outlier Injection

Introduced extreme values to simulate anomalous employee records.

### 4. Robustness Evaluation

Models were trained on clean data and evaluated on degraded test data.

Each experiment was repeated across multiple random seeds to improve result reliability.

---

## Evaluation Metrics

* Accuracy
* Precision
* Recall
* F1 Score
* ROC-AUC
* Robustness Score

### Robustness Score

Robustness Score = Average Corrupted AUC / Baseline AUC

Higher values indicate greater resistance to data quality degradation.

---

## Key Findings

### Missing Data

* Produced minimal degradation after median imputation.
* Both models remained relatively stable.
* Random Forest demonstrated slightly higher robustness.

### Noise

* Caused moderate reductions in predictive performance.
* Tree-based models showed stronger resilience to noisy inputs.

### Outliers

* Produced the largest performance decline.
* Logistic Regression was particularly sensitive to extreme values.
* Random Forest remained substantially more robust.

---

## Robustness Analysis

| Degradation Type | Most Robust Model | Robustness Score |
| ---------------- | ----------------- | ---------------- |
| Missing Data     | Random Forest     | 0.9817           |
| Noise            | Random Forest     | 0.9706           |
| Outliers         | Random Forest     | 0.9418           |

### Main Insight

Random Forest consistently preserved a larger proportion of its original predictive performance under degraded data conditions.

Outliers emerged as the most harmful form of corruption, especially for Logistic Regression.

---

## Feature Importance

The most influential predictors identified by Random Forest were:

1. MonthlyIncome
2. Age
3. TotalWorkingYears
4. YearsAtCompany
5. OverTime

These findings suggest that compensation, experience, and workload-related factors play an important role in employee attrition prediction.

---

## Real-World Implications

Employee attrition prediction models are increasingly used to support workforce planning and employee retention strategies.

This study demonstrates that model performance depends not only on the choice of algorithm but also on the quality of the underlying data. Missing values, noisy records, and outliers can reduce predictive reliability, particularly when models are deployed on real-world organizational data.

The findings suggest that organizations should monitor data quality alongside model performance and ensure that preprocessing pipelines are robust to common data issues.

Ultimately, a highly accurate model trained on clean historical data may not perform as expected when deployed on imperfect operational datasets.


---

## Technologies Used

* Python
* NumPy
* Pandas
* Scikit-learn
* Matplotlib
* Seaborn
* Jupyter Notebook

---

## Future Work

Potential extensions include:

* Feature-specific corruption analysis
* XGBoost and LightGBM comparison
* SHAP-based explainability analysis
* Investigation of real-world missingness patterns
* Fairness and bias analysis in HR AI systems

---

## Author

Author

Akansha Wadhwani

First-Year AIML Student (Completed)
Symbiosis Institute of Technology, Pune

Exploring Machine Learning and Data Science through hands-on projects and experimentation.
