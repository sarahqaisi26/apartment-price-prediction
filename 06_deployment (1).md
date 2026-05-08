# 06 — Project Deployment

## 6.0 Project Repository

All project files are available on GitHub:

 **[GitHub Repository](https://github.com/your-username/apartment-price-prediction)**

| File/Folder | Contents |
|-------------|----------|
| `notebooks/` | Main Python notebook |
| `data/raw/` | Original Excel dataset |
| `data/processed/` | Cleaned data for Tableau |
| `models/` | Saved ML models |
| `dashboards/` | Tableau workbook |
| `docs/` | Full project documentation |


## 6.1 How a Business User Consumes This Project

The project delivers value through two interfaces:

**1. Tableau Dashboard (for business users)**  
Non-technical stakeholders — court clerks, loan officers, property managers — interact with the Tableau Public dashboard. They can filter by city and neighborhood, explore price distributions, and compare actual versus predicted prices without touching any code.

**2. Python Prediction Function (for technical users)**  
Developers or analysts can load the saved model and call the `predict_price()` function with any apartment's features to get an instant price estimate. This function can be integrated into internal systems, APIs, or automated workflows.

---

## 6.2 Setup Instructions

### Prerequisites
- Python 3.8 or higher
- Git
-A Google account for Google Colab

### Step 1 — Clone the Repository
```bash
git clone https://github.com/your-username/apartment-price-prediction
cd apartment-price-prediction
```

### Step 2 — Install Dependencies
```bash
pip install -r requirements.txt
```

### Step 3 — Add the Data File
Place `company_X.xlsx` in the `data/raw/` folder.

### Step 4 — Run the Notebook

# Open Google Colab: https://colab.research.google.com
# Upload company_X.xlsx to session storage
# Upload the notebook and run all cells from top to bottom

---

## 6.3 Using the Prediction Function

Once the notebook has been run and the model is saved, predictions can be made as follows:

```python
import joblib
import pandas as pd

# Load saved model and encoders
model    = joblib.load('models/best_model.pkl')
le_city  = joblib.load('models/le_city.pkl')
le_loc   = joblib.load('models/le_loc.pkl')

# Predict price for a new apartment
predict_price(
    city             = 'Amman',
    location         = 'Abdoun',
    size             = 200,
    bedrooms         = 3,
    bathrooms        = 2,
    building_age     = 3,
    floor_num        = 2,
    balcony          = 1,
    furnished        = 0,
    furnishing_level = 0,
)

# Output:
# Predicted Price : 178,800 JOD
# Price per m²   : 894 JOD/m²
```

---

## 6.4 Tableau Dashboard

The Tableau dashboard is published on Tableau Public and can be accessed via browser without any installation.

**To open locally:**
1. Download Tableau Public from https://public.tableau.com/en-us/s/download
2. Open the `.twb` or `.twbx` file from the `dashboards/` folder
3. If prompted for a data source, point it to `data/processed/apartments_tableau.csv`

---

## 6.5 Tools Research and Selection

### Tools Evaluated

| Category | Tools Evaluated | Selected | Reason |
|----------|----------------|----------|--------|
| Language | Python, R | **Python** | Broader ML ecosystem, easier deployment |
| ML Library | scikit-learn, XGBoost, TensorFlow | **scikit-learn** | Sufficient for tabular data, well-documented |
| Visualization | Matplotlib, Seaborn, Plotly | **Matplotlib + Seaborn** | Integrated with pandas, no extra dependencies |
| BI Dashboard | Tableau, Power BI, Looker Studio | **Tableau Public** | Free, professional output, widely used in Jordan |
| Development | VSCode, PyCharm, Jupyter | **Google Colab** | No local installation required, free GPU |
| Version Control | GitHub, GitLab | **GitHub** | Industry standard, free for public repos |
| Model Saving | pickle, joblib, ONNX | **joblib** | Optimized for scikit-learn objects |

### Why Gradient Boosting over Deep Learning?

Deep learning models (neural networks) were considered but not pursued for this project. With only 603 records, neural networks would overfit severely — they require tens of thousands of samples to train reliably. Gradient Boosting is specifically designed for structured tabular data at this scale and consistently outperforms neural networks on small datasets in published research.

---

## 6.6 Requirements

```
pandas==2.0.0
numpy==1.24.0
matplotlib==3.7.0
seaborn==0.12.0
scikit-learn==1.3.0
joblib==1.3.0
openpyxl==3.1.0

```

---

## 6.7 Future Improvements

If this project were to move toward production deployment, the following enhancements would be valuable:

1. **Streamlit web application** — wrap the prediction function in a simple web interface that any user can access from a browser, input apartment features through a form, and receive an instant price estimate
2. **Automated retraining** — as Company X adds new transactions, the model should be retrained quarterly to stay current with market conditions
3. **Confidence intervals** — rather than a single point estimate, provide a price range (e.g., 150,000–175,000 JOD) to better communicate uncertainty to courts and lenders
4. **Geospatial features** — integrating distance to city center, schools, and commercial areas as features would likely improve accuracy significantly
5. **Time series component** — adding transaction dates would allow the model to account for market trends and seasonal patterns
