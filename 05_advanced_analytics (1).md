# 05 — Advanced Analytics and Machine Learning

## 5.1 Problem Type

This is a **supervised regression** problem. The target variable (`price`) is continuous and numeric, meaning we need a model that outputs a specific price estimate rather than a category label. The model learns the relationship between apartment features and price from labeled historical data, then applies that learned relationship to predict prices for new, unseen apartments.

---

## 5.2 Models Built and Compared

Six models were trained and evaluated on identical train/test splits to ensure a fair comparison.

### Model 1: Linear Regression
The simplest possible model — fits a straight line (hyperplane) through the data by minimizing the sum of squared errors. Assumes all feature-price relationships are linear and additive. Used as a baseline to measure how much the more complex models improve over the simplest approach.

**Result:** R² = 0.499 — explains roughly half the price variance. The linear assumption is too restrictive for this dataset.

---

### Model 2: Ridge Regression
An extension of linear regression that adds a penalty term (L2 regularization) to the loss function. This discourages any single coefficient from becoming too large, which reduces overfitting when features are correlated. The alpha parameter (set to 10) controls the strength of the penalty.

**Result:** R² = 0.529 — modest improvement over plain linear regression, suggesting mild multicollinearity in the feature set.

---

### Model 3: Lasso Regression
Similar to Ridge but uses L1 regularization, which can shrink some coefficients all the way to zero — effectively performing automatic feature selection. With alpha=100, several low-importance features were effectively eliminated.

**Result:** R² = 0.518 — similar to Ridge, confirming that many features contribute only marginally to predictive power.

---

### Model 4: Decision Tree
Builds a binary tree of if/else rules by recursively splitting the data on the feature that maximally reduces prediction error at each step. Highly interpretable — each prediction can be traced through a sequence of logical rules. However, individual trees tend to overfit without constraints.

**Parameters:** max_depth=8, random_state=42  
**Result:** R² = 0.397 — worst performer, likely due to overfitting on sparse branches in the tree.

---

### Model 5: Random Forest
An ensemble of 200 decision trees, each trained on a random subset of the data and features. Final prediction is the average across all trees. The randomization prevents any single tree from memorizing the training data, making the ensemble far more robust than a single tree.

**Parameters:** n_estimators=200, max_depth=12, min_samples_leaf=3, random_state=42  
**Result:** R² = 0.649 — strong improvement, demonstrating the value of ensemble methods.

---

### Model 6: Gradient Boosting , Best Model
Builds trees sequentially rather than in parallel. Each new tree focuses specifically on the residual errors of the previous model — gradually reducing prediction error with each iteration. The learning_rate parameter (0.05) controls how aggressively each tree corrects the previous one, preventing overshooting.

**Parameters:** n_estimators=200, max_depth=5, learning_rate=0.05, random_state=42  
**Result:** R² = 0.725 — best performer across all three metrics.

---

## 5.3 Model Performance Comparison

| Model | MAE (JOD) | RMSE (JOD) | R² |
|-------|-----------|------------|-----|
| Linear Regression | 21,129 | 34,391 | 0.499 |
| Ridge Regression | 20,748 | 33,334 | 0.529 |
| Lasso Regression | 20,791 | 33,736 | 0.518 |
| Decision Tree | 20,586 | 37,739 | 0.397 |
| Random Forest | 17,198 | 28,779 | 0.649 |
| **Gradient Boosting** | **15,193** | **25,472** | **0.725** |

**Metric definitions:**
- **MAE (Mean Absolute Error):** Average absolute difference between predicted and actual price. The most interpretable metric — our model is off by an average of 15,193 JOD per apartment.
- **RMSE (Root Mean Squared Error):** Similar to MAE but penalizes large errors more heavily. Higher than MAE indicates some significant outlier predictions.
- **R² (R-squared):** Proportion of price variance explained by the model. 0.725 means the model accounts for 72.5% of the variation in apartment prices.

---

## 5.4 Cross-Validation Results

To verify that the model's performance is stable and not dependent on a lucky train/test split, 5-fold cross-validation was performed on the full dataset.

| Fold | R² Score |
|------|---------|
| Fold 1 | 0.7224 |
| Fold 2 | 0.7632 |
| Fold 3 | 0.5876 |
| Fold 4 | 0.5371 |
| Fold 5 | 0.6257 |
| **Average** | **0.6472** |
| **Std Dev** | **0.0840** |

The variance across folds (especially Folds 3 and 4) reflects the dataset size limitation — with only 603 records and 91 neighborhoods, some folds happen to include more challenging geographic splits than others. The average cross-validation R² of 0.647 is slightly below the test-set R² of 0.725, which is a healthy sign that the model is not severely overfitting.

---

## 5.5 Feature Importance

The Gradient Boosting model assigns the following importance scores to each feature:

| Rank | Feature | Importance |
|------|---------|-----------|
| 1 | size (m²) | 58.45% |
| 2 | location_enc | 16.03% |
| 3 | Building Age | 5.37% |
| 4 | furnishing_level | 3.77% |
| 5 | city_enc | 3.31% |
| 6 | Bedrooms | 2.84% |
| 7 | Bathroom | 2.12% |
| 8–22 | Remaining features | < 2% each |

**Key finding:** Size and location together account for 74.5% of the model's predictive power. All other features collectively contribute the remaining 25.5%. This validates the real estate axiom that the three most important factors in property value are location, location, and size.

---

## 5.6 Interpretation of Results

An MAE of 15,193 JOD on a median price of ~85,000 JOD represents an average error of approximately 18%. In the context of court valuations, this is a meaningful benchmark — it tells the judge that the model's estimate has an expected margin of approximately ±15,000 JOD, which is comparable to or better than the variance between two independent human appraisers.

The model is most reliable for apartments in the 50,000–150,000 JOD range, which represents the bulk of the dataset. Predictions for very high-value properties (above 200,000 JOD) carry higher uncertainty due to the small number of such properties in the training data.

---

## 5.7 Why Gradient Boosting Won

| Reason | Explanation |
|--------|-------------|
| Handles non-linear relationships | Price doesn't increase linearly with size or age |
| Captures feature interactions | Location × size interaction affects price |
| Robust to outliers | Luxury apartments don't distort the model |
| Works well on small datasets | 603 records is enough for tree-based models |
| Sequential error correction | Each tree fixes mistakes of the previous one |

---

## 5.8 Model Limitations

| Limitation | Impact |
|-----------|--------|
| 603 training records | Limited generalization for rare property types |
| No transaction dates | Cannot account for market fluctuations over time |
| 91 neighborhoods | Some neighborhoods have very few records |
| No external features | Distance to schools, hospitals not included |
| Forced-sale vs market price | Court auction prices may differ from open market |

> **Note:** Despite these limitations, an R² of 0.725 is competitive 
> with published real estate ML studies on datasets of similar size.
