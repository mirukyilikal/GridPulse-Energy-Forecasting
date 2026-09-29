# ⚡ GridPulse: Energy Usage Forecasting

## Predict Energy Demand. Optimize Operational Costs.

GridPulse is an end-to-end machine learning energy forecasting platform that predicts future electricity consumption using historical energy usage data, time-series feature engineering, and XGBoost.

The project demonstrates a complete forecasting workflow including:

- Data cleaning and preprocessing
- Exploratory Data Analysis (EDA)
- Time-series feature engineering
- Baseline forecasting models
- Machine learning forecasting
- Model evaluation and comparison
- Business interpretation
- Interactive Streamlit dashboard

---

## 📌 Business Problem

Energy providers and facility operators need accurate demand forecasts to:

- Improve demand planning
- Reduce peak-load penalties
- Optimize energy procurement
- Support renewable energy integration
- Improve operational efficiency
- Plan maintenance activities
- Reduce forecasting uncertainty

Traditional forecasting methods often fail to capture complex temporal patterns. GridPulse uses machine learning to improve forecast accuracy and provide actionable business insights.

---

## 🎯 Project Objectives

The objectives of GridPulse are to:

- Forecast future energy consumption
- Build a scalable forecasting workflow
- Compare machine learning models against naive baselines
- Identify the key drivers of energy demand
- Deliver an interactive dashboard for business users

---

## 📊 Dataset

### UCI Individual Household Electric Power Consumption Dataset

Dataset Source:

https://archive.ics.uci.edu/ml/datasets/individual+household+electric+power+consumption

### Data Description

The dataset contains household electricity consumption measurements collected over several years.

Key variables include:

| Feature | Description |
|----------|-------------|
| Global_active_power | Household global active power (kW) |
| Global_reactive_power | Household global reactive power |
| Voltage | Average voltage |
| Global_intensity | Current intensity |
| Sub_metering_1 | Kitchen energy consumption |
| Sub_metering_2 | Laundry room energy consumption |
| Sub_metering_3 | Water heater and air conditioner consumption |

Target Variable:

```text
energy_kwh
```

---

## 🛠 Technology Stack

### Programming

- Python

### Data Processing

- Pandas
- NumPy

### Visualization

- Matplotlib
- Seaborn
- Plotly

### Machine Learning

- Scikit-learn
- XGBoost

### Deployment

- Streamlit

---

## 📂 Project Structure

```text
GridPulse-Energy-Forecasting/
│
├── data/
│   ├── raw/
│   └── processed/
│
├── notebooks/
│   └── GridPulse_Energy_Forecasting.ipynb
│
├── outputs/
│   ├── figures/
│   ├── metrics/
│   └── predictions/
│
├── models/
│   └── gridpulse_xgboost.pkl
│
├── app/
│   └── streamlit_app.py
│
├── requirements.txt
│
└── README.md
```

---

## 🔍 Exploratory Data Analysis

The project includes:

### Historical Consumption Analysis

- Energy consumption over time
- Daily patterns
- Weekly patterns
- Monthly patterns
- Quarterly patterns

### Statistical Analysis

- Distribution analysis
- Density plots
- Rolling averages
- Rolling standard deviation
- Autocorrelation analysis

### Data Quality Analysis

- Missing value inspection
- Duplicate timestamp detection
- Outlier identification
- Chronological consistency checks

---

## ⚙ Feature Engineering

Time-series features were created to improve forecast performance.

### Calendar Features

- Hour
- Day of Week
- Day of Month
- Month
- Quarter
- Week of Year
- Day of Year
- Weekend Indicator

### Cyclical Features

- Hour Sin
- Hour Cos
- Month Sin
- Month Cos

### Lag Features

- Lag 1
- Lag 2
- Lag 3
- Lag 24
- Lag 48
- Lag 168

### Rolling Statistics

- Rolling Mean (3)
- Rolling Mean (6)
- Rolling Mean (24)
- Rolling Standard Deviation (24)

---

## 🚫 Preventing Data Leakage

This project uses:

- Chronological train-validation-test splitting
- Historical lag features only
- Historical rolling statistics only

No future information is used during training.

---

## 📈 Forecasting Models

### Baseline Models

#### 1. Last Value Baseline

