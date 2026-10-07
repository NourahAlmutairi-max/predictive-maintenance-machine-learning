# Predictive Maintenance Using Machine Learning

An end-to-end machine learning project for equipment failure prediction, anomaly detection, explainable AI, and interactive Power BI monitoring.

## Project Overview

This project develops a predictive maintenance workflow using equipment operational data to identify potential machine failures and unusual operating conditions.

The system combines:

- Random Forest for machine failure prediction
- Validation-based classification threshold optimization
- Isolation Forest for anomaly detection
- SHAP for explainable AI
- Power BI for interactive monitoring and visualization

## Dataset

The project uses the AI4I 2020 Predictive Maintenance Dataset containing 10,000 equipment records.

The machine learning model uses five operational features:

- Air Temperature [K]
- Process Temperature [K]
- Rotational Speed [rpm]
- Torque [Nm]
- Tool Wear [min]

Target:

- `0` — Normal operation
- `1` — Machine failure

The dataset is highly imbalanced, with machine failures representing a small minority of the observations.

## Machine Learning Workflow

1. Data inspection and preparation
2. Stratified Train / Validation / Test split
3. Random Forest training with class weighting
4. Classification threshold optimization using the validation set
5. Final evaluation on the held-out test set
6. Isolation Forest anomaly detection
7. SHAP model explainability
8. Power BI data export and visualization

## Model Performance

The final Random Forest model achieved:

| Metric | Result |
|---|---:|
| Accuracy | 97.93% |
| Precision | 70.83% |
| Recall | 66.67% |
| F1 Score | 68.69% |
| PR-AUC | 0.761 |

The optimized classification threshold was **0.30**.

Because the dataset is highly imbalanced, Precision, Recall, F1 Score, and PR-AUC were considered alongside Accuracy.

## Anomaly Detection

Isolation Forest was used to identify unusual equipment operating conditions.

On the test set:

- 318 records were classified as anomalies
- 1,182 records were classified as normal
- Anomaly rate: 21.20%

The observed failure rate was approximately **11.95%** among anomalous records compared with approximately **1.10%** among normal records.

Anomaly detection identifies unusual operating patterns and should not be interpreted as directly predicting or proving the physical cause of failure.

## Explainable AI

SHAP was used to understand how individual operational features influenced the Random Forest predictions.

Global feature importance based on mean absolute SHAP values:

| Feature | Mean Absolute SHAP |
|---|---:|
| Torque [Nm] | 0.1860 |
| Rotational Speed [rpm] | 0.1317 |
| Tool Wear [min] | 0.0977 |
| Air Temperature [K] | 0.0713 |
| Process Temperature [K] | 0.0377 |

SHAP explains the behavior of the machine learning model and does not establish physical causation.

## Technologies

- Python
- Pandas
- NumPy
- Scikit-learn
- Random Forest
- Isolation Forest
- SHAP
- Power BI
- Google Colab

## Dashboard

An interactive Power BI dashboard was developed to visualize:

- Equipment risk levels
- Actual and predicted failures
- Failure probabilities
- Anomaly detection results
- Model evaluation metrics
- SHAP prediction drivers

## Limitations and Future Work

The dataset provides a useful environment for developing and evaluating the machine learning pipeline, but it contains a limited number of failure cases and operational features.

Future work could include larger equipment-specific datasets, additional sensor measurements, time-series data, and further model optimization for real industrial environments.
