# Hospital Operations & Patient Length-of-Stay Analytics  
*A full end-to-end data analytics and machine learning project for predicting inpatient Length of Stay*

![Project Banner](https://via.placeholder.com/1200x300.png?text=Hospital+LOS+Analytics+Project)

---

## Badges

![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)
![Jupyter](https://img.shields.io/badge/Jupyter-Notebook-orange.svg)
![scikit-learn](https://img.shields.io/badge/scikit--learn-ML-yellow.svg)
![Pandas](https://img.shields.io/badge/Pandas-Data%20Analysis-purple.svg)
![License: MIT](https://img.shields.io/badge/License-MIT-green.svg)

---

## Overview

This project provides an end-to-end analytical workflow for modeling **hospital inpatient Length of Stay (LOS)** using real-world–structured clinical and operational variables. It demonstrates best practices in:

- Data ingestion & cleaning  
- Feature engineering  
- Exploratory data analysis (EDA)  
- Machine learning modeling  
- Hyperparameter tuning  
- Model evaluation  
- Model explainability (SHAP)  
- Reproducible data science project structure  

The objective is to build a **predictive model that estimates the number of days a patient will remain hospitalized**, enabling hospitals to improve:

- Bed capacity planning  
- Resource allocation  
- Discharge management  
- Operational efficiency  

This is a portfolio project designed to showcase applied data analytics and ML skills in a healthcare operations context.

---

## Project Structure

```
Hospital-Operations-Patient-Outcomes-Analytics/
│
├── data/
│   ├── raw/                     
│   └── processed/               
│
├── notebooks/
│   ├── 01_data_cleaning.ipynb   
│   ├── 02_modeling.ipynb        
│   └── 03_explainability.ipynb  
│
├── hospital.venv/               
│
├── requirements.txt             
├── LICENSE
└── README.md                    
```

---

## Project Motivation

Accurately predicting **Length of Stay (LOS)** is a critical task in hospital operations.

Predictive LOS modeling enables proactive management of:

- Overcrowding & admission delays  
- Bed utilization  
- Staffing & resource allocation  
- Patient flow optimization  

This project demonstrates how machine learning can extract meaningful patterns from structured healthcare data to support operational decision-making.

---

## Dataset Summary

The dataset includes **100,000 patient encounters** with **28 variables**, covering:

- Demographics  
- Comorbidities  
- Lab results  
- Vitals  
- Operational information (facility, visit day, readmission count)  
- Target variable: `lengthofstay`

---

## Data Cleaning & Feature Engineering

Key cleaning operations:

- Converted dates to datetime  
- Type correction for numerical variables  
- One-hot encoding for facility indicators  
- Removal of leakage: dropped `discharged` column  
- Feature extraction: weekday + month  

Processed dataset saved in:

```
data/processed/cleaned_hospital_los.csv
```

---

## Machine Learning Modeling

Models implemented:

- Baseline (mean LOS)
- Random Forest Regressor
- Tuned Random Forest (RandomizedSearchCV)

### Train/Test Split
- 80% training (80,000 patients)
- 20% testing (20,000 patients)

### Baseline Results
| Metric | Value |
|--------|-------|
| RMSE | ~2.34 |
| MAE | ~1.90 |

---

## Random Forest Model

### Initial RF Performance
| Metric | Value |
|--------|-------|
| RMSE | ~1.40 |
| MAE | ~0.81 |
| R² | ~0.64 |

---

## Hyperparameter Tuning

Best parameters from RandomizedSearchCV:

```json
{
    "n_estimators": 200,
    "max_depth": 20,
    "min_samples_split": 10,
    "min_samples_leaf": 2,
    "max_features": 0.5
}
```

### Tuned Model Performance
| Metric | Value |
|--------|-------|
| RMSE | ~1.36 |
| MAE | ~0.80 |
| R² | ~0.66 |

---

## Feature Importance

Top predictors:

1. rcount  
2. facility E  
3. hematocrit  
4. glucose  
5. BMI  
6. sodium  
7. creatinine  

---

## SHAP Explainability

SHAP values explain how each feature contributes to individual predictions, increasing model transparency and trustworthiness in clinical contexts.

---

## Installation

### Clone repository
```bash
git clone https://github.com/yfigbio/Hospital-Operations-Patient-Outcomes-Analytics
cd Hospital-Operations-Patient-Outcomes-Analytics
```

### Create virtual environment
```bash
python3 -m venv hospital.venv
source hospital.venv/bin/activate
```

### Install dependencies
```bash
pip install -r requirements.txt
```

---

## License

MIT License.

---

## Author

Created by **Yaiza Anido Figueirido**  
For portfolio, learning, and demonstration of applied healthcare analytics & machine learning.

