# 02 — Data Research and Acquisition

## 2.1 Data Search Process

The search for suitable data for this project was guided by three requirements: the data had to be specific to the Jordanian real estate market, it had to contain enough features to build a meaningful predictive model, and it had to include actual transaction prices rather than listing prices (which are often inflated above the final sale value).

Several potential sources were evaluated before settling on the Company X dataset:

**Public listing websites (OpenSooq, Bayut.jo, Aqarmap):** These platforms contain thousands of listings with price and location data. However, listing prices are asking prices, not transaction prices — they can be 10–20% above actual sale values and are therefore unsuitable as a training target for a valuation model.

**Jordan Department of Lands and Survey:** The official government registry of property transactions. While this contains verified transaction data, it is not publicly accessible in bulk format and requires formal data-sharing agreements that were outside the scope of this project.

**Company X internal dataset:** A proprietary dataset of 626 apartment records compiled from Company X's transaction history across Jordan. This dataset contains verified transaction prices alongside a rich set of property features, making it ideal for supervised learning.

---

## 2.2 Data Acquisition

The dataset was provided directly by Company X in Microsoft Excel format (`company_X.xlsx`). It required no API integration, web scraping, or database query — it was delivered as a single structured file.

**File format:** `.xlsx` (Microsoft Excel)  
**Delivery method:** Direct transfer from Company X  
**Access level:** Private / proprietary  
**Usage rights:** Granted for academic research purposes

---

## 2.3 Data Sources Summary

| Source | Type | Used? | Reason |
|--------|------|-------|--------|
| Company X dataset | Excel file (proprietary) | ✅ Yes | Verified transaction prices, rich features |
| OpenSooq.com | Web listings | ❌ No | Asking prices, not transaction prices |
| Bayut.jo | Web listings | ❌ No | Asking prices, not transaction prices |
| Jordan Lands & Survey | Government registry | ❌ No | Not publicly accessible in bulk |

---

## 2.4 Dataset Description

**File name:** `company_X.xlsx`  
**Records:** 626 apartments (603 after cleaning)  
**Features:** 22 columns  
**Geographic coverage:** 8 Jordanian cities, 91 neighborhoods  
**Price range:** 9,975 — 359,800 JOD  

The dataset covers transactions across the following cities:

| City | Apartments |
|------|-----------|
| Amman | Majority |
| Zarqa | Present |
| Irbid | Present |
| Madaba | Present |
| Aqaba | Present |
| Karak | Present |
| Salt | Present |
| Ajloun | Present |

---

## 2.5 Data Limitations

**Size:** 603 records is a relatively small dataset for machine learning. Larger datasets would likely produce higher model accuracy. The cross-validation results showed some variance between folds (R² ranging from 0.53 to 0.76), which is partly attributable to data size.

**Geographic concentration:** A significant majority of records are from Amman, which means the model has more reliable predictions for Amman neighborhoods than for smaller cities.

**Time period:** The dataset does not include transaction dates, so it is not possible to control for market fluctuations over time or build a time-series component.

**Missing features:** Several factors that are known to influence property prices are not captured in the dataset — including proximity to schools, hospitals, and commercial centers; views; internal finishing quality; and floor plan layout.
