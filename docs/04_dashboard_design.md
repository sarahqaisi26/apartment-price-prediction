# 04 — Dashboard Design and Business Insights

<img width="600" src="https://github.com/user-attachments/assets/34a13830-15f8-4de2-801e-7c30cb3d2666" />

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

<img width="400" src="https://github.com/user-attachments/assets/c97f373d-5d0f-4b6e-a95b-ec845a607a84" />

**Insight:** Amman commands the highest prices, followed by Aqaba and Irbid. Karak and Ajloun represent the most affordable markets.

---

### Chart 2 — Price vs Size
**Type:** Scatter Plot

<img width="400" src="https://github.com/user-attachments/assets/0d077089-c8b6-4c86-91fa-641f5027c732" />

**Insight:** Strong positive relationship between size and price, but significant scatter confirms location creates major price variation at any given size.

---

### Chart 3 — Actual vs Predicted Price
**Type:** Scatter Plot

<img width="400" src="https://github.com/user-attachments/assets/d09905a3-6e5b-4c7a-8abd-78a757568f9c" />

**Insight:** Model performs well in the 50K–150K range. Most points cluster near the diagonal line, confirming model reliability.

---

### Chart 4 — Price Range Distribution
**Type:** Pie Chart

<img width="250" src="https://github.com/user-attachments/assets/71c4a9fd-5d7c-450b-9383-afc4e21539a3" />

**Insight:** Majority of apartments fall in the 50K–120K range, confirming Company X primarily serves the mid-market segment.

---

### Chart 5 — Top 10 Locations by Price
**Type:** Horizontal Bar Chart

<img width="400" src="https://github.com/user-attachments/assets/2ad7baf0-63ca-485e-b61b-8a5a4e9f6a75" />

**Insight:** Abdoun, Dair Ghbar, and Dabouq are the most expensive neighborhoods. Location alone can explain a 100% price difference for otherwise identical apartments.

---

### Chart 6 — Building Age vs Price
**Type:** Scatter Plot

<img width="400" src="https://github.com/user-attachments/assets/e808ae2b-4827-4633-8a69-0125f6eeb579" />

**Insight:** Newer buildings command higher prices. Clear price discount for buildings older than 10 years.

---

### Chart 7 — Furnished vs Unfurnished
**Type:** Bar Chart

<img width="400" src="https://github.com/user-attachments/assets/a9843ecc-6e73-4900-8d28-10f2b579e651" />

**Insight:** Furnished apartments command a price premium over unfurnished ones.

---

### Chart 8 — Price Heatmap
**Type:** Heatmap

<img width="250" src="https://github.com/user-attachments/assets/51968fcb-6134-446e-b551-36f53450e954" />

**Insight:** Amman spans all price ranges while smaller cities concentrate in lower bands.

---

### Chart 9 — City Distribution
**Type:** Pie Chart

<img width="250" src="https://github.com/user-attachments/assets/099c5e97-ef43-4e0c-a876-5ddca4589b1d" />

**Insight:** Amman dominates the portfolio, explaining why the model performs better for Amman properties.

---

### Chart 10 — Apartments by Price Range
**Type:** Bar Chart

<img width="400" src="https://github.com/user-attachments/assets/60ce2cb6-fd99-424a-a213-cd2c4a878a4a" />

**Insight:** Most apartments fall in the 80K–120K range, confirming the mid-market dominance.

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
