# Statistical Arbitrage (Pairs Trading) Backtester

This repository contains a complete, event-driven backtesting engine built from scratch in Python to simulate and optimize a quantitative pairs trading strategy.
The strategy models the mean-reverting behavior of the performance spread between the QQQ ETF and a synthetic, rebased basket of 5 large-cap tech stocks (AAPL, AMZN, META, GOOGL, NFLX).

### Final Strategy Performance (5-Year Backtest)
![Final Performance Dashboard](img/best-strat.png) 


---
## Core Strategy & Methodology

The trading signal is a **rolling Z-Score** (e.g., `window=60`) applied to the performance spread. This normalizes the spread, making it stationary and allowing for the identification of statistically significant (e.g., > 2.0 $\sigma$) deviations.

* **Entry:** A position is initiated when the Z-Score breaches the `entry_threshold`.
* **Exit:** The position is closed when the Z-Score reverts to its mean and crosses the `exit_threshold`.

Systematic parameter optimization was conducted to find the ideal parameters, leading to a peak performance of **Sharpe Ratio 1.41** and a **+168% Return on Capital**.

---
## Technical Features

* **Custom Backtesting Engine:** Built entirely in **Python**, the engine handles sequential order execution (1 order/day), commission costs, and portfolio management.
* **Detailed P&L Tracking:** The engine precisely tracks and decomposes performance into `realized` and `unrealized` P&L, as well as `Net Market Exposure`.
* **Data Processing & Signal Generation:** Signal calculation and time-series analysis are handled efficiently using **Pandas** and **NumPy**.
* **Advanced Visualization:** A custom, multi-plot **Matplotlib** dashboard provides a comprehensive analysis of the equity curve, P&L decomposition, market exposure, and all key performance indicators (KPIs).

---
## How to Run

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/nadamousteau/Quant-Trading-Project.git
    cd Quant-Trading-Project
    ```

2.  **Create a virtual environment (recommended):**
    ```bash
    python -m venv venv
    source venv/bin/activate  # On Windows: venv\Scripts\activate
    ```

3.  **Install the dependencies:**
    ```bash
    pip install -r requirements.txt
    ```

4.  **Launch Jupyter Notebook:**
    ```bash
    jupyter notebook
    ```
    Then, open the `ArbitrageTrading.ipynb` file and run the cells.
