# 📈 Demand Forecasting using Exponential Smoothing

**Instructor:** Prof. Meenakshi Kumari  
**Student:** Shubham Kurre (IIT Delhi)  
**Date:** February 2025  
**Case Study:** Forecasting Maruti Suzuki Sales (36 months → 4 months forecast)

---

## 🌟 Project Overview

This project applies **Single Exponential Smoothing (SES)** to forecast automobile sales, optimized using **Excel Solver** to minimize forecast error.  
The optimized smoothing constant (α = 0.285) reduced MAE from 17,298 to 1,116 (~15× improvement), showcasing the power of parameter tuning in time series forecasting.

---

## 🧠 1. Introduction to Demand Forecasting

**Demand Forecasting** estimates future customer demand based on historical data and statistical models.  
It is essential for:

- Production and inventory planning  
- Capacity and procurement scheduling  
- Workforce and financial forecasting  

---

## 🎯 2. Objectives of Forecasting

1. Reduce stockouts and excess inventory  
2. Optimize resource allocation  
3. Enhance production scheduling  
4. Support strategic decision-making  

---

## ⚙️ 3. Types of Forecasting Methods

### **A. Qualitative (Judgmental) Methods**
Used when historical data is limited.

| Method | Description | Use Case |
|--------|--------------|----------|
| Delphi Method | Expert consensus obtained iteratively | New product forecasting |
| Market Survey | Direct feedback from customers | Demand estimation before launch |
| Executive Opinion | Intuitive forecast by managers | Long-term strategic forecasts |
| Sales Force Composite | Inputs from sales representatives | Regional demand estimation |

---

### **B. Quantitative (Statistical) Methods**
Used when reliable historical data exists.

1. **Time Series Models** – use past patterns to predict future values.  
2. **Causal Models** – relate demand to external factors (price, marketing, GDP, etc.).

---

## 🧩 4. Components of a Time Series

| Component | Description |
|------------|--------------|
| **Trend (T)** | Long-term directional movement in data |
| **Seasonality (S)** | Periodic patterns repeating at fixed intervals |
| **Cyclical (C)** | Economic or business cycles spanning multiple years |
| **Random (R)** | Irregular or unpredictable fluctuations |

Mathematically:
$\[
Y_t = T_t + S_t + C_t + R_t
\]$

---

## 📊 5. Quantitative Forecasting Techniques

| Method | Key Idea | Best For |
|--------|-----------|----------|
| Naïve Forecast | Forecast = Last observed value | Stable data |
| Moving Average | Average of last *n* observations | Short-term smoothing |
| Weighted Moving Average | Assigns higher weight to recent data | Mild trends |
| Exponential Smoothing | Exponentially decreasing weights over time | Regular, stable data |
| Holt’s Method | Exponential smoothing with trend | Trending data |
| Holt–Winters | Adds trend + seasonality | Seasonal data |
| ARIMA | Combines autoregression, differencing, and moving average | Complex or autocorrelated data |

---

## 🔢 6. Exponential Smoothing Family (Detailed)

### **A. Single Exponential Smoothing (SES)**

Used when there is **no trend or seasonality**.

$\[
F_{t+1} = \alpha Y_t + (1 - \alpha)F_t
\]$

Where:  
- $\( F_{t+1} \)$: Forecast for next period  
- $\( Y_t \)$: Actual demand at time t  
- $\( \alpha \)$: Smoothing constant (0 < α < 1)

**Interpretation of α:**
| α Value | Effect |
|----------|--------|
| Low (≈ 0.1) | Stable, slow to react |
| High (≈ 0.9) | Quick response to recent changes |

---

### **B. Double Exponential Smoothing (Holt’s Method)**

Used when data shows a **trend**.

$\[
L_t = \alpha Y_t + (1 - \alpha)(L_{t-1} + T_{t-1})
\]$

$\[
T_t = \beta (L_t - L_{t-1}) + (1 - \beta)T_{t-1}
\]$

$\[
F_{t+m} = L_t + mT_t
\]$

Where:
- $\( L_t \)$: Estimated level  
- $\( T_t \)$: Estimated trend  
- $\( \alpha, \beta \)$: Smoothing constants

