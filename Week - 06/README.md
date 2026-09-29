# Healthcare Data Analysis & Visualization — Week 06

A Python-based **Healthcare Data Analysis and Visualization** project using the Healthcare dataset to analyze billing amounts across medical conditions and insurance providers.

This project builds on basic healthcare data preprocessing and statistical analysis by introducing **advanced data visualization techniques**, including stacked bar charts and violin plots.

---

## Project Overview

The project analyzes healthcare billing data to understand how billing amounts vary across:

* Medical Conditions
* Insurance Providers

The analysis includes:

* Data loading and exploration
* Missing value handling
* Date preprocessing
* Admission urgency categorization
* Hospital stay calculation
* Billing statistics
* Demographic analysis
* Gender distribution
* Medical condition-wise billing analysis
* Insurance provider-wise billing analysis
* Stacked bar visualization
* Violin plot visualization

The project is implemented using **Python, Pandas, NumPy, Matplotlib, and Seaborn**.

---

## Objectives

The main objectives of this project are:

1. To explore and understand the healthcare dataset.
2. To clean and preprocess the data.
3. To handle missing values.
4. To standardize admission and discharge dates.
5. To categorize admissions based on urgency.
6. To calculate hospital stay duration.
7. To analyze billing amount statistics.
8. To analyze patient demographics.
9. To examine gender distribution across medical conditions.
10. To compare billing amounts across medical conditions and insurance providers.
11. To visualize billing distributions using stacked bar charts and violin plots.

---

## Dataset

The project uses a healthcare dataset containing patient, medical, admission, insurance, billing, and hospital information.

### Main Dataset Columns

| Column               | Description                        |
| -------------------- | ---------------------------------- |
| `Name`               | Patient name                       |
| `Age`                | Patient age                        |
| `Gender`             | Patient gender                     |
| `Blood Type`         | Patient blood type                 |
| `Medical Condition`  | Patient's medical condition        |
| `Date of Admission`  | Date of hospital admission         |
| `Doctor`             | Doctor associated with the patient |
| `Hospital`           | Hospital name                      |
| `Insurance Provider` | Insurance provider                 |
| `Billing Amount`     | Patient billing amount             |
| `Room Number`        | Hospital room number               |
| `Admission Type`     | Type of admission                  |
| `Discharge Date`     | Date of discharge                  |
| `Medication`         | Medication information             |
| `Test Results`       | Patient test result                |

---

## Technologies Used

* **Python**
* **Pandas**
* **NumPy**
* **Matplotlib**
* **Seaborn**
* **Jupyter Notebook / Google Colab**

---

# Data Analysis Process

## 1. Importing Libraries

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

---

## 2. Loading the Dataset

The healthcare dataset is loaded using Pandas.

```python
df = pd.read_csv("healthcare_dataset(2).csv")
```

The dataset is then inspected using:

```python
print(df.head())
print(df.shape)
print(df.describe())
```

---

## 3. Missing Value Analysis

Missing values are identified using:

```python
print(df.isnull().sum())
```

Missing records are removed using:

```python
df = df.dropna()
```

The project also ensures that records without a medical condition are removed:

```python
df = df.dropna(subset=["Medical Condition"])
```

---

## 4. Date Preprocessing

The admission and discharge date columns are converted into datetime format:

```python
df["Date of Admission"] = pd.to_datetime(
    df["Date of Admission"]
)

df["Discharge Date"] = pd.to_datetime(
    df["Discharge Date"]
)
```

This allows the project to calculate hospital stay duration.

---

## 5. Admission Urgency Categorization

The `Admission Type` column is converted into an `Urgency` classification.

The three categories are:

* Emergency
* Urgent
* Elective

```python
df["Urgency"] = df["Admission Type"].map({
    "Emergency": "Emergency",
    "Urgent": "Urgent",
    "Elective": "Elective"
})
```

---

## 6. Hospital Stay Calculation

A new column called `Stay_Days` is created.

```python
df["Stay_Days"] = (
    df["Discharge Date"] -
    df["Date of Admission"]
).dt.days
```

This represents the number of days between admission and discharge.

---

## 7. Billing Statistics

Summary statistics are calculated for patient billing amounts.

```python
print("Billing Statistics:")
print(df["Billing Amount"].describe())
```

This provides information such as:

* Count
* Mean
* Standard deviation
* Minimum
* Maximum
* Quartiles
* Median

---

## 8. Hospital Stay Statistics

Summary statistics are also calculated for hospital stay duration.

```python
print("\nHospital Stay Statistics:")
print(df["Stay_Days"].describe())
```

This helps understand the distribution and variation of hospital stay durations.

---

## 9. Demographic Analysis

The number of patients and average age are calculated for each medical condition.

```python
print("\nDemographics:")
print(
    df.groupby("Medical Condition")["Age"]
    .agg(["count", "mean"])
)
```

This provides a basic demographic comparison across medical conditions.

---

## 10. Gender Distribution

Gender distribution is analyzed across medical conditions using a cross-tabulation.

