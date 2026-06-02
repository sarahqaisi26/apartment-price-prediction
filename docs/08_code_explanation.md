# 08 — Code Explanation

## 8.1 Overview

The project notebook consists of 10 sequential sections. Each section 
handles a specific stage of the machine learning pipeline — from loading 
raw data to generating predictions for new apartments.

---

## 8.2 Section 1 — Imports

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
from sklearn.ensemble import GradientBoostingRegressor, RandomForestRegressor
from sklearn.linear_model import LinearRegression, Ridge, Lasso
from sklearn.tree import DecisionTreeRegressor
from sklearn.model_selection import train_test_split, cross_val_score
from sklearn.preprocessing import LabelEncoder
from sklearn.metrics import mean_absolute_error, mean_squared_error, r2_score
import joblib
```

All required libraries are imported at the start. pandas and numpy handle 
data manipulation. matplotlib and seaborn handle visualization. scikit-learn 
provides all machine learning models and evaluation tools. joblib saves the 
trained model for future use.

---

## 8.3 Section 2 — Load Data

```python
url = "https://raw.githubusercontent.com/sarahqaisi26/apartment-price-prediction/main/data/raw/company_X.xlsx"
df = pd.read_excel(url)
```

Data is loaded directly from GitHub — no manual file upload needed. 
The dataset contains 626 apartment records with 22 features each.

---

## 8.4 Section 3 — Data Cleaning

```python
# Remove empty rows
df.dropna(how='all', inplace=True)

# Remove apartments with price = 1 JOD (data entry error)
df = df[df['price'] > 1000]

# Standardize city names
df['city'] = df['city'].str.strip().str.title()

# Fix Salt/Salat inconsistency
df['city'] = df['city'].replace('Salat', 'Salt')

# Clip furnishing level to valid range (0-5)
df['furnishing_level(1-5)'] = df['furnishing_level(1-5)'].clip(0, 5)
```

Key cleaning steps:
- Removed 23 completely empty rows
- Removed 1 record with price = 1 JOD (data entry error)
- Standardized city names (fixed capitalization)
- Unified Salt/Salat into one city name
- Clipped furnishing level to valid range 0–5

After cleaning: **603 usable apartment records**

---

## 8.5 Section 4 — Feature Engineering

```python
# Decode floor column
def decode_floor(val):
    if val < 0:
        return 0  # basement
    return int(str(abs(val))[0])

df['floor_number'] = df['floor'].apply(decode_floor)
df['is_basement'] = (df['floor_number'] == 0).astype(int)

# Total rooms
df['total_rooms'] = df['Bedrooms'] + df['Living room'] + df['Guest room'] + df['Kitchen']

# Amenities score
df['amenities_score'] = df[['Storage', "Maid's room", 'Terrace', 
                              'Garden', 'Roof', 'Duplex', 'Balcony']].sum(axis=1)
```

4 new features were engineered:
- **floor_number** — true floor level decoded from encoded column
- **is_basement** — binary flag for below-ground units
- **total_rooms** — sum of all room counts
- **amenities_score** — cumulative count of premium features

---

## 8.6 Section 5 — EDA Charts

Key visualizations generated:
- Price distribution histogram
- Average price by city (bar chart)
- Price vs Size (scatter plot)
- Correlation heatmap
- Price by bedroom count

These charts confirmed that **size** and **location** are the dominant 
price drivers before any modeling was done.

---

## 8.7 Section 6 — Encoding

```python
le_city = LabelEncoder()
le_loc  = LabelEncoder()

df['city_enc'] = le_city.fit_transform(df['city'])
df['location_enc'] = le_loc.fit_transform(df['location'])

