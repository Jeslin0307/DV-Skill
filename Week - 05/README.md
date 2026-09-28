# Healthcare Data Analysis & Visualization — Week 05

A Python-based **Healthcare Data Analysis** project that performs data cleaning, preprocessing, statistical analysis, admission categorization, hospital stay analysis, and demographic analysis using a healthcare dataset.

---

## Project Overview

This project analyzes a healthcare dataset containing patient information, medical conditions, admission details, billing amounts, and hospital stay information.

The analysis focuses on:

* Cleaning missing values
* Standardizing date attributes
* Categorizing admissions by urgency
* Calculating hospital stay duration
* Analyzing patient billing amounts
* Analyzing hospital stay statistics
* Segmenting patient demographics by medical condition
* Analyzing gender distribution across medical conditions

The project is implemented using **Python, Pandas, NumPy, and Matplotlib**.

---

## Objectives

The main objectives of this project are:

1. To load and understand the healthcare dataset.
2. To inspect the structure and statistical characteristics of the data.
3. To identify and handle missing values.
4. To standardize admission and discharge date attributes.
5. To categorize admissions into Emergency, Urgent, and Elective.
6. To calculate the number of hospital stay days.
7. To calculate summary statistics for billing amounts.
8. To calculate summary statistics for hospital stays.
9. To analyze patient demographics based on medical conditions.
10. To examine gender distribution across medical conditions.

---

## Dataset

The healthcare dataset contains **55,500 records and 15 columns**.

### Dataset Columns

| Column               | Description                            |
| -------------------- | -------------------------------------- |
| `Name`               | Patient name                           |
| `Age`                | Patient age                            |
| `Gender`             | Patient gender                         |
| `Blood Type`         | Patient blood type                     |
| `Medical Condition`  | Patient's medical condition            |
| `Date of Admission`  | Date of hospital admission             |
| `Doctor`             | Doctor associated with the patient     |
| `Hospital`           | Hospital name                          |
| `Insurance Provider` | Insurance provider                     |
| `Billing Amount`     | Patient billing amount                 |
| `Room Number`        | Hospital room number                   |
| `Admission Type`     | Type of admission                      |
| `Discharge Date`     | Date of discharge                      |
| `Medication`         | Medication associated with the patient |
| `Test Results`       | Patient test result                    |

---

## Technologies Used

* **Python**
* **Pandas**
* **NumPy**
* **Matplotlib**
* **Jupyter Notebook / Google Colab**

---

# Data Analysis Process

## 1. Importing Libraries

The project uses Pandas and NumPy for data processing and Matplotlib for visualization.

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
```

---

## 2. Loading the Dataset

The healthcare dataset is loaded using Pandas.

```python
df = pd.read_csv("healthcare_dataset(1).csv")
```

The dataset is then displayed for initial inspection.

```python
df
```

---

## 3. Initial Data Exploration

The following operations are used to understand the dataset:

```python
print(df.head())
print(df.shape)
print(df.describe())
```

### Purpose

* `head()` → displays the first few records.
* `shape` → identifies the number of rows and columns.
* `describe()` → provides statistical information about numerical columns.

---

## 4. Missing Value Analysis

Missing values are checked using:

```python
print(df.isnull().sum())
```

The dataset is then cleaned using:

```python
df = df.dropna()
```

The project also specifically ensures that records without a medical condition are removed:

```python
df = df.dropna(subset=["Medical Condition"])
```

---

## 5. Date Preprocessing

The admission and discharge date columns are converted into datetime format.

```python
df["Date of Admission"] = pd.to_datetime(
    df["Date of Admission"]
)

