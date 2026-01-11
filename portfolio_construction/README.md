# S&P 500 & Bonds Allocation Analysis with Monte Carlo Simulation

## Project Overview

This project explores strategic asset allocation between equities (S&P 500) and bonds using historical data and forward-looking Monte Carlo simulations. The objective is to understand how different allocation choices impact risk, return, and tail behavior of a portfolio over time.

The analysis is designed as a research and learning toolkit, combining traditional portfolio theory with simulation based risk assessment. The project is parallel with the "EDHEC Business School – Portfolio Construction & Management with Python" specialization and extends the provided tools with custom analysis and visualizations.

---

## Research Objectives

* Analyze how equity–bond allocation affects portfolio performance
* Quantify risk–return tradeoffs using historical and simulated data
* Explore tail risk and distributional properties of portfolio returns
* Provide an interactive framework for allocation experimentation

---

## Methodology

### 1. Data Sources

* S&P 500 total return proxy (FRED)
* Bond market proxy (FRED)

### 2. Portfolio Construction

* User defined allocation between equities and bonds
* Monthly rebalancing
* Wealth index construction from the given returns

### 3. Performance & Risk Metrics

For each allocation, the following statistics are computed:

* Annualized return
* Annualized volatility
* Sharpe ratio
* Maximum drawdown
* Skewness see distribution asymmetry
* Kurtosis to assess tail heaviness
* Value at Risk (VaR)
* Conditional Value at Risk (CVaR)

### 4. Monte Carlo Simulation

* Future return paths simulated via Geometric Brownian Motion
* Customizable parameters:

  * Drift
  * Volatility
  * Time horizon
  * Rebalancing frequency
* Thousands of simulated paths to assess uncertainty and downside risk

---

## Key Features

*  Interactive allocation analysis using "Ipywidgets" python library
*  Monte Carlo simulation of future portfolio wealth
*  Visualization of:

  * Historical wealth evolution
  * Simulated wealth distributions
  * Allocation sensitive performance outcomes
  * Comprehensive risk metrics 

---

## Tools & Technologies

* Python
* Pandas, Numpy
* Matplotlib
* Ipywidgets
* FRED (Federal Reserve Bank of Saint Louis) economic data

---

## Example Outputs

* Wealth evolution under different equity–bond mixes and their respective volatility and other metrics
* Distribution of terminal wealth from Monte Carlo simulations
* Sensitivity of Sharpe ratio and drawdowns to allocation changes

---

## Key Takeaways

* Portfolio outcomes are highly sensitive to allocation amounts, even within the simple asset classes
* Monte Carlo simulations reveal path dependency and tail risk not visible in historical backtests.
* Risk metrics like CVaR and drawdowns provide critical insights beyond volatility

---

## Academic Context

This project builds on tools and concepts from:

* "EDHEC Business School – Python Portfolio Construction" Specialization

The analysis uses some of the base materials with additional metrics.

---

## Disclaimer

This project is for educational and research purposes only. It is not an investment advice.
