Automated Google Sheets Portfolio Tracker
Project Overview
Intent:
The Automated Google Sheets Portfolio Tracker started as a personal project, utilizing Google Finance functions and manual data entry. Over time, it evolved into a more comprehensive tool with fully automated processes. This tracker allows you to monitor your portfolio's performance, with minimal manual input required. The core functionalities have been designed for finance but can easily be adapted to other industries requiring data storage and automation in Google Sheets.

Functionality:
The portfolio tracker automates all data entries except for the ‘Ticker’, ‘Shares’, and ‘Purchase’ columns on the ‘Portfolio Data’ sheet. Users can input their own data here to track their portfolios. The automation processes and Python code can be repurposed for various applications beyond finance, allowing for efficient data management in Google Sheets.

Process Overview
Packages Used
Finance:
empyrial
quantstats
yfinance
Google Integration:
google.colab
gspread
google.auth
General Utilities:
numpy
pandas
datetime
Note: The line %%capture is used to suppress the output of package installations, keeping the notebook clean and focused on the core functionality.

General Process
Google Account Authentication:
The first step involves signing in with your Google Account and linking your Google Sheets via a URL. The script targets the main data sheet using .get_worksheet(1)—remember that indexing starts at 0, so this points to the second sheet in your workbook.

Pulling Ticker Data and Weights:
The script retrieves ticker data and calculates each ticker's weight in the portfolio. These variables are then used to run an empyrial backtest, store the quantitative statistics in a Pandas DataFrame, and update the Google Sheet with these statistics.

Downloading and Processing Ticker Data:
The script downloads all ticker data from Yahoo Finance, reindexes the data to avoid sorting issues, and calculates percent returns. Quantitative statistics are calculated using quantstats. To optimize performance, the script has been simplified into a single function, making it easier to add new calculations with minimal code changes.

Implementing Dividends and Dividend Calendar:
A dividend calendar is implemented to display payout structures throughout the year, helping you easily calculate your yearly and monthly income. You can adjust the time period by modifying the month_names column to your desired start and end months.

Sector Data Integration:
The script retrieves sector data for each ticker to be used in plotting. If a sector is labeled ‘N/A’, it’s likely due to the asset being an ETF. However, note that incorrect sector assignment might falsely flag an asset as an ETF.

Calculating Returns and Visualizations:
The final section calculates portfolio returns, benchmark returns, and individual asset returns. These metrics are then used to generate visualizations on the main display sheet, specifically for the charts on the right-hand side (Individual Asset Returns and Portfolio & Benchmark).
