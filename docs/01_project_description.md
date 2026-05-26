> **Project Title:** Numbers Don't Lie: Replacing Traditional Appraisers 
> with Predictive Machine Learning for Mortgaged Properties
>
> **Team:** Sarah Al-Qaisi | Meerah Al-Dmour
> **Supervisor:** Dr. Hussam Barham
> **University of Petra — Second Semester 2025/2026**

# 01 — Project Description and Objectives
<img src="../assets/LOGO.jpg" width="200"/> <img src="../assets/REPORT%20(4).jpg" width="200"/>

## 1.1 What is This Project About?

This project addresses a real and pressing problem in the Jordanian real estate and legal system: **the valuation of mortgaged apartments for court proceedings**.

When a borrower defaults on a mortgage, the court requires an independent valuation of the property before it can be auctioned. Currently, this valuation is performed by a licensed appraiser — a human expert who physically visits the property, compares it to nearby sales, and provides an estimated market value. While this method has been standard practice for decades, it carries significant drawbacks:

- **Inconsistency:** Two appraisers can value the same apartment differently by tens of thousands of dinars
- **Subjectivity:** The process relies on personal judgment rather than objective data
- **Cost and delay:** Each appraisal requires scheduling, travel, and manual reporting, adding time and expense to already-delayed court proceedings
- **Lack of transparency:** The methodology is rarely documented in a way that can be audited or reproduced

This project proposes a **data-driven alternative**: a machine learning model trained on hundreds of real apartment transactions from Company X, capable of generating a fair, consistent, and explainable price estimate in seconds — based solely on the apartment's documented features.



## 1.2 Industry and Business Domain

This project operates at the intersection of three domains:

**Real Estate:** The Jordanian residential property market, focused on apartments across eight cities including Amman, Zarqa, Irbid, Madaba, Aqaba, Karak, Salt, and Ajloun.

**Legal / Judicial:** The court process surrounding mortgage defaults and property auctions, where accurate valuations directly affect the financial outcomes for both lenders and borrowers.

**Business Intelligence:** The application of data analysis, predictive modeling, and visualization to turn raw transaction data into actionable business insight.

---

## 1.3 How Will It Help the Industry?

The model delivers value at multiple levels:

**For courts and legal teams:** A fast, reproducible benchmark price that can be generated the moment a case is filed, reducing dependency on appraisers and shortening case timelines.

**For banks and lenders:** A consistent internal tool for pre-screening mortgage applications — flagging properties that are priced significantly above or below their predicted market value.

**For Company X:** A data asset that transforms their historical transaction records into a strategic competitive advantage. The model can be retrained as new data arrives, continuously improving its accuracy.

**For buyers and sellers:** Greater pricing transparency in a market where information asymmetry has historically favored experienced agents over ordinary buyers.

---

## 1.4 Business Problems Being Solved

| Problem | Our Solution |
|---------|-------------|
| Appraisers are slow and expensive | Model generates prediction in milliseconds |
| Two appraisers give different valuations | Model gives consistent, reproducible results |
| No audit trail for appraisal decisions | Model methodology is fully documented and transparent |
| Banks cannot pre-screen mortgage prices at scale | Model can score thousands of properties automatically |
| Court proceedings delayed by valuation scheduling | Prediction available immediately from documented features |

---

## 1.5 Project Objectives

1. **Build a reliable predictive model** that estimates apartment prices based on physical and locational features, with an R² score above 0.65
2. **Compare multiple ML algorithms** to identify the best-performing approach for this dataset
3. **Identify key price drivers** to help Company X understand which features add the most value
4. **Produce an interactive Tableau dashboard** for non-technical business users to explore pricing patterns
5. **Deliver a reproducible codebase** that the company can extend as new transaction data becomes available
6. **Document the full methodology** in a format that satisfies both academic and business standards

---
## 1.6 Expected Outcomes

By the end of this project, the following deliverables will be produced:

| Deliverable | Description | Status |
|-------------|-------------|--------|
| Python Notebook | Full ML pipeline from data cleaning to prediction | Complete |
| Trained Model | Gradient Boosting model saved as .pkl file | Complete |
| Tableau Dashboard | 8 interactive visualizations | Complete |
| GitHub Repository | Full documentation and version control | Complete |
| Prediction Function | Ready-to-use function for new apartments | Complete |

## 1.7 Real-World Impact

This project has direct applications in three real scenarios:

- **Court Case Filed** → Judge needs property value immediately → 
Model provides benchmark in seconds
- **Bank Loan Application** → Lender needs to verify collateral value → 
Model flags overpriced properties automatically  
- **Company X Agent** → Agent needs to price a new listing → 
Model provides data-backed starting point
