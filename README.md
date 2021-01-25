# Stock Portfolio Analysis

This repository contains the full code for the Stock Portfolio Analysis Jupyter Notebook based on Kevin Boller's "Python for Finance: Stock Portfolio Analyses" post on Medium (linked below). This altered version allows for a user to submit their portfolio transaction history and compare their performance to a S&P 500 ETF Benchmark (SPY).

Kevin Boller's Original Post: https://towardsdatascience.com/python-for-finance-stock-portfolio-analyses-6da4c3e61054

## Getting Started

### Installing Libraries and Packages

This project relies on the use of pandas and the yfinance historical market data downloader library to create a comprehensive dataframe "measuring investment inflows over equal holding periods." And utilizes plotly to visualize performance of individual investments to potentially determine where to divest holdings.
```
import pandas as pd
import numpy as np
import datetime
import plotly.express as px
import yfinance as yf
import pandas_market_calendars as mcal
from plotly.offline import init_notebook_mode, plot
init_notebook_mode(connected=True)
```

### Portfolio Data Format

Stock Transaction History should contain the following columns:
(extra column types are allowed such as notes or security, but they will not be used)
```
Symbol, Qty, Type, Open date, Adj cost per share, Adj cost
```
with values being:
```
{
  'Symbol': str,
  Qty: number,
  Type: 'Bought'|'Sold',
  Open date: yyyy-mm-dd datetime or str format,
  Adj cost per share: number,
  Adj cost: number,
  }
  ```

### Personal Data Used

This code will use your stock symbols within your csv to pull the historical data for each symbol. No personal information is shared with any other platform and all transaction history is analyzed within the notebook.

## How it Works

This code takes a list of stock symbols within a portfolio and creates a dataframe of historical returns for each stock as a daily snapshot. The dataframe is adjusted using the FIFO method and subtracts sold share amounts from the first bought share amounts to return a realistic adjusted cost per share on your investment. It also contains columns which show what your returns would have been had you spent an equivalent amount of money on the SPY stock, a strong indicator of the S&P 500's performance. Finally, plotly express uses the dataframe to compare your returns to the hypothetical S&P returns to help visualize which stocks are outperforming or underperforming the S&P 500. There is additional functionality for the program which allows the user to set a specific time frame of transaction history to compare to the benchmark rather than their complete history.

![Stock Screenshot](https://user-images.githubusercontent.com/56841052/105677466-e6daed00-5eb9-11eb-8d77-aa926b89d898.png)