```text
Forecast(t+1) = Actual(t)
```

#### 2. Seasonal Naive Baseline

```text
Forecast(t+1) = Actual(t-24)
```

### Machine Learning Model

#### XGBoost Regressor

Features:

- Gradient boosting
- Tree-based learning
- Handles nonlinear relationships
- Robust performance on tabular time-series features

---

## 📊 Model Performance

### Forecast Results

| Model | MAE | RMSE | R² |
|---------|---------:|---------:|---------:|
| XGBoost | 0.313 | 0.454 | 0.582 |
| Last Value Baseline | 0.372 | 0.575 | 0.330 |
| Seasonal Naive | 0.503 | 0.749 | -0.138 |

---

## ✅ Key Findings

The XGBoost model:

- Reduced forecast error by approximately 16%
- Improved RMSE by approximately 21%
- Increased explanatory power from R² = 0.33 to R² = 0.58

Compared with the strongest baseline model.

---

## 📌 Most Important Features

Top drivers of energy demand:

| Feature | Importance |
|----------|-----------:|
| lag_1 | 0.350 |
| rolling_mean_3 | 0.101 |
| hour_cos | 0.070 |
| hour | 0.045 |
| month_cos | 0.043 |
| hour_sin | 0.041 |
| lag_24 | 0.039 |
| lag_168 | 0.038 |

Key insight:

Recent consumption history is the strongest predictor of future demand.

---

## 📷 Project Visualizations

### Forecast Performance

- Actual vs Predicted Energy Consumption
- Forecast Error Distribution
- Model Comparison

### Demand Analysis

- Energy Consumption Over Time
- Average Usage by Hour
- Average Usage by Day of Week
- Monthly Demand Trends
- Rolling Mean Analysis

### Model Explainability

- Feature Importance Analysis

---

## 🖥 Streamlit Dashboard

The project includes an interactive Streamlit application featuring:

### Homepage

- GridPulse branding
- Hero section
- Forecast overview
- Business value cards

### Analytics Dashboard

- Actual vs Predicted visualization
- Forecast error analysis
- Model comparison
- Feature importance
- Business insights

---

## 🚀 Running the Project

### Install Requirements

```bash
pip install -r requirements.txt
```

### Launch Dashboard

```bash
streamlit run app/streamlit_app.py
```

---

## 💼 Business Value

GridPulse can support:

### Demand Planning

Forecast future energy needs before demand peaks occur.

### Energy Procurement

Support purchasing decisions using anticipated demand.

### Peak Load Reduction

Identify periods of high consumption risk.

### Operational Budgeting

Improve planning and forecasting accuracy.

### Renewable Energy Integration

Support battery scheduling and renewable generation planning.

---

## ⚠ Limitations

Current limitations include:

- Household-level dataset
- No weather variables
- No holiday information
- No occupancy information
- Limited external demand drivers
- Unexpected demand spikes remain difficult to predict

---

## 🔮 Future Improvements

Potential future enhancements:

- Weather integration
- Holiday calendar effects
- Real-time forecasting API
- Automated retraining pipeline
- Forecast confidence intervals
- Deep learning models (LSTM, Transformer)
- Cloud deployment
- Multi-site forecasting

---

## 🏗 Deployment Roadmap

Prototype:

```text
Google Colab
      ↓
XGBoost Model
      ↓
Streamlit Dashboard
```

Production:

```text
Data Sources
      ↓
ETL Pipeline
      ↓
Feature Store
      ↓
Forecast API (FastAPI)
      ↓
PostgreSQL Database
      ↓
Web Dashboard
      ↓
Monitoring & Alerts
```

---

## 👨‍💻 Author

**Miruk Yilikal**

Electrical and Computer Engineering Student  
Addis Ababa University

Interests:

- Machine Learning
- Data Science
- Forecasting Systems
- AI Applications
- Analytics Dashboards

---

## 📄 License

This project is intended for educational, portfolio, and demonstration purposes.

---

## ⭐ Project Summary

GridPulse demonstrates a complete machine learning forecasting workflow, transforming raw energy consumption data into actionable forecasts through feature engineering, model benchmarking, and interactive visualization.

The final XGBoost model outperformed naive forecasting baselines and provides a practical foundation for real-world energy analytics solutions.
