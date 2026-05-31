# Abstract

## Project Summary

The Jordanian real estate market has long depended on traditional property 
appraisers to estimate the value of mortgaged apartments during court 
proceedings. While this practice has served the industry for decades, it 
remains fundamentally limited by the subjective nature of human judgment, 
inconsistencies between different appraisers, and the time and cost 
associated with conducting manual valuations.

## Implementation Approach

This project collected 626 apartment transaction records from four sources: 
Company X, OpenSooq, Facebook marketplace listings, and court auction records. 
Following a rigorous data cleaning and feature engineering process, six machine 
learning models were trained and compared — Linear Regression, Ridge, Lasso, 
Decision Tree, Random Forest, and Gradient Boosting.

## Key Results

The Gradient Boosting model emerged as the best performer with an R² score 
of 0.7254, a Mean Absolute Error of 15,193 JOD, and an RMSE of 25,472 JOD. 
Feature importance analysis revealed that apartment size accounts for 58.45% 
of predictive power, followed by neighborhood location at 16.03%. The results 
demonstrate that machine learning can serve as a meaningful supplement to 
traditional appraisal methods.

---

## Acknowledgment

We would like to express our sincere gratitude to **Dr. Hussam Burham** for 
his continuous guidance throughout this project. We are also grateful to 
**Company X** for sharing their transaction data. Finally, we acknowledge 
the open-source community behind scikit-learn, pandas, matplotlib, and 
Tableau Public.
