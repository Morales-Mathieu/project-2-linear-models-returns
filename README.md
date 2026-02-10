# Project 2 — Linear Models for Next-Day Return Prediction

This repository investigates whether **linear models** can predict **next-day log returns** using only information available at time t, and evaluates performance using a **strict walk-forward (out-of-sample) backtest**.

Rendered report (HTML):  
https://morales-mathieu.github.io/project-2-linear-models-returns/linear-models-returns.html

---

## Overview

### Goal
Predict the next-day log return defined as:

    y(t+1) = log(P(t+1)) − log(P(t))

### Models
- OLS (statsmodels)
- Ridge regression
- Lasso regression
- Elastic Net regression

### Baselines
- Zero return baseline
- Last return baseline

### Metrics
- RMSE
- MAE
- Directional accuracy (sign prediction)

### Validation
- Time-series **walk-forward backtesting**
- Train on past data only, test on the next period
- No random shuffling, no data leakage

---

## Methodology

### Target
- Next-day log return (shifted by one trading day).

### Features (available at time t)
- Lagged returns
- Rolling volatility
- Momentum / trend proxies
- Optional market proxy features

All features are engineered using only information available at time t.

---

## Repository structure

├── data/
│   ├── raw/
│   └── processed/
├── docs/
│   └── linear-models-returns.html
├── notebooks/
│   └── linear-models-returns.ipynb
├── reports/
│   ├── figures/
│   └── tables/
├── src/
│   ├── feature_eng.py
│   ├── metrics.py
│   └── run.py
├── requirements.txt
└── README.md


- `docs/` contains the HTML report served via GitHub Pages.
- `reports/` contains exported figures and tables.
- `src/` contains reusable code (feature engineering, metrics, walk-forward evaluation).
- `notebooks/` contains the main analysis notebook that generates the report assets.

---

## How to run locally

### Create and activate a virtual environment
```bash
python -m venv .venv
# Windows
.venv\Scripts\activate
# macOS/Linux
source .venv/bin/activate

pip install -r requirements.txt

