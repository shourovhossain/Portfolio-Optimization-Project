# Multi-Asset Portfolio Risk & Optimization Engine (US Large-Cap Equities)

## Overview

This project builds a full **quantitative portfolio analysis and optimization engine** using daily price data for:
AAPL, MSFT, GOOGL, TSLA, SBUX (2020-02-01 to 2026-03-18).

It implements:

- Return and risk modelling
- Correlation and covariance analysis
- Portfolio construction:
  - Equal-Weight
  - Minimum-Variance Portfolio (MVP)
  - Maximum Sharpe (Tangency) Portfolio
- Efficient Frontier visualization
- Risk decomposition (contribution to portfolio volatility)
- PCA factor analysis
- Rolling risk metrics (time-varying volatility and correlation)
- Monte Carlo simulation of future portfolio outcomes
- Full performance summary (return, volatility, Sharpe, max drawdown)

## Data

- Source: `pandas_datareader` (Stooq)
- Assets: AAPL, MSFT, GOOGL, TSLA, SBUX
- Frequency: Daily
- Period: 2020-01-02 to 2026-03-18

Data is reshaped into a **wide price matrix** and converted to **daily log returns**, which serve as the core input for all models.

---

## Methodology

### 1. Return & Risk Modelling

- Compute daily log returns
- Summary statistics (mean, volatility, skewness, kurtosis)
- Return distribution plots
- Correlation matrix and heatmap
- Covariance matrix and annualized volatility

### 2. Portfolio Construction

Portfolios built:

- **Equal-Weight Portfolio (EW)**
- **Minimum-Variance Portfolio (MVP)**  
  - Solves: min wᵀΣw subject to Σw = 1, w ≥ 0
- **Maximum Sharpe Portfolio (Tangency Portfolio)**  
  - Solves: max (wᵀμ / √(wᵀΣw)) subject to Σw = 1, w ≥ 0

For each portfolio:

- Daily returns
- Cumulative performance
- Annualized return and volatility
- Sharpe ratio
- Comparison plots

### 3. Efficient Frontier

- Generate thousands of random portfolios
- Compute return, volatility, and Sharpe ratio
- Plot the efficient frontier
- Highlight MVP and Max Sharpe portfolios

### 4. Risk Decomposition

For MVP and Max Sharpe:

- Portfolio volatility σₚ
- Marginal contribution to risk (MCR)
- Total contribution to risk (TCR)
- Percentage contribution to risk (PCR)

Visualized as bar charts to show which assets dominate portfolio risk.

### 5. PCA Factor Analysis

- Standardize returns
- Apply PCA to extract principal components
- Analyze variance explained by each factor
- Inspect factor loadings per asset
- Visualize loadings for PC1 and PC2

This reveals underlying **risk factors** (e.g., tech factor, TSLA-specific factor).

### 6. Rolling Risk Metrics

- 60-day rolling annualized volatility per asset
- 60-day rolling correlation (e.g., AAPL vs MSFT)
- 60-day rolling portfolio volatility for EW, MVP, Max Sharpe

Shows **time-varying risk regimes** and correlation dynamics.

### 7. Monte Carlo Simulation

- Multivariate normal model using estimated μ and Σ
- Cholesky-based simulation of correlated daily returns
- 1-year horizon, multiple paths
- Distribution of terminal portfolio values for EW, MVP, Max Sharpe
- Monte Carlo-based VaR on terminal wealth

---

## Performance Summary

A final table compares:

- Annualized return
- Annualized volatility
- Sharpe ratio
- Max drawdown
- Monte Carlo terminal value statistics (mean, 5% and 1% VaR)


## Files

- `notebook.ipynb` — Full analysis, step-by-step
- `README.md` — Project description and methodology

---

## Possible Extensions

- Include a non-zero risk-free rate
- Add transaction costs and rebalancing
- Extend the universe to more assets or sectors
- Incorporate regime-switching volatility models (e.g., GARCH)
- Backtest dynamic allocation rules

---

## Summary

This project demonstrates:

- End-to-end portfolio construction and optimization
- Professional risk and factor analysis
- Time-varying risk diagnostics
- Monte Carlo stress testing
