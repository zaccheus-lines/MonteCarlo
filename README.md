Option Hedging Simulation

This Jupyter Notebook explores option pricing and dynamic delta hedging strategies based on the Black-Scholes-Merton (BSM) model. The primary focus is on simulating the hedging process for a European call option and analyzing the resulting replicating errors under various conditions.

## Overview

The notebook covers the following key areas:

1.  **BSM Model Implementation:** Calculation of initial option value and delta using the `financepy` library.
2.  **Stock Price Simulation:** Modeling stock price paths using Geometric Brownian Motion (GBM) under specified drift ($\mu$) and volatility ($\sigma$).
3.  **Delta Hedging Simulation:** Implementation of a self-financing delta hedging strategy (`OptionSim` function) that dynamically adjusts the portfolio (cash and stock holdings) to maintain delta neutrality over time. This includes functionality to incorporate proportional transaction costs ($\phi$).
4.  **Replicating Error Analysis:** Running Monte Carlo simulations (`run_simulations` function) over numerous stock price paths to calculate the hedging P&L (replicating error) at expiration.
5.  **Impact of Hedging Frequency:** Comparing the distribution of replicating errors for different hedging frequencies (e.g., monthly, weekly, daily).
6.  **Impact of Transaction Costs:** (Likely covered in later sections of the notebook) Analyzing how transaction costs affect the hedging performance.

## Dependencies

The notebook relies on the following Python libraries:

*   `numpy`
*   `pandas`
*   `matplotlib`
*   `seaborn`
*   `financepy`

You may need to install these libraries, particularly `financepy`:

```bash
pip install numpy pandas matplotlib seaborn financepy
```

## Usage

1.  Ensure you have the required dependencies installed.
2.  Open and run the `AD_notebook.ipynb` file using Jupyter Lab, Jupyter Notebook, or a compatible IDE (like VS Code).
3.  Execute the cells sequentially to follow the analysis. Key parameters (like $S_0, K, r, \sigma, T, \mu, N, \phi$) are defined within the code cells.

## Key Functions

*   `gbm(S_0, mu, sigma, T, N)`: Simulates a stock price path using GBM.
*   `OptionSim(K, S_0, r, mu, sigma, T, N, phi=None)`: Simulates the delta hedging process for one stock path.
*   `run_simulations(K, S_0, r, mu, sigma, T, N, P=10000, phi=None)`: Runs multiple `OptionSim` simulations and returns results in a DataFrame.