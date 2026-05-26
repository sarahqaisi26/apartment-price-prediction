<img src="assets/LOGO.jpg" width="120" align="right"/>
<img src="assets/logo.svg" width="320"/>

![Python](https://img.shields.io/badge/Python-3.10-blue) ![scikit-learn](https://img.shields.io/badge/scikit--learn-1.3-orange) ![Tableau](https://img.shields.io/badge/Tableau-Public-lightblue) ![Status](https://img.shields.io/badge/Status-Complete-green)

---

# Numbers Don't Lie
### Replacing Traditional Appraisers with Predictive Machine Learning for Mortgaged Properties

> Every year, Jordanian courts rely on human appraisers to value mortgaged apartments before auction.
> Two appraisers. Same apartment. A difference of 50,000 JOD.
> This project fixes that.

---

## Authors

| Name | Student Number |
|------|---------------|
| Sarah Al-Qaisi | 202210717 |
| Meerah Al-Dmour | 202210974 |

**Supervised by:** Dr. Hussam Barham
**Course:** 307498 – Graduation Project
**Semester:** Second Semester, 2025/2026

---

## What We Built

A machine learning model trained on 603 real apartment transactions across 8 Jordanian cities. Given any apartment's documented features — size, location, floor, age, amenities — the model predicts its fair market price in milliseconds.

No site visit. No subjectivity. No inconsistency.

The best model, Gradient Boosting, explains **72.5% of the variance** in apartment prices with an average error of **15,193 JOD** — comparable to the gap between two independent human appraisers.

---

## Key Results

| Model | MAE (JOD) | RMSE (JOD) | R² |
|-------|-----------|------------|-----|
| Linear Regression | 21,129 | 34,391 | 0.499 |
| Ridge Regression | 20,748 | 33,334 | 0.529 |
| Lasso Regression | 20,791 | 33,736 | 0.518 |
| Decision Tree | 20,586 | 37,739 | 0.397 |
| Random Forest | 17,198 | 28,779 | 0.649 |
| **Gradient Boosting** | **15,193** | **25,472** | **0.725** |

**What drives apartment prices in Jordan?**

| Factor | Importance |
|--------|-----------|
| Apartment Size (m²) | 58.45% |
| Location / Neighborhood | 16.03% |
| Building Age | 5.37% |
| Furnishing Level | 3.77% |
| City | 3.31% |

---

## Dataset

| Property | Value |
|----------|-------|
| Total records | 603 apartments |
| Cities | Amman, Zarqa, Irbid, Madaba, Aqaba, Karak, Salt, Ajloun |
| Neighborhoods | 91 unique locations |
| Features | 22 original + 4 engineered |
| Price range | 9,975 — 359,800 JOD |
| Sources | Company X, OpenSooq, Facebook, Court Auctions |

---

## Project Structure

| Folder/File | Contents |
|-------------|----------|
| `docs/` | Full project documentation (01–06) |
| `data/raw/` | Original Excel dataset |
| `data/processed/` | Cleaned data for Tableau |
| `notebooks/` | Main Python notebook |
| `dashboards/` | Tableau workbook |
| `models/` | Saved ML models |
| `requirements.txt` | Python dependencies |
---

## How to Run

```bash
# 1. Clone the repository
git clone https://github.com/sarahqaisi26/apartment-price-prediction

# 2. Install dependencies
pip install -r requirements.txt

# 3. Open Google Colab
# 4. Upload company_X.xlsx to session storage
# 5. Run all cells from top to bottom
```

See [docs/06_deployment.md](docs/06_deployment.md) for full setup instructions.

---

## Dashboard

View the interactive Tableau dashboard:
[View on Tableau Public](https://public.tableau.com)

---

## Tools Used

| Purpose | Tool |
|---------|------|
| Data Analysis & ML | Python (pandas, scikit-learn) |
| Visualization | Matplotlib, Seaborn |
| BI Dashboard | Tableau Public |
| Development | Google Colab |
| Version Control | GitHub |

