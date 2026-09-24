# Shopify Stock Data Analysis

A simple and practical **stock market data analysis project** using historical Shopify stock data.

This project explores Shopify's historical stock prices using **Python, Pandas, NumPy, and Matplotlib**. It focuses on visualizing the stock's closing-price trend and analyzing the distribution of its daily returns.

---

## Project Overview

This project uses historical Shopify stock market data to perform basic exploratory analysis and visualization.

The analysis includes:

* Loading historical Shopify stock data
* Inspecting the dataset
* Visualizing the **closing price over time**
* Calculating **daily returns**
* Visualizing the distribution of daily returns using a histogram

The project is implemented in both **Jupyter Notebook** and **Python script** formats.

---

## Objectives

The main objectives of this project are to:

1. Understand the structure of historical Shopify stock data.
2. Visualize Shopify's historical closing-price movement.
3. Calculate daily percentage returns.
4. Understand the distribution of daily stock returns.
5. Practice basic financial data analysis and visualization using Python.

---

## Dataset

The project uses historical stock data for **Shopify**.

The dataset contains **2,469 records** and **7 columns**.

### Dataset Columns

| Column      | Description                                |
| ----------- | ------------------------------------------ |
| `date`      | Date and time of the trading day           |
| `open`      | Opening stock price                        |
| `high`      | Highest stock price during the trading day |
| `low`       | Lowest stock price during the trading day  |
| `close`     | Closing stock price                        |
| `adj_close` | Adjusted closing price                     |
| `volume`    | Number of shares traded                    |

### Dataset Period

The dataset contains historical observations from:

**May 21, 2015 → March 14, 2025**

---

## Technologies Used

* **Python**
* **Pandas**
* **NumPy**
* **Matplotlib**
* **Jupyter Notebook / Google Colab**

---

## Project Structure

```text
Shopify-Stock-Data-Analysis/
│
├── Shopify_Stock_Data_DV_Week_04.ipynb
├── shopify_stock_data_dv_week_04.py
├── shopify_stock.csv
└── README.md
```

---

## Analysis Workflow

The project follows this basic data-analysis workflow:

```text
Historical Shopify Stock Data
              ↓
       Load CSV Dataset
              ↓
       Inspect Data
              ↓
   Closing Price Visualization
              ↓
       Calculate Daily Returns
              ↓
    Daily Return Distribution
```

---

## Import Required Libraries

The project uses Pandas, NumPy, and Matplotlib:

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```

---

## Load the Dataset

The Shopify stock dataset is loaded using Pandas:

```python
df = pd.read_csv("shopify_stock.csv")
```

The first few rows are displayed to inspect the data:

```python
print(df.head())
```

---

## Shopify Closing Price Visualization

The project visualizes Shopify's historical closing price using Matplotlib.

```python
plt.plot(df["date"], df["close"])

plt.xlabel("Date")
plt.ylabel("Closing Price")
plt.title("Shopify Closing Price")

plt.show()
```

### What This Visualization Shows

The line chart displays how Shopify's **closing stock price changes over time**.

This provides a simple visual overview of Shopify's historical price movement.

---

## Calculate Daily Returns

Daily returns are calculated using the percentage change in the closing price:

```python
df["Daily_Return"] = df["close"].pct_change()
```

The formula is:

```text
Daily Return = (Current Close - Previous Close) / Previous Close
```

This creates a new column called:

```text
Daily_Return
```

---

## Daily Return Distribution

The distribution of daily returns is visualized using a histogram:

```python
plt.hist(df["Daily_Return"].dropna(), bins=30)

plt.title("Daily Returns")
plt.xlabel("Daily Return")
plt.ylabel("Frequency")

plt.show()
```

### What This Visualization Shows

The histogram shows the **frequency distribution of Shopify's daily returns**.

The first return value is excluded from the visualization because `pct_change()` produces a missing value for the first observation.

---

## Visualizations

The project currently produces two main visualizations:

### 1. Shopify Closing Price

A line chart showing:

* Date on the X-axis
* Closing Price on the Y-axis

### 2. Daily Returns

A histogram showing:

* Daily Return on the X-axis
* Frequency on the Y-axis

---

## Dataset Summary

| Property          |      Value |
| ----------------- | ---------: |
| Number of records |      2,469 |
| Number of columns |          7 |
| Start date        | 2015-05-21 |
| End date          | 2025-03-14 |
| Missing values    |          0 |

---

## How to Run the Project

### Prerequisites

Make sure Python is installed on your system.

Install the required libraries:

```bash
pip install pandas numpy matplotlib jupyter
```

---

### Run the Jupyter Notebook

Start Jupyter Notebook:

```bash
jupyter notebook
```

Then open:

```text
Shopify_Stock_Data_DV_Week_04.ipynb
```

Run the cells sequentially to reproduce the analysis.

---

### Run the Python Script

Make sure these files are in the same directory:

```text
shopify_stock_data_dv_week_04.py
shopify_stock.csv
```

Then run:

```bash
python shopify_stock_data_dv_week_04.py
```

---

## Key Concepts Demonstrated

This project demonstrates several important concepts in Python-based data analysis:

### Data Handling

* Reading CSV files with Pandas
* Creating and working with DataFrames
* Inspecting tabular data

### Financial Data Analysis

* Historical stock-price analysis
* Closing-price visualization
* Daily percentage returns

### Data Visualization

* Line plots
* Histograms
* Axis labels
* Chart titles

---

## Possible Future Improvements

This project can be extended with additional analysis such as:

* Moving averages
* 50-day and 200-day moving averages
* Volatility analysis
* Trading-volume visualization
* Monthly and yearly returns
* Cumulative returns
* Open vs. Close price comparison
* High vs. Low price analysis
* Outlier detection
* Correlation analysis
* Candlestick charts

These extensions would provide a more detailed view of Shopify's historical stock behavior.

---

## Project Workflow at a Glance

```text
             SHOPIFY STOCK ANALYSIS
                       │
                       ▼
              Load CSV Dataset
                       │
                       ▼
                Inspect Data
                       │
             ┌─────────┴─────────┐
             ▼                   ▼
      Closing Price          Daily Returns
        Analysis               Analysis
             │                   │
             ▼                   ▼
       Line Chart             Histogram
```


