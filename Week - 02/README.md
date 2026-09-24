# Superstore Sales Data Analysis & Visualization — Week 02

A Python-based **Data Analysis and Data Visualization** project using the Superstore Sales dataset.

This project focuses on exploring sales and profit data and creating different types of visualizations to understand category-wise performance, profit distribution, discount impact, and relationships between numerical variables.

---

## Project Overview

The project uses the **Superstore Sales dataset** to perform exploratory data analysis and visualization using Python.

The analysis starts with basic data inspection and preprocessing, followed by multiple visualization techniques:

* Bar Plots
* Box Plots
* Scatter Plot
* Correlation Heatmap
* Sales Distribution
* Date and Delivery Analysis
* Category-wise Sales and Profit Analysis

The project is implemented using **Pandas, NumPy, Matplotlib, and Seaborn**.

---

## Objectives

The main objectives of this project are:

1. To explore and understand the Superstore Sales dataset.
2. To perform basic data preprocessing.
3. To convert date columns into the appropriate datetime format.
4. To calculate delivery duration.
5. To analyze sales and profit across product categories.
6. To understand profit distribution and variation.
7. To analyze the relationship between discount and profit.
8. To identify relationships between numerical variables using correlation.
9. To create meaningful visualizations using Matplotlib and Seaborn.

---

## Dataset

The dataset contains **10,194 records and 21 columns**.

### Dataset Columns

| Column           | Description                     |
| ---------------- | ------------------------------- |
| `Row ID`         | Unique row identifier           |
| `Order ID`       | Unique order identifier         |
| `Order Date`     | Date when the order was placed  |
| `Ship Date`      | Date when the order was shipped |
| `Ship Mode`      | Shipping method                 |
| `Customer ID`    | Unique customer identifier      |
| `Customer Name`  | Customer name                   |
| `Segment`        | Customer segment                |
| `Country/Region` | Country or region               |
| `City`           | Customer city                   |
| `State/Province` | Customer state or province      |
| `Postal Code`    | Postal code                     |
| `Region`         | Sales region                    |
| `Product ID`     | Product identifier              |
| `Category`       | Product category                |
| `Sub-Category`   | Product sub-category            |
| `Product Name`   | Product name                    |
| `Sales`          | Sales amount                    |
| `Quantity`       | Quantity ordered                |
| `Discount`       | Discount applied                |
| `Profit`         | Profit generated                |

---

## Technologies Used

* Python
* Pandas
* NumPy
* Matplotlib
* Seaborn
* Jupyter Notebook / Google Colab

---

# Data Analysis

## 1. Importing Libraries

The following Python libraries are used for data analysis and visualization:

```python
import pandas as pd
import numpy as np

import matplotlib.pyplot as plt
import seaborn as sns
```

---

## 2. Loading the Dataset

The Superstore dataset is loaded using Pandas.

```python
df = pd.read_csv("samplesuperstore - samplesuperstore.csv")
```

---

## 3. Exploring the Dataset

The following functions are used to understand the dataset:

```python
df.head()
df.info()
df.describe()
```

### Functions Used

* `head()` — displays the first few records.
* `info()` — provides information about columns and data types.
* `describe()` — provides statistical information about numerical columns.

---

## 4. Date Preprocessing

The `Order Date` and `Ship Date` columns are converted into datetime format.

```python
df['Order Date'] = pd.to_datetime(df['Order Date'])
df['Ship Date'] = pd.to_datetime(df['Ship Date'])
```

This allows date-based calculations to be performed correctly.

---

## 5. Delivery Days Calculation

A new column named `Delivery Days` is created using the difference between shipping date and order date.

```python
df['Delivery Days'] = (
    df['Ship Date'] - df['Order Date']
).dt.days
```

This helps analyze the number of days between order placement and shipping.

---

## 6. Category Analysis

The dataset contains three product categories:

* Furniture
* Office Supplies
* Technology

The unique categories are identified using:

```python
df['Category'].unique()
```

Missing values are also checked using:

```python
df.isnull().sum()
```

The provided dataset contains **no missing values** across the analyzed columns.

---

# Visualizations

## Part 1 — Bar Plots

Bar plots are used to compare sales and profit across categories.

The project specifically analyzes:

* Profit by Category
* Sales by Category

The notebook describes bar plots as a method for comparing sales and profit across categories, regions, and products.

### Profit by Category

```python
sns.barplot(
    data=df,
    x="Category",
    y="Profit"
)

plt.title("Profit by Category")
plt.show()
```

### Sales by Category

```python
sns.barplot(
    data=df,
    x="Category",
    y="Sales"
)

plt.title("Sales Distribution by Category")
plt.show()
```

