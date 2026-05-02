# Numbers Don't Lie: Replacing Traditional Appraisers with Predictive Machine Learning for Mortgaged Properties

> A Business Intelligence Graduation Project — University of Petra, 2025/2026

---

## Authors

| Name | Student Number |
|------|---------------|
| Sarah Al-Qaisi | 202210717 |
| Meerah Al-Dmour | 202210974 |

**Supervised by:** Dr. Hussam Burham  
**Course:** 307498 – Graduation Project  
**Semester:** Second Semester, 2025/2026

---

## Project Overview

Traditional property appraisers in Jordan rely on subjective judgment and manual inspection to estimate apartment values — a process that is slow, inconsistent, and expensive. This project replaces that process with a **machine learning model** trained on real transaction data collected from multiple sources including Company X, OpenSooq, Facebook marketplace listings, and court auction records.

The model predicts the fair market price of a mortgaged apartment based on 22 features including location, size, floor, building age, and amenities — achieving an **R² score of 0.7254** using Gradient Boosting, meaning it explains 72.5% of the variance in apartment prices across 8 Jordanian cities.

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
│   ├── raw/
│   └── processed/
├── notebooks/
├── dashboards/
├── models/
├── requirements.txt
└── .gitignore
```

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

## Tools Used

| Purpose | Tool |
|---------|------|
| Data Analysis & ML | Python (pandas, scikit-learn) |
| Visualization | Matplotlib, Seaborn |
| BI Dashboard | Tableau Public |
| Development | Google Colab |
| Version Control | GitHub |
