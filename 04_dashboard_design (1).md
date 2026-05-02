# 04 — Dashboard Design and Business Insights

## 4.1 Dashboard Overview

The Tableau dashboard was built on the `apartments_tableau.csv` file exported from the Python pipeline. This file contains the original apartment data enriched with three model-generated columns: `predicted_price`, `error` (actual minus predicted), and `error_pct` (percentage error), as well as a `price_range` category column.

The dashboard is designed for business users at Company X who need to explore pricing patterns without interacting with code. It answers six core business questions through interactive visualizations.

---

## 4.2 Dashboard Components

### Chart 1: Average Price by City
**Type:** Bar Chart  
**X-axis:** City | **Y-axis:** Average Price (JOD)

**Description:** Shows the median transaction price for apartments in each of the eight cities covered by the dataset.

**Insight Derived:** Amman consistently commands the highest prices, followed by Aqaba and Irbid. Karak and Ajloun represent the most affordable markets. This chart gives lenders and courts an immediate city-level benchmark when evaluating a mortgaged property.

---

### Chart 2: Price vs. Apartment Size
**Type:** Scatter Plot  
**X-axis:** Size (m²) | **Y-axis:** Price (JOD) | **Color:** Bedrooms

**Description:** Each dot represents one apartment. The color indicates the number of bedrooms, revealing how bedroom count interacts with size to determine price.

**Insight Derived:** The positive size-price relationship is clear but not perfectly linear — significant scatter above and below the trend line confirms that location and features create substantial price variation at any given size. Outlier dots far from the trend warrant closer investigation.

---

### Chart 3: Apartments by Price Range
**Type:** Bar Chart  
**X-axis:** Price Range Category | **Y-axis:** Count

**Description:** Distributes apartments into five price bands: Under 50K, 50K–80K, 80K–120K, 120K–180K, and Above 180K JOD.

**Insight Derived:** The majority of Company X's portfolio falls in the 50K–120K range, confirming that the company primarily serves the mid-market segment. Very few properties fall below 50K or above 180K, which are underserved niches.

---

### Chart 4: Actual vs. Predicted Price
**Type:** Scatter Plot  
**X-axis:** Actual Price | **Y-axis:** Predicted Price

**Description:** Each dot represents one apartment. A perfect model would place all dots on the diagonal line. Dots above the line indicate under-prediction; dots below indicate over-prediction.

**Insight Derived:** The model performs well in the 50K–150K range where most data is concentrated. Prediction accuracy decreases for very high-value properties (above 200K), which is expected given their scarcity in the training data. This chart is the most important for evaluating model trustworthiness.

---

### Chart 5: Average Price by Location
**Type:** Horizontal Bar Chart  
**Y-axis:** Neighborhood | **X-axis:** Average Price (JOD)

**Description:** Ranks all 91 neighborhoods by average apartment price, from most to least expensive.

**Insight Derived:** Premium neighborhoods like Abdoun, Dair Ghbar, and Dabouq significantly outperform the city average, while peripheral areas like Sahab and Tbarbour fall well below. This chart is critical for court valuations — the neighborhood alone can explain a 100% price difference for otherwise identical apartments.

---

### Chart 6: City Distribution
**Type:** Pie Chart  
**Dimension:** City

**Description:** Shows the proportion of apartments in the dataset from each city.

**Insight Derived:** Amman dominates the portfolio, which explains why the model performs better for Amman properties. This also highlights a data gap — more records from smaller cities would improve model generalization.

---

### Chart 7: Price Range Distribution
**Type:** Pie Chart  
**Dimension:** Price Range

**Description:** Shows what proportion of apartments fall into each price category.

**Insight Derived:** The mid-market segment (50K–120K) accounts for the majority of transactions, confirming where Company X's core business lies and where the model is most reliable.

---

### Chart 8: Price Heatmap by City and Price Range
**Type:** Heatmap  
**Rows:** Price Range | **Columns:** City | **Color:** Average Price

**Description:** A two-dimensional view showing how price ranges distribute across cities. Darker cells indicate higher average prices.

**Insight Derived:** The heatmap reveals that Amman spans all price ranges while smaller cities are concentrated in lower bands. Aqaba shows an interesting mid-to-high concentration, reflecting its tourism-driven premium market.

---

## 4.3 Business Value of the Dashboard

The dashboard transforms raw model output into a tool that non-technical stakeholders can use directly. A court clerk, loan officer, or property manager can open the dashboard, filter by city and neighborhood, and immediately see:

- What apartments in that area typically sell for
- How the model's predictions compare to actual prices
- Whether a specific property is priced above or below market expectations

This represents a fundamental shift from subjective appraisal to data-informed valuation.