```python
print("\nGender Distribution:")
print(
    pd.crosstab(
        df["Medical Condition"],
        df["Gender"]
    )
)
```

---

# Visualizations

## 1. Billing Amount by Medical Condition and Insurance Provider

The project first groups billing amounts by:

* Medical Condition
* Insurance Provider

```python
billing_data = df.groupby(
    ['Medical Condition', 'Insurance Provider']
)['Billing Amount'].sum().unstack(fill_value=0)
```

A **stacked bar chart** is then created:

```python
billing_data.plot(
    kind='bar',
    stacked=True,
    figsize=(12, 6)
)

plt.title(
    'Billing Amount by Medical Condition and Insurance Provider'
)

plt.xlabel('Medical Condition')
plt.ylabel('Total Billing Amount')

plt.xticks(rotation=45)
plt.legend(title='Insurance Provider')

plt.tight_layout()
plt.show()
```

### Purpose

This visualization helps compare total billing amounts across different medical conditions while showing the contribution of each insurance provider.

---

# 2. Violin Plot — Billing by Medical Condition

A violin plot is used to visualize the distribution of billing amounts for each medical condition.

```python
plt.figure(figsize=(12, 6))

sns.violinplot(
    data=df,
    x='Medical Condition',
    y='Billing Amount'
)

plt.title(
    'Billing Amount Distribution by Medical Condition'
)

plt.xlabel('Medical Condition')
plt.ylabel('Billing Amount')

plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```

### Purpose

The violin plot helps visualize:

* Distribution
* Spread
* Density
* Variation of billing amounts

across different medical conditions.

---

# 3. Violin Plot — Billing by Insurance Provider

The project also analyzes billing amount distribution across insurance providers.

```python
plt.figure(figsize=(12, 6))

sns.violinplot(
    data=df,
    x='Insurance Provider',
    y='Billing Amount'
)

plt.title(
    'Billing Amount Distribution by Insurance Provider'
)

plt.xlabel('Insurance Provider')
plt.ylabel('Billing Amount')

plt.xticks(rotation=45)
plt.tight_layout()
plt.show()
```

### Purpose

This visualization helps compare the distribution and variation of billing amounts across different insurance providers.

---

# Analysis Summary

| Analysis                          | Technique Used                  |
| --------------------------------- | ------------------------------- |
| Dataset Inspection                | `head()`, `shape`, `describe()` |
| Missing Values                    | `isnull().sum()`                |
| Data Cleaning                     | `dropna()`                      |
| Date Processing                   | `pd.to_datetime()`              |
| Admission Categorization          | `map()`                         |
| Hospital Stay                     | Date Difference                 |
| Billing Statistics                | `describe()`                    |
| Demographic Analysis              | `groupby()`                     |
| Gender Analysis                   | `crosstab()`                    |
| Billing by Condition & Insurance  | GroupBy + Stacked Bar           |
| Billing Distribution by Condition | Violin Plot                     |
| Billing Distribution by Insurance | Violin Plot                     |

---

# Project Structure

```text
Healthcare-Data-Visualization/
│
├── Healthcare_Data_DV_Week_06.ipynb
│
├── healthcare_data_dv_week_06.py
│
├── healthcare_dataset(2).csv
│
└── README.md
```

---

# How to Run the Project

## 1. Clone the Repository

```bash
git clone https://github.com/your-username/Healthcare-Data-Visualization.git
```

## 2. Navigate to the Project Folder

```bash
cd Healthcare-Data-Visualization
```

## 3. Install Required Libraries

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

## 4. Run the Python Program

```bash
python healthcare_data_dv_week_06.py
```

## 5. Run the Jupyter Notebook

```bash
jupyter notebook
```

Then open:

```text
Healthcare_Data_DV_Week_06.ipynb
```

---

# Key Learning Outcomes

Through this project, the following concepts are practiced:

* Python Data Analysis
* Pandas DataFrames
* NumPy
* Data Cleaning
* Missing Value Handling
* Date-Time Conversion
* Data Transformation
* GroupBy Operations
* Cross-Tabulation
* Statistical Analysis
* Stacked Bar Charts
* Violin Plots
* Healthcare Data Analysis
* Data Visualization

---

# Future Improvements

The project can be extended with:

* Interactive healthcare dashboards
* Admission trends over time
* Hospital-wise billing analysis
* Billing amount comparison by admission type
* Urgency-wise billing analysis
* Age-group analysis
* Medication-wise analysis
* Test-result analysis
* Medical condition trends
* Geographic healthcare analysis
* Power BI or Tableau dashboard

---

# Conclusion

The **Healthcare Data Analysis & Visualization — Week 06** project demonstrates how Python visualization techniques can be used to analyze healthcare billing data.

The project combines data preprocessing and statistical analysis with visual techniques such as **stacked bar charts and violin plots** to examine billing amounts across medical conditions and insurance providers.

It provides practical experience in using **Pandas for data manipulation, Matplotlib and Seaborn for visualization, and Python for healthcare data analysis**.

---
