# Gold Price Forecasting using Machine Learning & Explainable AI

A research-oriented financial forecasting study using machine learning 
and explainable AI to model gold market behavior.

## Overview

This project investigates whether macroeconomic and technical indicators 
can predict gold price returns using machine learning. The central finding 
is that while raw price prediction is deceptively easy (Linear Regression 
R²=0.99), return forecasting — the realistic task — is substantially harder, 
with most models demonstrating near-baseline predictive performance. 
LSTM was the only model to achieve positive R² 
(+0.006) on return prediction, suggesting weak but exploitable temporal 
structure in gold markets.

## Research Questions

- Do macroeconomic indicators (Treasury Yield, VIX, USD Index) carry 
  predictive signal for gold returns?
- How does forecasting difficulty change between raw prices and returns?
- Can explainable AI reveal which economic forces drive gold behavior?

## Dataset

Historical daily data (2015–2025) collected via yfinance:
Gold Futures, Silver, Crude Oil, S&P 500, USD Index, VIX, Treasury Yield

## Models & Results

| Model             | Task           | MAE     | RMSE    | R²      |
|-------------------|----------------|---------|---------|---------|
| Linear Regression | Raw Price      | 15.07   | 20.10   | 0.9947  |
| Linear Regression | Return         | 0.00696 | 0.00906 | -0.0410 |
| Random Forest     | Return         | 0.01001 | 0.01268 | -1.0394 |
| XGBoost           | Return         | 0.00693 | 0.00921 | -0.0755 |
| LSTM              | Return         | 0.00674 | 0.00886 | +0.0057 |

## Key Findings

- Treasury Yield was the strongest predictor by SHAP analysis, consistent 
  with gold's role as a non-yielding asset sensitive to interest rates
- LSTM outperformed all models on return forecasting, suggesting sequential 
  memory captures temporal dependencies that engineered lag features approximate 
  but miss
- High R² on raw prices is misleading — driven by autocorrelation, not 
  genuine forecasting power

## Tech Stack
Python, Pandas, NumPy, Scikit-learn, XGBoost, Keras, SHAP, yfinance, ta

## Limitations & Future Work
Short-term returns remain largely stochastic. Future directions include 
Transformer-based forecasting, rolling-window validation, and sentiment 
analysis integration.
