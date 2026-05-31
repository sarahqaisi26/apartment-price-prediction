## 7.1 Summary of Findings

This project successfully demonstrated that machine learning can produce 
meaningful and reliable apartment price estimates from structured property 
data in the Jordanian market. The Gradient Boosting Regressor, trained on 
603 apartment records from eight cities, achieved an R² score of 0.7254 — 
explaining nearly three-quarters of the observed variation in transaction prices.

With a Mean Absolute Error of 15,193 JOD, the model's average prediction 
falls within approximately 18% of the true transaction price. This level 
of accuracy is competitive with the variation observed between independent 
human appraisers operating in the same market.

---

## 7.2 Most Important Insights

| Insight | Finding |
|---------|---------|
| Top price driver | Apartment size accounts for 58.45% of price variance |
| Second driver | Neighborhood location accounts for 16.03% |
| Best model | Gradient Boosting with R² = 0.725 |
| Average error | 15,193 JOD per apartment |
| Most expensive city | Amman |
| Most expensive neighborhood | Abdoun |
| Price range | 9,975 — 359,800 JOD |

---

## 7.3 Model Performance Evaluation

| Model | MAE (JOD) | RMSE (JOD) | R² |
|-------|-----------|------------|-----|
| Linear Regression | 21,129 | 34,391 | 0.499 |
| Ridge Regression | 20,748 | 33,334 | 0.529 |
| Lasso Regression | 20,791 | 33,736 | 0.518 |
| Decision Tree | 20,586 | 37,739 | 0.397 |
| Random Forest | 17,198 | 28,779 | 0.649 |
| **Gradient Boosting** | **15,193** | **25,472** | **0.725** |

---

## 7.4 Business Impact and Recommendations

**Recommendation 1 — Adopt as pre-screening tool:**
Banks and lenders should use this model to verify whether a property's 
listed price is consistent with its market value before approving mortgages.

**Recommendat
