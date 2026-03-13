# DriveScore: Insurance Premium Prediction from Telematics Data

> A supervised machine learning pipeline that predicts insurance premiums from driving behavior signals — demonstrating the core engine behind Usage-Based Insurance (UBI).

---

##  Project Overview

Traditional insurance pricing relies on static factors like age, location, and vehicle type. **DriveScore** simulates how modern insurers use **telematics data** — real-time signals from in-car sensors and mobile apps — to price risk more accurately and fairly.

This project covers the full data science workflow: synthetic data generation, exploratory analysis, feature engineering, model training, evaluation, and business interpretation.

---

##  Repository Structure

```
drivescore/
│
├── DriveScore_Insurance_Premium_Prediction.ipynb                       
├── telematics_data.csv                            # Synthetic dataset (5,000 policies)
├── DriveScore_Presentation.pptx                  
└── README.md
```

---

## Dataset

The dataset is synthetically generated using a domain-informed formula that mirrors real-world telematics insurance pricing logic.

| Category | Features |
|---|---|
| **Driver Profile** | Age, years licensed, vehicle type, vehicle age, prior claims |
| **Telematics Signals** | Avg speed, hard braking/trip, sharp cornering/trip, phone use/trip, % night driving, % speeding, % highway driving, trips/week, annual mileage |
| **Engineered Features** | Driving risk score, mileage per trip, experience ratio, age group |
| **Target** | Annual insurance premium ($400 – $3,290) |

- **Records:** 5,000 policies
- **Mean premium:** $1,528
- **Train/test split:** 80/20

---

## Pipeline

```
Data Generation → EDA → Feature Engineering → Model Training → Evaluation → Feature Importance
```

### Models Compared

| Model | RMSE | MAE | R² |
|---|---|---|---|
| Linear Regression | $191 | $154 | 0.693 |
| Ridge Regression | $191 | $154 | 0.692 |
| Random Forest | $173 | $134 | 0.748 |
| **Gradient Boosting** | **$131** | **$104** | **0.855** |

**Gradient Boosting** is the best-performing model — a **24% improvement in RMSE** over the linear baseline.

---

##  Key Findings

- **Telematics signals dominate:** The composite driving risk score, hard braking, avg speed, and phone use are stronger predictors than static demographics alone
- **Prior claims still matter:** Even in a telematics setting, claims history adds significant signal
- **Non-linear age effect:** Both young drivers (<25) and older drivers (>65) attract higher premiums — captured better by ensemble models than linear regression
- **Sports cars pay most:** $1,750 median premium vs $1,350 for Hatchbacks

---

##  Business Implications

- Safe drivers could receive discounts of **15–25%** under a UBI pricing model
- **Phone use per trip** is the most actionable lever — in-app coaching or blocking while driving could reduce premiums
- Telematics-based pricing reduces reliance on proxy variables (zip code, demographics), improving **pricing equity**
- Feature importance outputs are audit-ready for **regulatory explainability** requirements

---
