# Stock Portfolio Analysis

This repository contains the full code for the Stock Portfolio Analysis Jupyter Notebook based on Kevin Boller's "Python for Finance: Stock Portfolio Analyses" post on Medium (linked below). This altered version allows for a user to submit their portfolio transaction history and compare their performance to a S&P 500 ETF Benchmark (SPY).

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