---

### **C. Triple Exponential Smoothing (Holt–Winters Method)**

Used when data has **trend and seasonality**.

$\[
L_t = \alpha \frac{Y_t}{S_{t-s}} + (1 - \alpha)(L_{t-1} + T_{t-1})
\]$

$\[
T_t = \beta (L_t - L_{t-1}) + (1 - \beta)T_{t-1}
\]$

$\[
S_t = \gamma \frac{Y_t}{L_t} + (1 - \gamma)S_{t-s}
\]$

$\[
F_{t+m} = (L_t + mT_t)S_{t+m-s}
\]$

Where:
- $\( S_t \)$: Seasonal component  
- $\( s \)$: Seasonal period  
- $\( \gamma \)$: Seasonal smoothing constant  

**Model Types:**
- **Additive:** Constant seasonal amplitude  
- **Multiplicative:** Seasonal amplitude changes with level  

---

## 🧮 7. ARIMA (AutoRegressive Integrated Moving Average) Model

**ARIMA** is a powerful statistical model for time series forecasting that captures **autocorrelation**, **trend**, and **non-stationarity**.

### **General Form:**
$\[
ARIMA(p, d, q)
\]$

| Parameter | Meaning |
|------------|----------|
| **p** | Number of autoregressive (AR) terms |
| **d** | Number of differences needed to make data stationary |
| **q** | Number of moving average (MA) terms |

---

### **A. Autoregressive (AR) Component**
Uses past values of the variable to predict future values.

$\[
Y_t = c + \phi_1 Y_{t-1} + \phi_2 Y_{t-2} + ... + \epsilon_t
\]$

---

### **B. Differencing (I Component)**
Removes trend and stabilizes mean of non-stationary data.

$\[
Y_t' = Y_t - Y_{t-1}
\]$

---

### **C. Moving Average (MA) Component**
Uses past forecast errors to improve predictions.

$\[
Y_t = c + \theta_1 \epsilon_{t-1} + \theta_2 \epsilon_{t-2} + \epsilon_t
\]$

---

### **D. Seasonal ARIMA (SARIMA)**
Extends ARIMA by incorporating **seasonal autoregression and differencing**:
$\[
ARIMA(p, d, q)(P, D, Q)_s
\]$
where *s* is the seasonal period (e.g., 12 for monthly data).

---

### **When to Use ARIMA:**
- Data shows autocorrelation or non-stationary trends  
- No obvious seasonality (for seasonal patterns → SARIMA)  
- When exponential smoothing doesn’t adequately model dependencies  

---

## 📏 8. Forecast Error Metrics

| Metric | Formula | Interpretation |
|--------|----------|----------------|
| **Error (eₜ)** | $e_t = Y_t - F_t$ | Difference per period |
| **MAE** | $\text{MAE} = \frac{1}{n} \sum_{t=1}^{n} |e_t|$ | Average absolute error |
| **MSE** | $\text{MSE} = \frac{1}{n} \sum_{t=1}^{n} e_t^2$ | Penalizes large errors |
| **RMSE** | $\text{RMSE} = \sqrt{\text{MSE}}$ | Standard deviation of forecast errors |
| **MAPE** | $\text{MAPE} = \frac{100}{n} \sum_{t=1}^{n} \frac{|e_t|}{Y_t}$ | Percentage accuracy |
| **Bias** | $\text{Bias} = \frac{1}{n} \sum_{t=1}^{n} e_t$ | Directional tendency of errors |

> **A good model** minimizes MAE/MSE and maintains near-zero bias.


---

## 🧠 9. Optimization of Smoothing Constants

To find optimal α, β, and γ:
- **Trial-and-error:** Vary parameters manually and compare MAE.  
- **Excel Solver / Optimization Tools:** Automate minimization of MAE or MSE.  
- **Automated search (Grid Search / ML libraries):** For large datasets.

Example:  
Optimized α = 0.285 reduced MAE from 17,298 → 1,116 (~15× improvement).

---

## 🧩 10. Practical Steps in Forecasting Workflow

