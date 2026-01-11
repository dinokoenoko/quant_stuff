# Meta Alpha Research on BIST100

## Overview

This project implements an end-to-end quantitative research pipeline for discovering, filtering, and combining trading signals (or alphas) in a cross-sectional equity setting. Using each BIST100 equity, this project computes Alpha101 style signals, selects factors by regularized regression, and evaluates a long–short meta alpha portfolio under realistic assumptions.

This is a research project, not production gains.

---

## Objectives

* Translate market hypotheses into quantitative alpha features
* Handle real world noisy financial data
* Filter and combine signals using statistically disciplined methods
* Evaluate cross-sectional long–short performance with transaction costs
* Build a reusable research framework transferable to other asset classes

---

## Data

* Universe: BIST100 equities
* Frequency: Daily
* Period: 2010–2025
* Fields:

  * Open, High, Low, Close, Volume
  * Returns
  * VWAP
  * Average Daily Volume (ADV): 10–180 day windows

Data is converted from wide format to long (symbol–date) format for a proper cross-sectional analysis.

---

## Methodology

### 1. Feature Engineering

* Computation of Alpha101 paper style signals
* Alphas are calculated per stock and date
* Incompatible or undefined alphas are automatically skipped

### 2. Alpha Filtering & Cleaning

* Replace infinite values with NaN
* Drop overly sparse alphas (>30% NaNs)
* Winsorize extreme values (±10σ)
* Normalize features (z-score)

### 3. Meta-Alpha Construction

* **Model:** LassoCV regression with time series cross-validation
* **Objective:** Predict next-day (or multi-day, like 5) returns
* **Why LassoCV:**

  * Reduces overfitting
  * Improves interpretability

### 4. Target Definition

* Forward returns per stock
* Optional transaction cost adjustment
* Supports multiple holding periods (1-day, 5-day)

### 5. Portfolio Evaluation

* Cross-sectional ranking by meta alpha
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

> Results are illustrative, not claiming of immediate usable alpha.

---

## Design Principles

* Research reproducibility over performance maximization 
* Explicit handling of missing/noisy data
* Clear separation between data, features, and models by creating different classes for each
* East to implement architecture (easily extendable to commodities, power, gas etc.)

---

## Limitations

* Equity-based test universe (not energy markets, yet)
* Daily frequency 
* Only basic transaction costs added, no slippage/production costs 

---

## Future Extensions

* Possibly applying this framework to energy markets (power, gas, emissions etc.)
* Integrate fundamental and weather features
* Regime aware meta models


---

## Disclaimer

This project is for **research and educational purposes only**. It is not an investment advice or a production ready trading system.
Also i have used the first 50 alphas of the Alpha101 alphas, not because i tested other possibilities and came to the realization that this was the most profitable, because i didnt want to use all the alphas which might result in having more strategies that are profitable just by the added chance that more strategies means probability of a strategy working would increase but it would actually just be overfitting.

---

## Author

Enes Köseahmetoğlu

Quantitative Research / Trading Application
