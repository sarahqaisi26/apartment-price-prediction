# Beyond the Appraiser: Predicting Mortgaged Apartment Prices Using Machine Learning

> A Business Intelligence Graduation Project — University of Petra, 2025/2026

---

## Authors

| Name | Student Number |
|------|---------------|
| Sara Al-Qaisi |202210717|
| Meerah Al-Dmour |202210974|

**Supervised by:** Dr. Hussam Burham  
**Course:**  Graduation Project  
**Semester:** Second Semester, 2026

---

## Project Overview

Traditional property appraisers in Jordan rely on subjective judgment and manual inspection to estimate apartment values — a process that is slow, inconsistent, and expensive. This project replaces that process with a **machine learning model** trained on real transaction data from Company X, a Jordanian real estate firm.

The model predicts the fair market price of a mortgaged apartment based on 22 features including location, size, floor, building age, and amenities — achieving an **R² score of 0.72** using Gradient Boosting, meaning it explains 72% of the variance in apartment prices.

---

## Project Structure

```
apartment-price-prediction/
├── README.md                          # This file
├── docs/
│   ├── 01_project_description.md      # Project goals and business context
│   ├── 02_data_research.md            # Data sources and acquisition
│   ├── 03_data_analysis.md            # EDA and data understanding
│   ├── 04_dashboard_design.md         # Tableau dashboard documentation
│   ├── 05_advanced_analytics.md       # ML models and results
│   └── 06_deployment.md               # How to run the project
├── data/
│   ├── raw/                           # Original Excel file
│   └── processed/                     # Cleaned data for Tableau
├── notebooks/                         # Jupyter notebook (main code)
├── dashboards/                        # Tableau dashboard export
├── models/                            # Saved ML models (.pkl)
├── requirements.txt                   # Python dependencies
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
1. Apartment Size (m²) → 58% importance
2. Location / Neighborhood → 16% importance
3. Building Age → 5% importance

---

## How to Run

```bash
# 1. Clone the repository
git clone https://github.com/your-username/apartment-price-prediction

# 2. Install dependencies
pip install -r requirements.txt

# 3. Open the notebook
jupyter notebook notebooks/apartment_price_prediction.ipynb
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
