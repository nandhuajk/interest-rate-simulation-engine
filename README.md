# End-to-End Fixed Income Calibration & Simulation Engine

An institutional-grade interest rate quantitative engine built in Python. This repository ingests multi-year raw daily historical yield data for the 10-Year U.S. Treasury Note (`DGS10`) from FRED, executes an empirical calibration of a continuous-time stochastic short-rate model, and generates future multi-path interest rate trajectories.

## Financial Engineering Framework
This project implements the **Vasicek Model**, modeling the short-rate \(r_t\) via a stochastic differential equation (SDE) embedded with continuous drift mean reversion:

\[dr_t = k(\theta - r_t)dt + \sigma dW_t\]

Where:
* **k (Speed of Mean Reversion):** Quantifies how aggressively the macro economy pulls the interest rate back to its long-term baseline.
* **θ (Long-Term Mean):** The steady-state equilibrium interest rate derived from 10 years of market data.
* **σ (Volatility Parameter):** The scale factor of systemic market shocks.
* **\(dW_t\):** Standard Brownian motion (Gaussian random walk).

## Core Capabilities
* **Data Cleansing Infrastructure:** Automated parsing and forward-filling routines to account for non-trading holiday/weekend market settlement gaps.
* **Empirical OLS Calibration:** Discretizes the SDE into an ordinary least squares regression framework to extract true, non-arbitrary drift parameters.
* **Monte Carlo Execution Simulator:** Generates multi-path asset return scenarios mapped against real historical volatility bounds.