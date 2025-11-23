# Customer Churn Prediction (XGBoost)

A machine learning project for **binary classification** aiming to detect customer churn in a telecom dataset. The workflow includes preprocessing, model training, handling class imbalance, and hyperparameter tuning using GridSearchCV.

---

## Key Features

* **End-to-End ML Pipeline:** Data cleaning, splitting, training, tuning, and evaluation.
* **Imbalanced Data Handling:** Used `scale_pos_weight` to improve the detection of the minority class (churn customers).
* **Model Optimization:** **Grid Search** was used to find the best hyperparameters for optimal performance.
* **Transparent Results:** Full metrics are reported exactly as achieved—without hiding weaknesses.

---

## Dataset

This project uses the **Telco Customer Churn dataset** from Kaggle.

🔗 [Dataset Link](https://www.kaggle.com/blastchar/telco-customer-churn)

### Details

| Attribute | Value |
| :--- | :--- |
| **Type** | Tabular classification dataset |
| **Target Variable** | **`Churn`** |
| **Classes** | **0:** Not Churn, **1:** Churn |
| **Characteristics** | Includes demographics, contract types, billing information, and service usage. Imbalanced target distribution (more non-churn than churn). |

---

## Tech Stack

* **Language:** Python
* **ML Libraries:** `scikit-learn`, `XGBoost`
* **Visualization:** `Matplotlib`
* **Tools:** `GridSearchCV` for hyperparameter tuning

---

## Project Pipeline

1.  ### Preprocessing
    * Loaded and inspected dataset.
    * Split into training and testing sets.
    * Dropped customer ID.
    * Applied `scale_pos_weight` to counter class imbalance.

2.  ### Baseline Model
    * Initial **XGBoost** model trained with default parameters.
    * Helped establish baseline **recall** and **accuracy**.

3.  ### Hyperparameter Tuning
    * `GridSearchCV` explored combinations of: `learning_rate`, `max_depth`, `colsample_bytree`, `subsample`, `n_estimators`, and `scale_pos_weight`.

#### Best Parameters Found:

```json
{
  "colsample_bytree": 0.8,
  "learning_rate": 0.01,
  "max_depth": 3,
  "n_estimators": 100,
  "scale_pos_weight": 2.766,
  "subsample": 1.0
}
```
* **Best Recall (CV):** $0.8208$

---

## Results

The final tuned model was evaluated on the test set.

### Classification Report

| Class | Precision | Recall | F1-score | Support |
| :---: | :---: | :---: | :---: | :---: |
| **0** | $0.93$ | $0.70$ | $0.80$ | $1036$ |
| **1** | $0.51$ | $0.86$ | $0.64$ | $373$ |

### Overall Metrics

| Metric | Score |
| :--- | :---: |
| **Accuracy** | $0.7409$ |
| **ROC-AUC** | $0.8565$ |
| **Macro F1** | $0.72$ |
| **Weighted F1** | $0.76$ |
