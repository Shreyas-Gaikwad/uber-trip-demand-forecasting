# Uber Trip Demand Forecasting System

An end-to-end **urban mobility demand analytics and forecasting system** built on real-world Uber FOIL data.
This project goes beyond basic time-series modeling to deliver **exploratory insights, robust forecasting, and an interactive analytics dashboard** suitable for decision support and planning.

The focus is not only on prediction accuracy, but on **understanding demand patterns, seasonality, and operational signals** that drive ride-hailing ecosystems.

---

## Problem Statement

Accurately forecasting ride-hailing demand is a complex real-world problem due to:

* Strong weekly and monthly seasonality
* Non-stationary demand trends over time
* Supply–demand coupling (active vehicles vs trips)
* High variance across dispatching bases

The goal of this project is to design a **data-driven demand forecasting system** that:

* Explains historical demand patterns via EDA
* Learns temporal dependencies using lagged features
* Produces reliable short-term forecasts
* Communicates insights through an interactive dashboard

---

## Features

* Comprehensive exploratory data analysis (EDA)
* Time-based feature engineering (lags, rolling windows, seasonality)
* Multiple forecasting approaches with graceful fallbacks

  * Machine Learning (Random Forest, Gradient Boosting)
  * Time-series forecasting with Prophet
* Holdout-based evaluation using MAE and RMSE
* Recursive multi-day demand forecasting
* Interactive Dash dashboard with:

  * KPI summaries
  * Trend visualizations
  * Base-level drill-down analysis
  * Forecast uncertainty bands

---

## System Architecture

```
Raw FOIL Data (CSV)
   |
   v
Data Cleaning & Validation
   |
   v
Exploratory Data Analysis (Trends, Seasonality, Distribution)
   |
   v
Feature Engineering (Lags, Rolling Means, Calendar Features)
   |
   v
Model Training & Evaluation
   |   - Random Forest
   |   - Gradient Boosting
   |   - Prophet (seasonality-aware)
   v
Demand Forecasting (Short-term, Multi-step)
   |
   v
Interactive Analytics Dashboard (Dash + Plotly)
```

---

## Models Used

| Model                       | Purpose                                                  |
| --------------------------- | -------------------------------------------------------- |
| Random Forest Regressor     | Non-linear baseline with lagged features                 |
| Gradient Boosting Regressor | High-bias–variance trade-off for time-series signals     |
| Prophet                     | Seasonality-aware forecasting with uncertainty intervals |

Prophet is preferred when available due to its ability to explicitly model weekly and monthly seasonality.
The system automatically falls back to tree-based models if Prophet is unavailable.

---

## Forecasting Strategy

* City-level daily aggregation of trips
* Next-day prediction using lagged and rolling features
* Time-aware train–test split (no leakage)
* Recursive forecasting for multi-day horizons
* Forecast uncertainty estimated from residual variance

This mirrors how short-term operational forecasts are produced in real-world mobility platforms.

---

## Dashboard

<img width="1920" height="3407" alt="image" src="https://github.com/user-attachments/assets/a27cb1e2-18ba-43ff-a21c-8c3b28223dd9" />

The Dash-based dashboard provides:

* Dataset-level KPIs (total trips, averages, active vehicles)
* Daily trip trends with forecast overlays
* Monthly and weekday demand patterns
* Weekend vs weekday demand split
* Top dispatching bases by trips and vehicle supply
* Interactive per-base time-series exploration
* 30-day demand forecast with confidence bands

---

## Data

### Dataset Source

The dataset used in this project is Uber's publicly available **FOIL (For-Hire Vehicle) trip data**, aggregated across dispatching bases.

Due to size and licensing constraints, the dataset is not included in this repository. Users should download the data separately and place it in the project directory before execution.

### Data Description

* `date` – Trip date
* `dispatching_base_number` – Uber base identifier
* `trips` – Total completed trips
* `active_vehicles` – Number of active vehicles

Data is aggregated at daily granularity for forecasting.

---

## Project Structure

```
uber-trip-demand-forecasting/
├── Uber_Trip_Demand_Forecasting.ipynb   # Complete end-to-end analysis & modeling
├── requirements.txt                     # Project dependencies
└── README.md
```

The project intentionally uses a **single, well-documented Jupyter notebook** to present the full workflow end-to-end.

---

## Installation

Clone the repository:

```bash
git clone https://github.com/Shreyas-Gaikwad/uber-trip-demand-forecasting.git
cd uber-trip-demand-forecasting
```

Create a virtual environment and install dependencies:

```bash
python -m venv .venv
source .venv/bin/activate  # Windows: .venv\\Scripts\\activate
pip install -r requirements.txt
```

---

## Usage

Run the notebook sequentially to:

1. Perform EDA and visualize demand patterns
2. Train forecasting models
3. Evaluate performance
4. Generate multi-day forecasts
5. Launch the interactive dashboard

The dashboard is launched **from within the notebook itself**.

Run the notebook sequentially until the dashboard section, then execute the Dash cell to start the server.

Once running, open the dashboard in your browser at:

```
http://127.0.0.1:8050
```

---

## Key Learnings

* Demand forecasting is as much about **understanding patterns** as prediction
* Lagged features and rolling statistics capture strong temporal signals
* Explicit seasonality modeling improves forecast stability
* Visualization is critical for trust in forecasts

---

## Contributing

Contributions are welcome.

Please open issues or submit pull requests for:

* Bug fixes
* Feature enhancements
* Dashboard improvements
* Documentation updates

---

## Author

Built by **Shreyas Gaikwad**  
Master’s in Computer Applications (MCA)  
Focus: Machine Learning, Time-Series Forecasting, and Applied Data Science
