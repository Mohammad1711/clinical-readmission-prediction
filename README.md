
# Predicting 30-Day Hospital Readmission in Patients with Diabetes

## Overview

This clinical data science project explores whether routinely collected clinical and hospitalization data can help identify patients with diabetes who are at increased risk of hospital readmission within 30 days.

The project combines exploratory data analysis, clinical cohort refinement, preprocessing, and machine learning.

## Research Question

**Can routinely collected clinical and hospitalization data identify patients with diabetes who are at increased risk of hospital readmission within 30 days?**

## Dataset

The analysis uses the **Diabetes 130-US Hospitals for Years 1999–2008** dataset from the UCI Machine Learning Repository.

The original dataset contains:

- 101,766 hospital encounters
- 50 original variables
- Data from 130 U.S. hospitals
- Demographic, diagnostic, medication, laboratory, and healthcare-utilization information

## Final Analytical Cohort

After clinical review of discharge-disposition codes, 1,652 death-related encounters were excluded because these patients were not eligible for subsequent 30-day readmission.

The final analytical cohort contained:

- **100,114 hospital encounters**
- **11.34% 30-day readmission rate**

## Exploratory Finding

Previous inpatient utilization showed a strong descriptive association with 30-day readmission.

Observed readmission increased from:

- **8.44%** with no previous inpatient visits
- **12.92%** with one previous inpatient visit
- **17.43%** with two previous inpatient visits
- **20.29%** with three previous inpatient visits
- **23.61%** with four previous inpatient visits
- **36.41%** with five or more previous inpatient visits

These findings represent associations and should not be interpreted as causal effects.

## Predictive Models

Three approaches were evaluated:

1. Majority-class baseline
2. Logistic Regression
3. Random Forest

An 80/20 stratified train-test split was used.

## Final Results

| Model | Accuracy | Precision | Recall | F1-score | ROC-AUC |
|---|---:|---:|---:|---:|---:|
| Majority Baseline | 0.8866 | 0.0000 | 0.0000 | 0.0000 | 0.5000 |
| Logistic Regression | 0.6491 | 0.1701 | 0.5399 | 0.2587 | 0.6404 |
| Random Forest | 0.6197 | 0.1677 | 0.5936 | 0.2615 | 0.6481 |

Random Forest achieved the highest recall (**59.36%**) and ROC-AUC (**0.648**).

However, precision remained low, and the models should not be considered suitable for clinical deployment.

## Clinical Data Science Insight

During model interpretation, `discharge_disposition_id` emerged as an influential feature.

Review of the data dictionary revealed that the original cohort included patients who had died and therefore could not subsequently be readmitted.

These encounters were excluded and the entire modeling pipeline was retrained.

This illustrates the importance of combining **clinical reasoning with data science**, rather than evaluating predictive performance alone.

## Limitations

- Retrospective observational data
- Data collected between 1999 and 2008
- Encounter-level rather than patient-level train-test split
- Multiple encounters from the same patient may occur across train and test sets
- Class imbalance
- No external validation
- No clinical threshold optimization
- Predictive associations do not establish causality

## Next Steps

Future work could include:

- Patient-level train-test splitting
- Cross-validation
- Clinical feature engineering
- Threshold optimization
- Calibration analysis
- External validation

## Tools

Python | Pandas | NumPy | Matplotlib | Scikit-learn | Jupyter Notebook

## Disclaimer

This project is an educational and exploratory clinical data science analysis.

The models are **not intended for clinical decision-making or patient care**.
