# Corporación Favorita Time-Series Forecasting

Time‑series forecasting of Corporación Favorita retail sales using multiple machine‑learning and statistical models.

## Tools & Skills Used

![Data%20Science](https://img.shields.io/badge/Data%20Science-Machine%20Learning-%23DC143C)
![Data%20Science](https://img.shields.io/badge/Data%20Science-Time--Series%20Forecasting-%23DC143C)
![Data%20Engineering](https://img.shields.io/badge/Data%20Engineering-uv-%23DE5FE9)
![Python](https://img.shields.io/badge/Python-XGBoost-%233776AB)
![Python](https://img.shields.io/badge/Python-Prophet-%233776AB)
![Python](https://img.shields.io/badge/Python-Statsmodels-%233776AB)
![Python](https://img.shields.io/badge/Python-sklearn-%233776AB)
![Python](https://img.shields.io/badge/Python-matplotlib-%233776AB)

---

## Quick Access

- [Metadata Sheet](/data/favorita-metadata.md)
- [Notebook 01 | Data Preparation](/notebooks/01-data-preparation.ipynb)
- [Notebook 02 | Exploratory Data Analysis](/notebooks/02-exploratory-data-analysis.ipynb)
- [Notebook 03 | Model: XGBoost](/notebooks/03-model-xgboost.ipynb)
- [Notebook 04 | Model: SARIMA](/notebooks/04-model-sarima.ipynb)
- [Notebook 05 | Model: Prophet](/notebooks/05-model-prophet.ipynb)

---

## Project Overview

This project addresses the challenge of predicting daily unit sales for **Corporation Favorita**, a large Ecuadorian retailer. By accurately forecasting demand, the business can optimize inventory levels, reduce waste of perishable goods, and improve overall supply chain efficiency.

---

## Problem Context

Sales forecasting is critical for retail stability. The primary challenge lies in the high volatility of daily sales, regional holiday impacts, and the influence of promotions. Failure to forecast accurately leads to stockouts (lost revenue) or overstocking (increased holding costs and waste).

---

## Data Overview

- **Dataset:** `Corporation Favorita Grocery Sales`
- **Datasource:** [Kaggle](https://www.kaggle.com/competitions/favorita-grocery-sales-forecasting/data)
- **Date Range:** 2013-01-02 to 2017-08-15
- **Training Range:** 2013-02-01 to 2013-12-31
- **Forecast Range:** 2014-01-01 to 2014-03-31
- **Sample Criteria:** Random sample of 300,000 rows featuring sales for the top 3 product families only in the Guayas region

---

## Methodology

The project followed a structured machine learning pipeline:

- **Data Preparation:** Filter for transactions in the Guayas region, limit to sales for the top 3 product families only, and take a random 300,000 rows sample.
- **EDA & Feature Engineering:** Visualization of seasonal trends and creation of temporal features and signals.
- **Modeling:** Comparative testing of three distinct approaches:
  - **XGBoost:** A gradient-boosted tree model utilizing item-level features.
  - **SARIMA:** A traditional statistical approach for time-series forecasting.
  - **Prophet:** An additive model designed for business-scale forecasting.
- **Evaluation:** Models were assessed using MAE, Bias, and R-Squared.

---

## Model Comparison

| Model | MAE | Bias | R-Square | Training Time | Verdict |
| --- | --- | --- | --- | --- | --- |
| **XGBoost** | 0.16 | 0.01 | -0.17 | 00:01 | `Best Performer` |
| **SARIMA** | 312.04 | 265.47 | -0.74 | 00:00 | Moderate |
| **Prophet** | 486.84 | 483.55 | -3.21 | 00:00 | Over-predicted |

**Note:** **XGBoost** outperformed the others because it could process "Micro" features (promotions) that univariate models ignored.

---

## Setup & Installation

### 1. Clone the Repository

```bash
git clone https://github.com/krauseannelize/project-ml-favorita-sales-forecasting.git
cd project-ml-favorita-sales-forecasting
```

### 2. Environment Setup with `uv`

```bash
# Install dependencies and create virtual environment
uv sync

# Activate the environment
# On Windows:
.venv\Scripts\activate
# On macOS/Linux:
source .venv/bin/activate
```

### 3. Data Acquisition (Kaggle)

The dataset is hosted on Kaggle. You will need the Kaggle CLI configured or a Kaggle account:

- Download the data from: [Corporation Favorita Grocery Sales Forecasting](https://www.kaggle.com/competitions/favorita-grocery-sales-forecasting/data)
- Unzip the core files required for this analysis:
  - `holidays_events.csv`
  - `items.csv`
  - `oil.csv`
  - `stores.csv`
  - `train.csv`
  - `transactions.csv`
- Place the unzipped `.csv` files into the `../data` folder

---

## Future Improvements

- **Extended Training:** Incorporating at least 24 months of data to allow models to distinguish between recurring annual cycles and one-off structural trend shifts.
- **External Regressors & Data Enrichment:** Integrating external factors such as national holidays, local payday flags (Quincena), and natural disaster data.
- **Deep Learning Architectures:** Implementing models specifically designed for complex seasonality, such as **N-BEATS** or **Temporal Fusion Transformers (TFT)**, to capture non-linear temporal dependencies.

---

## Author

**Name:** [Annelize Krause](https://www.linkedin.com/in/annelizekrause/)  
**Date:** January 2026