df["Discharge Date"] = pd.to_datetime(
    df["Discharge Date"]
)
```

This allows the project to perform date-based calculations accurately.

---

# Admission Urgency Categorization

The `Admission Type` column is mapped into an `Urgency` column.

The project categorizes admissions into:

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

This creates a standardized urgency classification for the admissions.

---

# Hospital Stay Analysis

A new column named `Stay_Days` is created by calculating the difference between the discharge date and admission date.

```python
df["Stay_Days"] = (
    df["Discharge Date"] -
    df["Date of Admission"]
).dt.days
```

This allows the project to analyze the duration of hospital stays.

---

# Billing Amount Analysis

Summary statistics are calculated for the `Billing Amount` column.

```python
print("Billing Statistics:")
print(df["Billing Amount"].describe())
```

The dataset's billing amount statistics include:

| Statistic          |     Value |
| ------------------ | --------: |
| Count              |    55,500 |
| Mean               | 25,539.32 |
| Standard Deviation | 14,211.45 |
| Minimum            | -2,008.49 |
| 25th Percentile    | 13,241.22 |
| Median             | 25,538.07 |
| 75th Percentile    | 37,820.51 |
| Maximum            | 52,764.28 |

---

# Hospital Stay Statistics

Summary statistics are calculated for the newly created `Stay_Days` column.

```python
print("\nHospital Stay Statistics:")
print(df["Stay_Days"].describe())
```

This provides information such as:

* Number of records
* Average hospital stay
* Minimum stay
* Maximum stay
* Median stay
* Quartiles
* Variation in hospital stay duration

---

# Demographic Analysis

Patient demographics are analyzed based on medical conditions.

The project groups patients by `Medical Condition` and calculates:

* Number of patients
* Average age

```python
print("\nDemographics:")
print(
    df.groupby("Medical Condition")["Age"]
    .agg(["count", "mean"])
)
```

### Medical Conditions in the Dataset

The dataset contains the following medical conditions:

* Arthritis
* Diabetes
* Hypertension
* Obesity
* Cancer
* Asthma

---

# Gender Distribution

Gender distribution is analyzed across different medical conditions using a cross-tabulation.

```python
print("\nGender Distribution:")
print(
    pd.crosstab(
        df["Medical Condition"],
        df["Gender"]
    )
)
```

This allows comparison of the number of male and female patients across different medical conditions.

---

# Dataset Summary

| Feature              |                       Value |
| -------------------- | --------------------------: |
| Total Records        |                      55,500 |
| Total Columns        |                          15 |
| Admission Types      |                           3 |
| Medical Conditions   |                           6 |
| Missing Values       |                           0 |
| Admission Categories | Emergency, Urgent, Elective |

### Admission Type Distribution

| Admission Type | Records |
| -------------- | ------: |
| Elective       |  18,655 |
| Urgent         |  18,576 |
| Emergency      |  18,269 |

### Medical Condition Distribution

| Medical Condition | Records |
| ----------------- | ------: |
| Arthritis         |   9,308 |
| Diabetes          |   9,304 |
| Hypertension      |   9,245 |
| Obesity           |   9,231 |
| Cancer            |   9,227 |
| Asthma            |   9,185 |

---

# Analysis Areas

| Analysis                       | Method Used                     |
| ------------------------------ | ------------------------------- |
| Dataset Inspection             | `head()`, `shape`, `describe()` |
| Missing Value Analysis         | `isnull().sum()`                |
| Missing Value Handling         | `dropna()`                      |
| Date Standardization           | `pd.to_datetime()`              |
| Admission Categorization       | `map()`                         |
| Hospital Stay Calculation      | Date Difference                 |
| Billing Analysis               | `describe()`                    |
| Hospital Stay Statistics       | `describe()`                    |
| Medical Condition Demographics | `groupby()`                     |
| Gender Distribution            | `crosstab()`                    |

---

# Project Structure

```text
Healthcare-Data-Analysis/
│
├── Healthcare_Data_DV_Week_05.ipynb
│
├── healthcare_data_dv_week_05.py
│
├── healthcare_dataset(1).csv
│
└── README.md
```

---

# How to Run the Project

## 1. Clone the Repository

```bash
git clone https://github.com/your-username/Healthcare-Data-Analysis.git
```

## 2. Navigate to the Project Folder

```bash
cd Healthcare-Data-Analysis
```

## 3. Install Required Libraries

```bash
pip install pandas numpy matplotlib jupyter
```

## 4. Run the Python Program

```bash
python healthcare_data_dv_week_05.py
```

## 5. Run the Jupyter Notebook

```bash
jupyter notebook
```

Then open:

```text
Healthcare_Data_DV_Week_05.ipynb
```

---

# Key Learning Outcomes

This project provides practical experience with:

* Python programming
* Pandas DataFrames
* Data cleaning
* Missing value handling
* Date-time preprocessing
* Data transformation
* Data aggregation
* GroupBy operations
* Cross-tabulation
* Statistical analysis
* Healthcare data analysis
* Exploratory Data Analysis

---

# Future Improvements

The project can be extended by adding:

* Medical condition-wise billing visualization
* Admission urgency visualization
* Hospital-wise patient analysis
* Billing amount distribution
* Hospital stay distribution
* Age-group analysis
* Medication-wise analysis
* Test result analysis
* Admission trends over time
* Interactive healthcare dashboards using Power BI or Tableau

---

# Conclusion

The **Healthcare Data Analysis — Week 05** project demonstrates how Python can be used to clean, preprocess, and analyze healthcare data.

The project transforms raw healthcare records into useful analytical information by handling missing values, standardizing dates, categorizing admission urgency, calculating hospital stay duration, summarizing billing amounts, and analyzing patient demographics.

This project provides practical experience in applying **Pandas-based data analysis techniques to a healthcare dataset**.

---
