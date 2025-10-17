# Statistical Arbitrage Backtesting Engine

This project details the end-to-end development of a Python-based backtesting environment for a quantitative *pairs trading* (statistical arbitrage) strategy. The objective is to model and exploit the mean-reverting behavior of the performance spread between the QQQ ETF and a synthetic basket of large-cap tech stocks.

![Performance Dashboard](img/dashboard_performance.png)

---
## Strategy Concept

The strategy is built on the hypothesis that the performance spread between two correlated assets or portfolios is stationary. When this spread deviates to a statistically significant degree, a trade is initiated with the expectation that the spread will revert to its historical mean.

1.  **Signal Calculation:** The spread (`diff`) is calculated from the rebased (base 100) performance of the two portfolios.
2.  **Z-Score Transformation:** To obtain a stationary signal that is comparable over time, the `diff` is transformed into a Z-Score using a rolling-window mean and standard deviation.
3.  **Execution Logic:** Orders are placed when the Z-Score reaches extreme thresholds (`entry_threshold`) and are closed when the signal reverts toward its mean (`exit_threshold`).

---
## Key Features

* **Complete Backtesting Engine:** Built from scratch in Python, it handles position tracking, order execution, commissions, and detailed performance logging (realized/unrealized P&L, market exposure).
* **Adaptive Z-Score Strategy:** Utilizes a rolling window to ensure the trading signal adapts to recent market conditions.
* **Advanced Performance Dashboard:** Generates a comprehensive visual report with Matplotlib, including an equity curve, P&L decomposition, market exposure, and key performance indicators (Sharpe Ratio, Max Drawdown, etc.).

---
## Tech Stack

* **Python 3.x**
* **Pandas** for data manipulation.
* **NumPy** for numerical calculations.
* **yfinance** for downloading market data.
* **Matplotlib** for data visualization.
* **Jupyter Notebook** as the research environment.

---
## How to Run This Project

1.  **Clone the repository:**
    ```bash
    git clone [URL_of_your_GitHub_repository]
    cd quant-trading-project
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
    Then, open the `backtest_notebook.ipynb` file.
