# Energy-consumption
Electricity consumption forecast

Household Energy Consumption Forecasting (SARIMAX • Prophet • XGBoost)
This project analyzes and forecasts household energy consumption using three different modeling approaches: SARIMAX, Prophet, and XGBoost. The goal is to compare classical statistical forecasting, additive time‑series modeling, and machine‑learning‑based regression on the same 24‑hour prediction window.

📌 Dataset
Raw smart‑meter readings containing:

Date and start time

Energy usage (kWh)

Data cleaned, merged into a single timestamp, and resampled to hourly averages.

📌 Methods
1. SARIMAX (Seasonal ARIMA with Exogenous Components)
Captures autocorrelation and daily seasonality (24‑hour cycle).

Model: (1,1,1) with seasonal (1,1,1,24)

Forecasts next 24 hours using historical hourly averages.

2. Prophet (Additive Model by Meta)
Decomposes the series into trend + seasonality + holidays.

Handles missing timestamps and irregularities well.

Generates 24‑hour future predictions with uncertainty intervals.

3. XGBoost (Machine Learning Regression)
Time series reframed as a supervised ML problem.

Engineered features:

Hour, day of week, month, weekend flag

Lag features: lag1, lag24

Rolling windows: rolling_24, rolling_168

Trained on all historical data except the final 24 hours.

📌 Evaluation Metrics
All models evaluated on the same 24‑hour test window using:

MAE (Mean Absolute Error)

RMSE (Root Mean Squared Error)

R² Score

📌 Visualization
A combined plot compares:

Actual energy usage

SARIMAX predictions

Prophet predictions

XGBoost predictions

📌 Key Files
House-Hold-Energy-consumption.py — full modeling pipeline

README.md — project summary and results

Forecast plots and comparison tables

⭐ FINAL INTERPRETATION: SARIMAX vs Prophet vs XGBoost
🔹 SARIMAX — Best for Stable Seasonality
SARIMAX performed well because the dataset shows a strong daily cycle.
It captured:

Autocorrelation

24‑hour seasonality

Short‑term fluctuations

However, SARIMAX can struggle when:

Patterns shift

Nonlinear behavior appears

External factors influence usage

🔹 Prophet — Smooth, Interpretable, but Conservative
Prophet produced smooth, stable forecasts.
Strengths:

Handles missing data

Automatically models trend + seasonality

Produces uncertainty intervals

Limitations:

Can underfit sharp peaks

Less responsive to sudden changes

Prophet is excellent for business dashboards, but not always the most accurate for high‑frequency data.

🔹 XGBoost — Most Flexible and Often Most Accurate
With lag features and rolling windows, XGBoost learns:

Nonlinear patterns

Sudden spikes

Complex interactions between time‑based features

Strengths:

Captures nonlinear behavior

Learns from engineered features

Often achieves the lowest error

Limitations:

Requires careful feature engineering

Does not inherently understand time order (you handled this correctly)

🏆 Overall Conclusion
SARIMAX → Strong for classical time‑series structure

Prophet → Smooth, interpretable, business‑friendly

XGBoost → Most flexible and typically the strongest performer with proper features
