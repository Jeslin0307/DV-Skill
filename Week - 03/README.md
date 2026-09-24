# Apple Stock Data Analysis

A data analysis project focused on exploring and preprocessing **Apple Inc. (AAPL) historical stock market data** using Python, Pandas, NumPy, and Matplotlib.

The project demonstrates the basic workflow of loading a historical stock dataset, inspecting its structure, identifying data-quality issues, and preparing the data for further analysis and visualization.

---

## Project Overview

This project works with historical stock market data for **Apple Inc. (AAPL)**.

The analysis starts by importing the dataset into a Pandas DataFrame and performing initial data inspection. The dataset is then cleaned by handling missing values and removing duplicate records.

### Workflow

```text
Apple Historical Stock Data
            ↓
      Load CSV Dataset
            ↓
     DataFrame Creation
            ↓
       Data Inspection
            ↓
     Missing Value Check
            ↓
      Duplicate Removal
            ↓
      Cleaned Dataset
            ↓
   Further Analysis / Visualization
```

---

## Project Files

| File                                | Description                                       |
| ----------------------------------- | ------------------------------------------------- |
| `Apple_Stock_Data_DV_Week_03.ipynb` | Jupyter Notebook containing the analysis workflow |
| `apple_stock_data_dv_week_03.py`    | Python script version of the analysis             |
| `Apple_historical_data.csv`         | Historical Apple stock market dataset             |
| `README.md`                         | Project documentation                             |

---

## Dataset

The project uses historical stock data for **Apple Inc. (AAPL)**.

### Dataset Information

* **Rows:** 11,355
* **Columns:** 8
* **Ticker:** AAPL
* **Company:** Apple Inc.
* **Time period:** Historical daily stock data beginning in December 1980

### Columns

| Column   | Description                                   |
| -------- | --------------------------------------------- |
| `Date`   | Trading date                                  |
| `Open`   | Opening stock price                           |
| `High`   | Highest stock price during the trading period |
| `Low`    | Lowest stock price during the trading period  |
| `Close`  | Closing stock price                           |
| `Volume` | Number of shares traded                       |
| `ticker` | Stock ticker symbol (`AAPL`)                  |
| `name`   | Dataset/company name                          |

---

## Technologies Used

* **Python**
* **Pandas** – Data loading, inspection, and cleaning
* **NumPy** – Numerical computing
* **Matplotlib** – Data visualization
* **Jupyter Notebook / Google Colab** – Interactive analysis

---

## Analysis Performed

### 1. Import Libraries

The project uses the following Python libraries:

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```

### 2. Load the Dataset

The CSV file is loaded using Pandas:

```python
df = pd.read_csv("Apple_historical_data.csv")
```

### 3. Inspect the Dataset

The first few records are displayed using:

```python
print(df.head())
```

The structure and information about the dataset are checked using:

```python
print(df.info())
```

This helps understand the available columns, data types, and dataset structure.

### 4. Data Cleaning

Missing values are removed:

```python
df = df.dropna()
```

Duplicate records are removed:

```python
df = df.drop_duplicates()
```

The resulting DataFrame represents the cleaned dataset that can be used for subsequent analysis.

---

## Stock Data Features

The dataset contains the standard OHLCV information used in stock-market analysis:

**OHLCV**

* **O** → Open
* **H** → High
* **L** → Low
* **C** → Close
* **V** → Volume

These variables can be used for additional exploratory analysis, statistical analysis, and financial visualizations.

---

## How to Run the Project

### Option 1 — Jupyter Notebook

1. Clone the repository:

```bash
git clone <YOUR-REPOSITORY-URL>
```

2. Navigate into the project folder:

```bash
cd <YOUR-REPOSITORY-NAME>
```

3. Install the required libraries:

```bash
pip install pandas numpy matplotlib jupyter
```

4. Start Jupyter Notebook:

```bash
jupyter notebook
```

5. Open:

```text
Apple_Stock_Data_DV_Week_03.ipynb
```

6. Run the notebook cells sequentially.

---

### Option 2 — Run the Python Script

Make sure the CSV file is in the same directory as the Python script.

Then run:

```bash
python apple_stock_data_dv_week_03.py
```

---

## Recommended Repository Structure

```text
apple-stock-data-analysis/
│
├── Apple_Stock_Data_DV_Week_03.ipynb
├── apple_stock_data_dv_week_03.py
├── Apple_historical_data.csv
├── README.md
└── .gitignore
```

---

## Possible Future Improvements

The current project focuses mainly on **data loading, inspection, and cleaning**. The cleaned dataset can be extended with additional analysis such as:

* Apple closing-price trend analysis
* Open vs. Close price comparison
* Daily price-change analysis
* Trading-volume analysis
* Year-wise stock performance
* Monthly and yearly aggregations
* Moving averages
* Stock-price visualization using Matplotlib
* Volatility analysis
* Correlation analysis between OHLC variables

These extensions can provide deeper insights into Apple's historical stock-price behavior.

---

## Project Objective

The main objective of this project is to demonstrate a basic **data-analysis pipeline using Python**:

```text
Load → Inspect → Clean → Analyze → Visualize
```

It provides a foundation for performing more advanced exploratory data analysis on historical stock-market data.

---

## Data Cleaning Summary

The preprocessing stage includes:

| Step | Operation                                 |
| ---- | ----------------------------------------- |
| 1    | Load CSV using Pandas                     |
| 2    | Inspect first records                     |
| 3    | Inspect DataFrame information             |
| 4    | Remove missing values                     |
| 5    | Remove duplicate records                  |
| 6    | Prepare cleaned data for further analysis |

---

## Dataset Snapshot

The dataset contains the following fields:

```text
Date
Open
High
Low
Close
Volume
ticker
name
```

The dataset contains **11,355 historical records** across these 8 columns.

---


The historical stock data is provided as part of the project dataset and should not be considered financial advice.