# Save encoders for future predictions
joblib.dump(le_city, 'le_city.pkl')
joblib.dump(le_loc,  'le_loc.pkl')
```

City (8 values) and location (91 values) are converted to numbers 
using Label Encoding. Both encoders are saved so the same mapping 
is applied when predicting new apartments.

---

## 8.8 Section 7 — Train/Test Split

```python
features = ['Building Age', 'floor_number', 'is_basement', 'Bedrooms',
            'Living room', 'Guest room', 'Bathroom', 'Kitchen', 'Storage',
            "Maid's room", 'Terrace', 'Garden', 'Roof', 'Duplex', 'Balcony',
            'size', 'city_enc', 'location_enc', 'furnished',
            'furnishing_level(1-5)', 'total_rooms', 'amenities_score']

X = df[features]
y = df['price']

X_train, X_test, y_train, y_test = train_test_split(
    X, y, test_size=0.2, random_state=42
)
```

- **Training set:** 482 apartments (80%)
- **Test set:** 121 apartments (20%)
- Random seed fixed at 42 for reproducibility

---

## 8.9 Section 8 — Train 6 Models

```python
models = {
    'Linear Regression':   LinearRegression(),
    'Ridge Regression':    Ridge(alpha=10),
    'Lasso Regression':    Lasso(alpha=100),
    'Decision Tree':       DecisionTreeRegressor(max_depth=8, random_state=42),
    'Random Forest':       RandomForestRegressor(n_estimators=200, max_depth=12, 
                                                  min_samples_leaf=3, random_state=42),
    'Gradient Boosting':   GradientBoostingRegressor(n_estimators=200, max_depth=5,
                                                      learning_rate=0.05, random_state=42)
}

for name, model in models.items():
    model.fit(X_train, y_train)
    y_pred = model.predict(X_test)
    print(f"{name}: R²={r2_score(y_test, y_pred):.3f}")
```

All 6 models trained on identical splits. Results:

| Model | R² |
|-------|----|
| Linear Regression | 0.499 |
| Ridge Regression | 0.529 |
| Lasso Regression | 0.518 |
| Decision Tree | 0.397 |
| Random Forest | 0.649 |
| **Gradient Boosting** | **0.725** |

---

## 8.10 Section 9 — Cross-Validation

```python
cv_scores = cross_val_score(best_model, X, y, cv=5, scoring='r2')
print(f"Average R²: {cv_scores.mean():.3f} ± {cv_scores.std():.3f}")
```

5-Fold Cross-Validation confirmed model stability:
- Average R² = 0.647
- Standard deviation = 0.084

---

## 8.11 Section 10 — Predict Function

```python
def predict_price(city, location, size, bedrooms, bathrooms,
                  building_age, floor_num, balcony, furnished, furnishing_level):
    
    city_enc = le_city.transform([city])[0]
    loc_enc  = le_loc.transform([location])[0]
    
    features = [[building_age, floor_num, 0, bedrooms, 1, 0,
                 bathrooms, 1, 0, 0, 0, 0, 0, 0, balcony,
                 size, city_enc, loc_enc, furnished,
                 furnishing_level, bedrooms + 2, balcony]]
    
    price = best_model.predict(features)[0]
    price = round(price / 100) * 100
    
    print(f"Predicted Price : {price:,.0f} JOD")
    print(f"Price per m²   : {price/size:,.0f} JOD/m²")

# Example
predict_price('Amman', 'Abdoun', 200, 3, 2, 3, 2, 1, 0, 0)
# Output: Predicted Price: 178,800 JOD | 894 JOD/m²
```

The prediction function accepts apartment features, encodes categorical 
variables using saved encoders, and returns an instant price estimate.

---

## 8.12 Flowchart

```
Load Data from GitHub
        ↓
Data Cleaning (603 records)
        ↓
Feature Engineering (4 new features)
        ↓
EDA & Visualization
        ↓
Label Encoding
        ↓
Train/Test Split (80/20)
        ↓
Train 6 Models
        ↓
Evaluate & Compare
        ↓
Cross-Validation
        ↓
Save Best Model (Gradient Boosting)
        ↓
Export Tableau CSV
        ↓
Predict New Apartments
```

