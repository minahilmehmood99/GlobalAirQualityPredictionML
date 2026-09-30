# 🌍 Global Air Quality Index (AQI) Prediction

[![Python 3.8+](https://img.shields.io/badge/Python-3.8%2B-blue.svg)](https://www.python.org/)
[![Scikit-Learn](https://img.shields.io/badge/Library-Scikit--Learn-orange.svg)](https://scikit-learn.org/)
[![Pandas](https://img.shields.io/badge/Library-Pandas-150458.svg)](https://pandas.pydata.org/)

An end-to-end Machine Learning project focused on analyzing multi-pollutant atmospheric data across major global cities to forecast the **Air Quality Index (AQI)** using supervised regression models.

---



## 📌 Project Overview

Air pollution is one of the most critical environmental threats to global public health. Predicting the **Air Quality Index (AQI)** accurately enables municipal authorities and communities to issue health advisories and take proactive measures.

### Core Objectives
1. **Automated Data Pipeline**: Streamline dynamic dataset ingestion from cloud storage using `gdown`.
2. **Exploratory Data Analysis (EDA)**: Identify statistical missingness patterns, pollutant distributions, and regional variances across major urban centers.
3. **Data Preprocessing & Cleaning**: Apply statistically justified missing value dropping and One-Hot Encoding to categorical spatial variables.
4. **Supervised Modeling & Evaluation**: Benchmark multiple regression architectures using standard quantitative metrics ($R^2$, $MSE$, $MAE$).

---

## 📊 Dataset Description

The dataset (`Air_Quality.csv`) consists of **52,704 historical atmospheric readings** captured across multiple global metropolitan areas.

### Feature Specification
| Feature Name | Type | Description |
| :--- | :--- | :--- |
| `Date` | Datetime | Timestamp of the air quality reading |
| `City` | Categorical | Target urban center (*Brasilia, Cairo, Dubai, London, New York, Sydney*) |
| `CO` | Continuous | Carbon Monoxide level ($\mu g/m^3$) |
| `CO2` | Continuous | Carbon Dioxide level ($\mu g/m^3$) |
| `NO2` | Continuous | Nitrogen Dioxide level ($\mu g/m^3$) |
| `SO2` | Continuous | Sulfur Dioxide level ($\mu g/m^3$) |
| `O3` | Continuous | Ground-level Ozone concentration ($\mu g/m^3$) |
| `PM2.5` | Continuous | Fine Particulate Matter $\le 2.5 \mu m$ |
| `PM10` | Continuous | Coarse Particulate Matter $\le 10 \mu m$ |
| **`AQI`** | Continuous | **Target Variable**: Calculated Air Quality Index |

---

## 🛠️ Data Preprocessing & Engineering

```text
[ Raw CSV / Cloud Drive ]
           │
           ▼
[ Automated gdown Retrieval ]
           │
           ▼
[ Missingness Assessment ] ──> (Dropped CO2 due to ~81.69% missingness & weak r ≈ 0.158)
           │
           ▼
[ Duplicate Verification ] ──> (Confirmed 0 duplicate records)
           │
           ▼
[ One-Hot Encoding ]       ──> (Transformed 'City' feature into binary vectors)
           │
           ▼
[ ML Model Pipelines ]
```

### Key Analytical Decisions:
1. **`CO2` Feature Dropping**: Analysis revealed that `CO2` exhibited **~81.69% missing values** distributed equally across cities. Pearson correlation between `CO2` and target `AQI` was weak ($r \approx 0.158$). Dropping `CO2` preserved dataset integrity while avoiding synthetic bias from imputation.
2. **Categorical Transformation**: Spatial attribute `City` was encoded using **One-Hot Encoding** (`pd.get_dummies`) to establish numeric input vectors for model compatibility.

---

## 🤖 Supervised Machine Learning Models

The project evaluates and compares five regression algorithms:

1. **Linear Regression**: Baseline parametric algorithm to establish linear relationships.
2. **Decision Tree Regressor**: Non-linear tree-based structure capturing non-linear split boundaries.
3. **Random Forest Regressor**: Ensemble bagging model reducing variance across trees.
4. **K-Nearest Neighbors (KNN)**: Non-parametric distance-based instance learning.
5. **Support Vector Regressor (SVR)**: Kernel-based margin optimization for continuous predictions.

### Performance Evaluation Metrics
Models are evaluated on hold-out test sets using:
* **Coefficient of Determination ($R^2$ Score)**
* **Mean Squared Error ($MSE$)**
* **Mean Absolute Error ($MAE$)**

---

## 📁 Project Directory Structure

```text
GlobalAirQualityPredictionML/
├── Air_Quality.csv            # Atmospheric pollutant dataset
├── AirQualityPrediction.ipynb # End-to-end Jupyter Notebook (EDA & Modeling)
├── requirements.txt           # Environment library dependencies
└── README.md                  # Project documentation
```

---

## ⚙️ Installation & Usage Guide

### 1. Clone the Repository
```bash
git clone [https://github.com/minahilmehmood99/GlobalAirQualityPredictionML.git](https://github.com/minahilmehmood99/GlobalAirQualityPredictionML.git)
cd GlobalAirQualityPredictionML
```

### 2. Set Up Virtual Environment (Recommended)
```bash
# Windows
python -m venv venv
venv\Scripts\activate

# macOS / Linux
python3 -m venv venv
source venv/bin/activate
```

### 3. Install Dependencies
```bash
pip install -r requirements.txt
```

### 4. Execute the Notebook
Launch Jupyter Notebook or Jupyter Lab to run `AirQualityPrediction.ipynb`:
```bash
jupyter notebook AirQualityPrediction.ipynb
```

---

## 📜 Copyright

© 2026 All rights reserved.