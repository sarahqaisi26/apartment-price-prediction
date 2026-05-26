# 03 — Data Description and Understanding


## 3.1 Data Dictionary

Every column in the dataset is described below, including its data type, range of values, and relevance to price prediction.

| Column | Type | Description | Relevance |
|--------|------|-------------|-----------|
| `Apartment_ID` | ID | Unique identifier for each apartment | Not used in model |
| `Building Age` | Numeric | Age of the building in years | Older buildings tend to sell for less |
| `floor` | Encoded | Encoded floor position (decoded in preprocessing) | Floor level affects price |
| `Bedrooms` | Numeric | Number of bedrooms | More bedrooms = higher price (generally) |
| `Living room` | Numeric | Number of living rooms | Contributes to total room count |
| `Guest room` | Numeric | Number of guest rooms | Premium feature in Jordanian market |
| `Bathroom` | Numeric | Number of bathrooms | Strong predictor of apartment size |
| `Kitchen` | Numeric | Number of kitchens | Standard feature |
| `Storage` | Binary (0/1) | Has storage room | Minor price premium |
| `Maid's room` | Binary (0/1) | Has maid's room | Premium feature |
| `Terrace` | Binary (0/1) | Has terrace | Valued outdoor space |
| `Garden` | Binary (0/1) | Has private garden | Significant premium in Jordan |
| `Roof` | Binary (0/1) | Has roof access | Valued feature |
| `Duplex` | Binary (0/1) | Is a duplex unit | Premium apartment type |
| `Balcony` | Binary (0/1) | Has balcony | Common feature in Amman |
| `size` | Numeric | Total area in square meters | **Strongest predictor** |
| `city` | Categorical | City name (8 cities) | Major price driver |
| `location` | Categorical | Neighborhood name (91 neighborhoods) | Second strongest predictor |
| `furnished` | Binary (0/1) | Is the apartment furnished | Affects price |
| `furnishing_level(1-5)` | Numeric | Quality of furnishing on 0–5 scale | Refines furnished flag |
| `Price per SQM` | Numeric | Price ÷ size (derived) | Used for analysis only |
| `price` | Numeric | **Target variable** — transaction price in JOD | What we predict |

---

## 3.2 Engineered Features

Four additional features were created during preprocessing:

| Feature | Formula | Purpose |
|---------|---------|---------|
| `floor_number` | Decoded from `floor` column | True floor level (0 = basement) |
| `is_basement` | 1 if floor_number == 0, else 0 | Captures basement price discount |
| `total_rooms` | Sum of all room counts | Single measure of apartment scale |
| `amenities_score` | Sum of 7 binary amenity flags | Captures cumulative feature premium |

---

## 3.3 Exploratory Data Analysis

### Price Distribution

The price distribution is approximately normal with a slight right skew, indicating a small number of high-value luxury apartments pulling the mean above the median.

- **Minimum:** 9,975 JOD
- **Median:** ~85,000 JOD
- **Mean:** ~86,600 JOD
- **Maximum:** 359,800 JOD
- **Standard deviation:** ~43,400 JOD

One record with a price of 1 JOD was identified as a data entry error and removed.

### Price by City

Amman dominates the dataset and shows the highest median prices overall, though significant variation exists within Amman across neighborhoods. Zarqa and Karak show the lowest median prices, consistent with their lower land values and demand levels relative to the capital.

### Price vs. Size

The relationship between size and price is strongly positive and roughly linear, though with considerable scatter — two apartments of the same size can differ by 50,000 JOD or more depending on their location and features. This confirms that size alone is insufficient for accurate valuation.

### Correlation Analysis

Key correlations with price:

| Feature | Correlation with Price |
|---------|----------------------|
| size | +0.68 (strongest) |
| Bedrooms | +0.44 |
| Bathroom | +0.42 |
| Balcony | +0.18 |
| Garden | +0.16 |
| Building Age | -0.19 |
| is_basement | -0.14 |

Building age shows a negative correlation — older buildings sell for less. Basement apartments also carry a consistent price discount.

### Sample Apartments from the Dataset

<img src="../assets/AP_PHOTO.jpg" width="300"/> <img src="../assets/AP_PHOTO%20(3).jpg" width="300"/>

<img src="../assets/AP_PHOTO%20(4).jpg" width="300"/> <img src="../assets/AP_PHOTO%20(5).jpg" width="300"/>
---

## 3.4 Key Insights from EDA

1. **Size is the dominant price driver**, but location creates a multiplier effect — the same 150m² apartment can be worth 60,000 JOD in Zarqa and 130,000 JOD in Abdoun, Amman.

2. **Neighborhood matters more than city label** — within Amman alone, the gap between the cheapest and most expensive neighborhoods exceeds 40,000 JOD in median price.

3. **Building age has a non-linear effect** — properties under 3 years old command a clear new-build premium, while the discount for older buildings becomes more pronounced after 10 years.

4. **Most apartments are unfurnished** — only 39 of 603 apartments (6.5%) are furnished, limiting the model's ability to learn strong furnishing effects.

5. **Amenities add incremental value** — gardens and terraces add the most value among binary features, while storage rooms and maid's rooms contribute smaller premiums.

---

## 3.5 Dataset Statistics Summary

| Metric | Value |
|--------|-------|
| Total apartments | 603 |
| Cities | 8 |
| Neighborhoods | 91 |
| Numeric features | 12 |
| Binary features | 7 |
| Categorical features | 2 |
| Engineered features | 4 |
| Total features used in model | 22 |
| Missing values after cleaning | 0 |
| Price — minimum | 9,975 JOD |
| Price — median | 84,975 JOD |
| Price — mean | 86,601 JOD |
| Price — maximum | 359,800 JOD |

---

## 3.6 Why These Features Matter

The features in this dataset capture four dimensions of apartment value:

- **Physical scale** — size, bedrooms, bathrooms, total rooms
- **Location** — city, neighborhood (the two strongest predictors)
- **Condition** — building age, floor, furnished status
- **Extras** — amenities score, garden, terrace, balcony

Together, these dimensions give the model enough information to 
explain 72.5% of the price variation across 603 apartments 
in 8 Jordanian cities.