1. **Data Collection:** Obtain reliable time series data.  
2. **Visualization:** Identify patterns, seasonality, and trends.  
3. **Stationarity Check (for ARIMA):** Apply differencing if required.  
4. **Model Selection:** Choose SES, Holt’s, Holt–Winters, or ARIMA.  
5. **Parameter Optimization:** Tune α, β, γ, or (p, d, q).  
6. **Validation:** Compare forecast vs. actuals using MAE/MSE.  
7. **Deployment:** Use forecast for production/inventory planning.  

---

## 🏭 11. Industrial Applications

| Sector | Use |
|---------|-----|
| Manufacturing | Production scheduling, capacity utilization |
| Automobile | Sales prediction, spare part planning |
| Retail | Inventory management and pricing decisions |
| Energy | Load demand forecasting |
| Healthcare | Medicine demand and logistics |
| Finance | Revenue and risk prediction |

---

## ⚠️ 12. Limitations of Forecasting

- Sensitive to sudden market changes or disruptions  
- Relies on historical data accuracy  
- Parameter tuning may lead to overfitting  
- Forecast accuracy declines with long horizons  

---

## 💡 13. Key Interview Points

1. **Difference between Moving Average and Exponential Smoothing:**  
   - Moving Average gives equal weights; Exponential Smoothing gives decreasing weights.  

2. **When to use ARIMA vs Exponential Smoothing:**  
   - ARIMA → suitable for autocorrelated, non-stationary data.  
   - Exponential Smoothing → simple, effective for short-term stable patterns.  

3. **Why α < 1?**  
   - Ensures gradual response and avoids overreacting to noise.  

4. **ARIMA vs Holt–Winters:**  
   - Holt–Winters explicitly models seasonality and trend using smoothing.  
   - ARIMA models these implicitly using autoregression and differencing.  

---


## ✅ Summary

> Demand Forecasting combines **statistical modeling, optimization, and business intelligence** to anticipate market needs.  
> While **Exponential Smoothing** provides simplicity and interpretability, **ARIMA** offers depth for autocorrelated or non-stationary data.  
> Effective parameter optimization, as seen in this project (α = 0.285), can drastically improve accuracy and decision-making reliability.

---


# Project

# 📊 Demand Forecasting using Exponential Smoothing

This project applies **Single Exponential Smoothing (SES)** to forecast future automobile sales, using **36 months of Maruti Suzuki data**.  
The goal was to identify the optimal smoothing factor (α) and minimize forecast error for short-term planning.


---

## 🎯 Objectives
- Forecast 4 months of sales data using **Exponential Smoothing**.
- Optimize the smoothing constant (α) to reduce **Mean Absolute Error (MAE)**.
- Visualize and interpret trends for **inventory and production planning**.

---

## 🧰 Tools & Libraries
- **Microsoft Excel** – Solver Optimization  
- **Python (Pandas, Matplotlib)** – Visualization  
- **Numpy / Statsmodels** – Time Series Analysis

---

## ⚙️ Methodology

1. **Data Source:** Monthly sales data (36 months) of *Maruti Suzuki*.
2. **Model:**  
   $\[
   F_t = \alpha A_{t-1} + (1 - \alpha) F_{t-1}
   \]$
   where $\( F_t \)$ = forecast, $\( A_t \)$ = actual, and $\( \alpha \)$ = smoothing constant.
3. **Optimization:** α tuned between 0.1–0.9 using Excel Solver.
4. **Performance Metrics:**  
   - MAE (Mean Absolute Error)  
   - MAPE (Mean Absolute Percentage Error)

---

## 📊 Results Summary

| Metric | Baseline | Optimized Model |
|---------|-----------|----------------|
| α (Alpha) | — | 0.285 |
| MAE | 17,298 | **1,116** |
| Improvement | — | ~15× reduction in error |

![Forecast Plot](Results/forecast_plot.png)

---

## 🧠 Learning Outcomes
- Understood **smoothing and lag correction** in time series forecasting.  
- Learned to **tune α using optimization techniques**.  
- Applied **visual analytics** for demand planning and supply forecasting.  
- Demonstrated practical use in **automobile industry planning**.

---

## 📂 Repository Structure
