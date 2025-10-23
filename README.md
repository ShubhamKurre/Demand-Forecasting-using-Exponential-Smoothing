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
   \[
   F_t = \alpha A_{t-1} + (1 - \alpha) F_{t-1}
   \]
   where \( F_t \) = forecast, \( A_t \) = actual, and \( \alpha \) = smoothing constant.
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
