# Comparison of Stock Market Strategies

This repository contains the final paper and Python code for the capstone project **"Comparison of Stock Market Strategies"**, submitted for the Master of Quantitative Economics program at UCLA.

**Author:** Nicholas Pelonis  
**Advisor:** Randall Rojas  
**Date:** March 14, 2025

---

## Overview

This project evaluates a range of rule-based stock trading strategies applied to historical Tesla (TSLA) stock data. The strategies include:

- Buy and Hold
- One-Day Signal
- Mean Reversion
- Trend Following
- Relative Strength Index (RSI)

Using Python, each strategy was backtested on 7 years of training data (2012–2018) and evaluated on a one-year holdout period (2019) to test out-of-sample performance.

---

## Contents

- `Nicholas Pelonis Capstone Final Version.pdf` – Final submitted paper (includes all analysis and results)
- `strategy_code/` – Folder containing all Python scripts and notebooks used for modeling and visualization

---

## Summary of Findings

- **Buy and Hold** yielded strong performance, with a cumulative return of over 1100% and a Sharpe ratio of 0.96 during training.
- **RSI strategy**, after parameter optimization, outperformed Buy and Hold in both cumulative returns and Sharpe ratio:
  - **Training Cumulative Return**: 1313.01%
  - **Training Sharpe Ratio**: 1.01
  - **Test Year Sharpe Ratio (2019)**: 0.991 vs. 0.859 for Buy and Hold
- Other strategies (Mean Reversion, Trend Following) performed similarly to Buy and Hold but did not significantly outperform it.
- The One-Day Signal strategy consistently underperformed.

---

## Technologies Used

- Python
- pandas, numpy
- matplotlib, seaborn
- yfinance (for data collection)

---

## Data

Historical daily stock prices for Tesla (TSLA) were obtained using the `yfinance` API, covering the period from **January 2012 to December 2019**.

---

## How to Reproduce

1. Clone this repository.
2. Navigate to the .ipynb file in this folder.
3. Run the scripts or open the Jupyter notebooks to reproduce each strategy and graph.
4. Data will be pulled automatically via the `yfinance` API.

---

## License

This project is released for academic and personal use. Please credit the author if you build upon this work.

---

## Acknowledgments

Special thanks to Prof. Randall Rojas for his guidance and feedback throughout the course of this project.

