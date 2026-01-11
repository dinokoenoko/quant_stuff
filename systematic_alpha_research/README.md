# Meta-Alpha Research on BIST100

## Overview

This project implements an end-to-end **quantitative research pipeline** for discovering, filtering, and combining trading signals (alphas) in a **cross-sectional equity setting**. Using BIST100 equities as a test universe, the project computes Alpha101-style signals, selects robust factors via regularized regression, and evaluates a long–short meta-alpha portfolio under realistic assumptions.

The focus is **research discipline and reproducibility**, not curve-fitting or production claims.

---

## Objectives

* Translate market hypotheses into quantitative alpha features
* Handle real-world, noisy financial data
* Filter and combine signals using statistically disciplined methods
* Evaluate cross-sectional long–short performance with transaction costs
* Build a reusable research framework transferable to other asset classes

---

## Data

* **Universe:** BIST100 equities
* **Frequency:** Daily
* **Period:** 2010–2025
* **Fields:**

  * Open, High, Low, Close, Volume
  * Returns
  * VWAP
  * Average Daily Volume (ADV): 10–180 day windows

Data is converted from wide format to **long (symbol–date)** format for cross-sectional analysis.

---

## Methodology

### 1. Feature Engineering

* Computation of Alpha101-style signals
* Alphas are calculated per stock and date
* Incompatible or undefined alphas are automatically skipped

### 2. Alpha Filtering & Cleaning

* Replace infinite values with NaN
* Drop overly sparse alphas (>30% NaNs)
* Winsorize extreme values (±10σ)
* Normalize features (z-score)

### 3. Meta-Alpha Construction

* **Model:** LASSO regression with time-series cross-validation
* **Objective:** Predict next-day (or multi-day) returns
* **Why LASSO:**

  * Enforces sparsity
  * Reduces overfitting
  * Improves interpretability

### 4. Target Definition

* Forward returns per stock
* Optional transaction cost adjustment
* Supports multiple holding periods (e.g., 1-day, 5-day)

### 5. Portfolio Evaluation

* Cross-sectional ranking by meta-alpha
* Quintile-based analysis
* Long–short (Q5 − Q1) portfolio
* Performance metrics:

  * Mean return
  * Volatility
  * Sharpe ratio
  * Rank correlation

---

## Results (Example)

* Successfully computed and filtered ~25–30 usable alphas
* Sparse meta-model selected a small subset of informative signals
* Long–short portfolio exhibited positive spread and stable behavior
* Performance varied across regimes, emphasizing non-stationarity

> Results are **illustrative**, not claims of persistent alpha.

---

## Project Structure

```
.
├── data/
│   └── bist100_data.pkl
├── alpha101.py          # Alpha signal definitions
├── meta_alpha.py        # Meta-alpha construction logic
├── loader.py            # Data loading & transformation
├── experiment.py        # End-to-end experiment runner
└── README.md
```

---

## Design Principles

* Research reproducibility over performance maximization
* Explicit handling of missing and noisy data
* Clear separation between data, features, and models
* Market-agnostic architecture (easily extendable to commodities, power, gas)

---

## Limitations

* Equity-based test universe (not energy markets)
* Daily frequency only
* No claim of out-of-sample persistence
* No execution or slippage modeling beyond basic transaction costs

---

## Future Extensions

* Apply framework to energy markets (power, gas, emissions)
* Integrate fundamental and weather features
* Regime-aware meta-models
* Intraday extensions
* Walk-forward validation

---

## Disclaimer

This project is for **research and educational purposes only**. It does not constitute investment advice or a production trading system.

---

## Author

Enes Köseahmetoğlu

Quantitative Research / Trading Applications
