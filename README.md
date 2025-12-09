# Simple ATR Documentation

## Overview

This mini-project calculates the Average True Range (ATR) for a selected financial instrument using historical market data from Yahoo Finance. It demonstrates how to:

* Fetch data with **yfinance**
* Compute the **True Range (TR)**
* Compute the **Average True Range (ATR)** using a rolling window
* Store the results inside a **pandas DataFrame**

The code is short, but it reflects a standard workflow used in quantitative analysis and trading‑related data processing.

---

## Project Structure

The script performs the following steps in sequence:

1. **Configuration** of input parameters (ticker, period, interval, rolling window)
2. **Data download** via Yahoo Finance
3. **True Range calculation** using a helper function
4. **ATR computation** via a rolling mean
5. **Appending results** to the main DataFrame
6. **Output of the first rows** for inspection

---

## Dependencies

The project uses two Python libraries:

* `yfinance` — for pulling market data
* `pandas` — for data manipulation and rolling calculations

Both must be installed before running the script.

---

## Configuration Parameters

The script begins with four user‑defined parameters:

* **ticker**: The asset symbol (e.g., "NVDA")
* **period**: Length of historical data to download (e.g., "1mo")
* **interval**: Candle size (e.g., "1d")
* **rolling_window**: Number of periods used when calculating ATR (default: 14)

These variables allow the script to be easily adapted to another asset or timeframe.

---

## Data Download

The script uses `yf.Ticker(ticker)` to create a handler and then calls `.history()` to pull OHLCV price data.

The DataFrame includes:

* High
* Low
* Close
* Open
* Volume
* Dividends / Stock Splits (if any)

The script focuses on **High**, **Low**, and **Close** because these values define True Range.

---

## True Range Calculation

True Range is defined as the maximum of three components:

1. High − Low
2. |High − Previous Close|
3. |Low − Previous Close|

The function:

* Aligns these three series
* Computes row‑wise maximum values

This produces a time series representing daily volatility.

---

## ATR Calculation

ATR is a smoothed measure of volatility computed using a rolling window. The script applies:

* A **simple moving average** (SMA) to the TR series
* Window size defined earlier (default = 14 periods)

The ATR column is added to the main DataFrame.

---

## Output

The script prints the first 20 rows of the dataset, now including:

* TR (True Range)
* ATR (Average True Range)

This provides a quick check that calculations are correct and data is aligned.

---

## Purpose and Use Cases

This script can serve as:

* A minimal demonstration of ATR computation
* A starting point for integrating volatility indicators into trading strategies
* A template for more advanced indicator pipelines

It is intentionally simple so users can easily modify or extend it.

---

## Possible Extensions

To expand the project, consider adding:

* Plotting ATR vs. price
* Alternative smoothing options (Wilder’s smoothing, EMA)
* Multi‑ticker batch processing
* Signal generation (e.g., ATR‑based stop‑loss)
* Exporting results to CSV or a database

---

## Summary

The script provides a clear workflow for fetching market data, computing True Range, and calculating the ATR indicator. It forms a solid base for quantitative trading research or as a teaching example in Python financial analysis.
