# Superstore Sales Data Analysis & Visualization

A Python-based **Exploratory Data Analysis (EDA) and Data Visualization** project using the Superstore Sales dataset.
This project focuses on understanding sales data, performing basic data preprocessing, calculating delivery time, analyzing category-wise sales, and creating meaningful visualizations.

---

## Project Overview

The **Superstore Sales Data Analysis** project explores sales transactions to identify patterns and understand the distribution of sales across different product categories.

The project uses Python libraries such as **Pandas, NumPy, Matplotlib, and Seaborn** for data loading, preprocessing, analysis, and visualization.

The analysis includes:

* Loading and inspecting the dataset
* Understanding dataset structure and statistics
* Converting date columns into datetime format
* Calculating delivery duration
* Checking unique product categories
* Checking for missing values
* Analyzing total sales by category
* Visualizing category-wise sales
* Understanding the distribution of sales values

---

## Objectives

The main objectives of this project are:

1. To understand the structure and characteristics of the Superstore dataset.
2. To perform basic data preprocessing.
3. To analyze sales across different product categories.
4. To calculate the number of days taken for delivery.
5. To identify missing values in the dataset.
6. To create visualizations for better understanding of the data.
7. To practice Python-based exploratory data analysis and visualization.

---

## Dataset

The dataset contains **10,194 sales records** and **21 columns**.

### Important Columns

| Column           | Description                     |
| ---------------- | ------------------------------- |
| `Row ID`         | Unique row identifier           |
| `Order ID`       | Unique order identifier         |
| `Order Date`     | Date when the order was placed  |
| `Ship Date`      | Date when the order was shipped |
| `Ship Mode`      | Shipping method used            |
| `Customer ID`    | Customer identifier             |
| `Customer Name`  | Name of the customer            |
| `Segment`        | Customer segment                |
| `Country/Region` | Country or region               |
| `City`           | Customer city                   |
| `State/Province` | Customer state/province         |
| `Postal Code`    | Postal code                     |
| `Region`         | Sales region                    |
| `Product ID`     | Product identifier              |
| `Category`       | Main product category           |
| `Sub-Category`   | Product sub-category            |
| `Product Name`   | Product name                    |
| `Sales`          | Sales amount                    |
| `Quantity`       | Quantity ordered                |
| `Discount`       | Discount applied                |
| `Profit`         | Profit generated                |

---

## Technologies Used

* **Python**
* **Pandas**
* **NumPy**
* **Matplotlib**
* **Seaborn**
* **Jupyter Notebook / Google Colab**

---

## Data Analysis Process

### 1. Importing Libraries

The project uses Pandas and NumPy for data manipulation and Matplotlib and Seaborn for visualization.

```python
import pandas as pd
import numpy as np

import matplotlib.pyplot as plt
import seaborn as sns
```

---

### 2. Loading the Dataset

The Superstore CSV dataset is loaded using Pandas.

```python
df = pd.read_csv("samplesuperstore - samplesuperstore.csv")
```

---

### 3. Exploring the Dataset

The dataset is initially explored using:

```python
df.head()
df.info()
df.describe()
```

These functions help understand the dataset structure, data types, and statistical summary.

---

### 4. Date Preprocessing

The `Order Date` and `Ship Date` columns are converted into datetime format.

```python
df['Order Date'] = pd.to_datetime(df['Order Date'])
df['Ship Date'] = pd.to_datetime(df['Ship Date'])
```

This allows date-based calculations to be performed correctly.

---

### 5. Calculating Delivery Days

A new column called `Delivery Days` is created to determine the number of days between ordering and shipping.

```python
df['Delivery Days'] = (
    df['Ship Date'] - df['Order Date']
).dt.days
```

This provides an additional measure that can be used to understand shipping duration.

---

### 6. Category Analysis

The dataset contains three major product categories:

* **Office Supplies**
* **Furniture**
* **Technology**

The total sales for each category are calculated using:

```python
category_sales = df.groupby('Category')['Sales'].sum()
```

### Category-wise Sales

| Category        | Total Sales |
| --------------- | ----------: |
| Technology      | $839,893.28 |
| Furniture       | $754,747.76 |
| Office Supplies | $731,893.31 |

The analysis shows that the three categories contribute substantially to the overall sales, with Technology having the highest total sales in this dataset.

---

## Visualizations

### 1. Sales by Category

A bar chart is created to compare total sales across product categories.

```python
category_sales.plot(
    kind='bar',
    figsize=(8,5)
)

plt.title("Sales by Category")
plt.ylabel("Total Sales")
plt.show()
```

This visualization makes it easier to compare the contribution of each product category to total sales.

---

### 2. Sales Distribution

A histogram is used to visualize the distribution of individual sales values.

```python
plt.figure(figsize=(8,5))

sns.histplot(
    df['Sales'],
    bins=30
)

plt.title("Sales Distribution")
plt.show()
```

The visualization helps understand how sales values are distributed across the dataset.

---

## Key Dataset Observations

Based on the analysis:

* The dataset contains **10,194 records**.
* There are **21 columns**.
* The dataset contains **3 product categories**.
* `Office Supplies` contains the largest number of records.
* `Technology` has the highest total sales among the three categories.
* The dataset does not contain missing values in the provided columns.
* Delivery duration ranges from **0 to 11 days**.
* The average delivery duration is approximately **3.96 days**.
* Sales values vary considerably, with some transactions having substantially higher sales amounts than the majority of records.

---

## Project Structure

```text
Superstore-Sales-Data-Analysis/
│
├── Superstore_Sales_Data_DV_Week_01(1).ipynb
│
├── superstore_sales_data_dv_week_01.py
│
├── samplesuperstore - samplesuperstore(1).csv
│
└── README.md
```

---

## How to Run the Project

### 1. Clone the Repository

```bash
git clone https://github.com/your-username/Superstore-Sales-Data-Analysis.git
```

### 2. Navigate to the Project Folder

```bash
cd Superstore-Sales-Data-Analysis
```

### 3. Install Required Libraries

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### 4. Run the Python File

```bash
python superstore_sales_data_dv_week_01.py
```

### Or Run the Jupyter Notebook

```bash
jupyter notebook
```

Then open:

```text
Superstore_Sales_Data_DV_Week_01(1).ipynb
```

---

## Future Improvements

The project can be further extended by adding:

* Monthly and yearly sales analysis
* Region-wise sales analysis
* State and city-wise sales analysis
* Sub-category performance analysis
* Profit and loss analysis
* Discount vs. profit analysis
* Ship mode analysis
* Customer segment analysis
* Sales and profit trend analysis
* Interactive dashboards using Power BI or Tableau

---

## Skills Demonstrated

This project demonstrates practical knowledge of:

* Data Loading
* Data Cleaning
* Data Preprocessing
* Exploratory Data Analysis
* Data Aggregation
* Date-Time Handling
* GroupBy Operations
* Statistical Analysis
* Data Visualization
* Python Programming
* Pandas
* NumPy
* Matplotlib
* Seaborn

---

## Conclusion

This project provides a basic exploratory analysis of the Superstore sales dataset using Python. It demonstrates how raw sales data can be inspected, transformed, analyzed, and visualized to identify useful patterns and summarize business-related information.

The project also provides a foundation for more advanced analysis, predictive modeling, and interactive dashboard development.

---


