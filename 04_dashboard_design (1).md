# 04 — Dashboard Design and Business Insights

<img width="1536" height="925" alt="Screenshot (68)" src="https://github.com/user-attachments/assets/34a13830-15f8-4de2-801e-7c30cb3d2666" />


## 4.1 Dashboard Overview

The Tableau dashboard was built on the `apartments_tableau.csv` file 
exported from the Python pipeline. This file contains the original 
apartment data enriched with model-generated columns: `predicted_price`, 
`error`, `error_pct`, and `price_range`.

The dashboard is designed for business users at Company X who need to 
explore pricing patterns without interacting with code. It answers 
core business questions through 11 interactive visualizations.

**Dashboard Link:** [View on Tableau Public](https://public.tableau.com)

---

## 4.2 Dashboard Components

### Chart 1 — Average Price by City
**Type:** Bar Chart

![Average Price by City](../assets/chart1_city.png)

**Insight:** Amman commands the highest prices, followed by Aqaba 
and Irbid. Karak and Ajloun represent the most affordable markets.

---

### Chart 2 — Price vs Size
**Type:** Scatter Plot

![Price vs Size](../assets/chart2_size.png)

**Insight:** Strong positive relationship between size and price, 
but significant scatter confirms location creates major price 
variation at any given size.

---

### Chart 3 — Actual vs Predicted Price
**Type:** Scatter Plot

![Actual vs Predicted](../assets/chart3_predicted.png)

**Insight:** Model performs well in the 50K–150K range. Most points 
cluster near the diagonal line, confirming model reliability.

---

### Chart 4 — Average Price by Bedrooms
**Type:** Bar Chart

![Price by Bedrooms](../assets/chart4_bedrooms.png)

**Insight:** Clear positive relationship between bedroom count and 
price up to 4 bedrooms.

---

### Chart 5 — Price Range Distribution
**Type:** Pie Chart

![Price Range Distribution](../assets/chart5_price_range.png)

**Insight:** Majority of apartments fall in the 50K–120K range, 
confirming Company X primarily serves the mid-market segment.

---

### Chart 6 — Top 10 Locations by Price
**Type:** Horizontal Bar Chart

![Top 10 Locations](../assets/chart6_locations.png)

**Insight:** Abdoun, Dair Ghbar, and Dabouq are the most expensive 
neighborhoods. Location alone can explain a 100% price difference 
for otherwise identical apartments.

---

### Chart 7 — Building Age vs Price
**Type:** Scatter Plot

![Building Age vs Price](../assets/chart7_building_age.png)

**Insight:** Newer buildings command higher prices. Clear price 
discount for buildings older than 10 years.

---

### Chart 8 — Furnished vs Unfurnished
**Type:** Bar Chart

![Furnished vs Unfurnished](../assets/chart8_furnished.png)

**Insight:** Furnished apartments command a price premium over 
unfurnished ones.

---

### Chart 9 — Price Heatmap
**Type:** Heatmap

![Price Heatmap](../assets/chart9_heatmap.png)

**Insight:** Amman spans all price ranges while smaller cities 
concentrate in lower bands.

---

### Chart 10 — City Distribution
**Type:** Pie Chart

![City Distribution](../assets/chart10_city_pie.png)

**Insight:** Amman dominates the portfolio, explaining why the 
model performs better for Amman properties.

---

### Chart 11 — Apartments by Price Range
**Type:** Bar Chart

![Apartments by Price Range](../assets/chart11_apartments_range.png)

**Insight:** Most apartments fall in the 80K–120K range, confirming 
the mid-market dominance.

---

## 4.3 Business Value of the Dashboard

The dashboard transforms raw model output into a tool that 
non-technical stakeholders can use directly:

| User | How They Use It |
|------|----------------|
| Court clerk | Get instant price benchmark by city and neighborhood |
| Loan officer | Verify if property price matches market value |
| Property manager | Explore pricing patterns across cities |
| Company X agent | Provide data-backed pricing to clients |

This represents a fundamental shift from subjective appraisal 
to data-informed valuation.