### Category-wise Summary

| Category        |       Sales |      Profit |
| --------------- | ----------: | ----------: |
| Furniture       | $754,747.76 |  $19,730.00 |
| Office Supplies | $731,893.31 | $126,023.44 |
| Technology      | $839,893.28 | $146,543.38 |

---

# Part 2 — Box Plots

Box plots are used to understand:

* Data distribution
* Median
* Outliers
* Variation

These are the purposes specified in the project notebook.

### Overall Profit Distribution

```python
sns.boxplot(
    data=df,
    y="Profit"
)

plt.title("Profit Distribution")
plt.show()
```

### Profit Variation Across Categories

```python
sns.boxplot(
    data=df,
    x="Category",
    y="Profit"
)

plt.title("Profit Variation Across Categories")
plt.show()
```

These visualizations help examine how profit values are distributed and how their variation differs across categories.

---

# Part 3 — Discount vs Profit Analysis

The project analyzes the relationship between **Discount** and **Profit**.

The purpose is to investigate whether discounts are associated with changes in profitability. The notebook frames this as examining whether discounts improve sales or reduce profitability.

### Checking Discount Values

```python
df["Discount"].unique()
```

### Scatter Plot

```python
sns.scatterplot(
    data=df,
    x="Discount",
    y="Profit"
)

plt.title("Impact of Discount on Profit")
plt.show()
```

The scatter plot helps visualize how profit values are distributed at different discount levels.

---

# Part 4 — Correlation Heatmap

Correlation is used to understand the relationship between numerical variables.

The project first selects numerical columns:

```python
numeric_df = df.select_dtypes(
    include="number"
)
```

Then calculates the correlation matrix:

```python
corr = numeric_df.corr()
```

Finally, a heatmap is created:

```python
sns.heatmap(
    corr,
    annot=True
)

plt.title("Correlation Heatmap")
plt.show()
```

The correlation heatmap provides a visual representation of relationships among the numerical variables in the dataset.

---

# Key Analysis Areas

This project covers the following major areas:

| Analysis                         | Visualization / Method |
| -------------------------------- | ---------------------- |
| Sales by Category                | Bar Plot               |
| Profit by Category               | Bar Plot               |
| Overall Profit Distribution      | Box Plot               |
| Profit Variation by Category     | Box Plot               |
| Discount vs Profit               | Scatter Plot           |
| Numerical Variable Relationships | Correlation Heatmap    |
| Sales Distribution               | Histogram              |
| Delivery Duration                | Date Difference        |
| Missing Value Analysis           | `isnull().sum()`       |

---

# Project Structure

```text
Superstore-Sales-Data-Visualization/
│
├── Superstore_Sales_Data_DV_Week_02.ipynb
│
├── superstore_sales_data_dv_week_02.py
│
├── samplesuperstore - samplesuperstore(2).csv
│
└── README.md
```

---

# How to Run the Project

## Step 1 — Clone the Repository

```bash
git clone https://github.com/your-username/Superstore-Sales-Data-Visualization.git
```

## Step 2 — Open the Project Folder

```bash
cd Superstore-Sales-Data-Visualization
```

## Step 3 — Install Required Libraries

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

## Step 4 — Run the Python File

```bash
python superstore_sales_data_dv_week_02.py
```

### Or Run the Jupyter Notebook

```bash
jupyter notebook
```

Then open:

```text
Superstore_Sales_Data_DV_Week_02.ipynb
```

---

# Key Learning Outcomes

Through this project, the following concepts are practiced:

* Python for Data Analysis
* Pandas DataFrame operations
* NumPy
* Data Inspection
* Data Preprocessing
* Date-Time Conversion
* GroupBy Operations
* Data Aggregation
* Bar Charts
* Box Plots
* Scatter Plots
* Histograms
* Correlation Analysis
* Heatmaps
* Exploratory Data Analysis

---

# Future Improvements

The project can be extended with additional analysis such as:

* Monthly and yearly sales trends
* Region-wise sales and profit analysis
* State and city-wise analysis
* Sub-category analysis
* Customer segment analysis
* Shipping mode analysis
* Profit margin analysis
* Discount impact analysis
* Sales and profit trend visualization
* Interactive dashboards using Power BI or Tableau

---

# Conclusion

The **Superstore Sales Data Analysis & Visualization — Week 02** project demonstrates how Python can be used to explore a real-world sales dataset and communicate insights through different visualization techniques.

The project progresses from basic data exploration to more detailed visual analysis using **bar plots, box plots, scatter plots, and correlation heatmaps**.

It provides practical experience in understanding data distributions, comparing categories, exploring relationships between variables, and presenting analytical results visually.

---



