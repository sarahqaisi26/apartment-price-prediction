![Python](https://img.shields.io/badge/Python-3.10-blue)
![scikit-learn](https://img.shields.io/badge/scikit--learn-1.3-orange)
![Tableau](https://img.shields.io/badge/Tableau-Public-lightblue)
![Status](https://img.shields.io/badge/Status-Complete-green)
# Numbers Don't Lie: Replacing Traditional Appraisers with Predictive Machine Learning for Mortgaged Properties

> A Business Intelligence Graduation Project — University of Petra, 2025/2026

---

## Authors

| Name | Student Number |
|------|---------------|
| Sara Al-Qaisi | 202210717 |
| Mira Al-Damour | 202210974 |

**Supervised by:** Dr. Hussam Burham  
**Course:** 307498 – Graduation Project  
**Semester:** Second Semester, 2025/2026

---

## Project Overview

Traditional property appraisers in Jordan rely on subjective judgment and manual inspection to estimate apartment values — a process that is slow, inconsistent, and expensive. This project replaces that process with a **machine learning model** trained on real transaction data collected from multiple sources including Company X, OpenSooq, Facebook marketplace listings, and court auction records.

The model predicts the fair market price of a mortgaged apartment based on 22 features including location, size, floor, building age, and amenities — achieving an **R² score of 0.7254** using Gradient Boosting, meaning it explains 72.5% of the variance in apartment prices across 8 Jordanian cities.

---

## Priject motivation

## Why This Matters

In Jordan, mortgaged apartment valuations for court proceedings 
rely entirely on human appraisers — a process that is slow, 
expensive, and inconsistent. Two appraisers can value the same 
apartment differently by 20,000–50,000 JOD. This project 
provides a data-driven benchmark that is fast, reproducible, 
and fully transparent.

---

## Project Structure

```
apartment-price-prediction/
├── README.md
├── docs/
│   ├── 01_project_description.md
│   ├── 02_data_research.md
│   ├── 03_data_analysis.md
│   ├── 04_dashboard_design.md
│   ├── 05_advanced_analytics.md
│   └── 06_deployment.md
├── data/
│   ├── raw/                           # Original Excel file (company_X.xlsx)
│   └── processed/                     # Cleaned data for Tableau (apartments_tableau.csv)
├── notebooks/                         # Main project notebook (.ipynb)
├── dashboards/                        # Tableau dashboard export
├── models/                            # Saved ML models (.pkl files)
├── requirements.txt                   # Python dependencies
└── .gitignore
```

---

## Dataset Description

## Dataset

| Property | Value |
|----------|-------|
| Total records | 603 apartments |
| Cities covered | 8 (Amman, Zarqa, Irbid, Madaba, Aqaba, Karak, Salt, Ajloun) |
| Neighborhoods | 91 unique locations |
| Features | 22 original + 4 engineered |
| Price range | 9,975 — 359,800 JOD |
| Sources | Company X, OpenSooq, Facebook, Court Auctions |

---


## Key Results

| Model | MAE (JOD) | RMSE (JOD) | R² |
|-------|-----------|------------|-----|
| Linear Regression | 21,129 | 34,391 | 0.499 |
| Ridge Regression | 20,748 | 33,334 | 0.529 |
| Lasso Regression | 20,791 | 33,736 | 0.518 |
| Decision Tree | 20,586 | 37,739 | 0.397 |
| Random Forest | 17,198 | 28,779 | 0.649 |
| **Gradient Boosting** | **15,193** | **25,472** | **0.725** ✅ |

**Top 3 Price Factors:**
1. Apartment Size (m²) → 58.45%
2. Location / Neighborhood → 16.03%
3. Building Age → 5.37%

---

## How to Run

```bash
# 1. Clone the repository
git clone https://github.com/your-username/apartment-price-prediction

# 2. Install dependencies
pip install -r requirements.txt

# 3. Open Google Colab — https://colab.research.google.com
# 4. Upload company_X.xlsx to the session storage
# 5. Upload the notebook (.ipynb) and run all cells from top to bottom
```

See [docs/06_deployment.md](docs/06_deployment.md) for full setup instructions.

---

## Tools Used

| Purpose | Tool |
|---------|------|
| Data Analysis & ML | Python (pandas, scikit-learn) |
| Visualization | Matplotlib, Seaborn |
| BI Dashboard | Tableau Public |
| Development | Google Colab |
| Version Control | GitHub |

## Dashboard Link

## Dashboard

The interactive Tableau dashboard is available at:
[View on Tableau Public](https://public.tableau.com)

Includes 8 visualizations covering price distribution, 
city comparisons, actual vs predicted prices, and feature importance.
