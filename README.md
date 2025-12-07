The project calculates **True Range (TR)** and **Average True Range (ATR)** for historical stock price data.

It includes:

* fetching market data using `yfinance`;
* computing TR from the three standard components;
* computing ATR as a rolling average of TR (user-defined period);
* outputting the resulting series for volatility analysis.

Useful as a minimal example of implementing volatility indicators in Python.
