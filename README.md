Stock Data Extraction and Visualization
Overview
This project extracts stock and revenue data for Tesla (TSLA) and GameStop (GME) using yfinance and web scraping techniques. It then visualizes the stock price trends with Python plotting.

Features
Stock Data Extraction: Uses yfinance to download historical stock data for TSLA and GME.

Revenue Data Scraping: Scrapes annual revenue data from Macrotrends.net for Tesla and GameStop.

Data Saving: Saves stock data as CSV files.

Visualization: Plots closing stock prices over time with customizable graph titles.

Requirements
Python 3.x

Libraries: yfinance, pandas, requests, beautifulsoup4, matplotlib

Install required libraries via pip:

bash
Copiar
Editar
pip install yfinance pandas requests beautifulsoup4 matplotlib
Usage
Extract Tesla stock data:

python
Copiar
Editar
import yfinance as yf
tesla = yf.Ticker("TSLA")
tesla_data = tesla.history(start="2020-01-01", end="2025-07-01")
tesla_data.reset_index(inplace=True)
tesla_data.to_csv("tesla_stock_data.csv", index=False)
Extract Tesla revenue data via web scraping:
Run the scraping script to create tesla_revenue DataFrame.

Extract GameStop stock data similarly and save as gme_stock_data.csv.

Extract GameStop revenue data via web scraping.

Plot stock price graphs:
Use the provided make_graph function with loaded CSV data.

Example Plot Function
python
Copiar
Editar
import matplotlib.pyplot as plt

def make_graph(data, title):
    plt.figure(figsize=(10, 5))
    plt.plot(data['Date'], data['Close'], label='Close Price')
    plt.title(title)
    plt.xlabel('Date')
    plt.ylabel('Stock Price (USD)')
    plt.grid(True)
    plt.legend()
    plt.tight_layout()
    plt.show()
Notes
Ensure date columns are parsed with pd.to_datetime(..., utc=True) to avoid warnings.

Always check website terms before web scraping.

The code assumes CSV files are saved and loaded locally.
