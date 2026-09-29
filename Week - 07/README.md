# Student Performance Data Analysis – Data Visualization Week 07

## Project Overview

This project focuses on analyzing **student academic performance** using Python and data analysis techniques.

The dataset contains information about students' demographic and academic details, including **gender, race/ethnicity, parental level of education, lunch type, test preparation course, and scores in Mathematics, Reading, and Writing**.

The analysis explores the structure and quality of the dataset, calculates descriptive statistics, creates overall student performance metrics, and identifies potential **outliers in Mathematics scores**.

---

## Objectives

The main objectives of this project are:

* Explore the Student Performance dataset
* Understand the structure and characteristics of the data
* Check for missing values
* Check for duplicate records
* Analyze Mathematics, Reading, and Writing scores
* Calculate descriptive statistics
* Calculate the total score for each student
* Calculate the percentage of each student
* Identify potential outliers in Mathematics scores using the IQR method

---

## Technologies Used

* **Python**
* **Pandas** – Data loading, manipulation, and analysis
* **NumPy** – Numerical operations
* **Matplotlib** – Data visualization
* **Seaborn** – Statistical visualization
* **Jupyter Notebook / Google Colab**

---

## Dataset

The project uses the **StudentsPerformance.csv** dataset.

### Dataset Details

| Property          | Details |
| ----------------- | ------- |
| Number of Records | 1,000   |
| Number of Columns | 8       |
| Missing Values    | None    |
| Duplicate Records | None    |

### Dataset Columns

| Column                        | Description                      |
| ----------------------------- | -------------------------------- |
| `gender`                      | Gender of the student            |
| `race/ethnicity`              | Race or ethnicity group          |
| `parental level of education` | Parent's highest education level |
| `lunch`                       | Type of lunch provided           |
| `test preparation course`     | Test preparation course status   |
| `math score`                  | Mathematics score                |
| `reading score`               | Reading score                    |
| `writing score`               | Writing score                    |

---

## Data Exploration

The dataset was initially explored using:

* `head()` – To view the first few records
* `tail()` – To view the last few records
* `describe()` – To obtain statistical summaries
* `shape` – To identify the number of rows and columns
* `info()` – To understand column data types and dataset structure
* `isnull().sum()` – To check missing values
* `duplicated().sum()` – To check duplicate records

The analysis confirmed that the dataset contains **1,000 records and 8 columns**, with no missing values or duplicate records.

---

## Score Analysis

The following three academic score columns were selected for detailed analysis:

```python
score_columns = ['math score', 'reading score', 'writing score']
```

Descriptive statistics were calculated for these three subjects, including:

* Count
* Mean
* Standard deviation
* Minimum
* 25th percentile
* Median
* 75th percentile
* Maximum

### Score Summary

| Subject     | Mean Score | Minimum | Maximum |
| ----------- | ---------: | ------: | ------: |
| Mathematics |      66.09 |       0 |     100 |
| Reading     |      69.17 |      17 |     100 |
| Writing     |      68.05 |      10 |     100 |

The analysis shows that **Reading has the highest average score among the three subjects** in this dataset.

---

## Total Score Calculation

A new column called **`Total Score`** was created by adding the Mathematics, Reading, and Writing scores.

```python
df["Total Score"] = (
    df["math score"]
    + df["reading score"]
    + df["writing score"]
)
```

The total score represents the student's combined performance across all three subjects.

The maximum possible total score is **300**.

---

## Percentage Calculation

A new **`Percentage`** column was calculated from the total score.

```python
df["Percentage"] = (df["Total Score"] / 300) * 100
```

This converts the combined score into a percentage based on a maximum score of 300.

The average percentage across the dataset is approximately **67.77%**.

---

## Outlier Detection

The project also identifies potential outliers in **Mathematics scores** using the **Interquartile Range (IQR)** method.

The following steps were used:

1. Calculate the first quartile (**Q1**)
2. Calculate the third quartile (**Q3**)
3. Calculate the Interquartile Range:

```python
IQR = Q3 - Q1
```

4. Define the lower and upper boundaries:

```text
Lower Boundary = Q1 - 1.5 × IQR
Upper Boundary = Q3 + 1.5 × IQR
```

5. Identify Mathematics scores outside these boundaries.

The number of detected Mathematics outliers is then displayed using:

```python
print(f"Number of outliers in math score: {len(outliers)}")
```

---

## Analysis Workflow

```text
Load Dataset
     ↓
Explore Dataset
     ↓
Check Shape & Information
     ↓
Check Missing Values
     ↓
Check Duplicate Records
     ↓
Analyze Subject Scores
     ↓
Calculate Descriptive Statistics
     ↓
Calculate Total Score
     ↓
Calculate Percentage
     ↓
Detect Mathematics Score Outliers
```

---

## Project Structure

```text
Student-Performance-Data-DV-Week-07/
│
├── Student_Performance_Data_DV_Week_07.ipynb
├── student_performance_data_dv_week_07.py
├── StudentsPerformance.csv
└── README.md
```

---

## How to Run the Project

### 1. Clone the Repository

```bash
git clone <your-repository-link>
```

### 2. Open the Project Folder

```bash
cd Student-Performance-Data-DV-Week-07
```

### 3. Install Required Libraries

```bash
pip install pandas numpy matplotlib seaborn
```

### 4. Run the Python Program

Make sure the CSV file is in the same folder as the Python file.

For GitHub/local execution, you can use:

```python
df = pd.read_csv("StudentsPerformance.csv")
```

> **Note:** Your current `.py` file uses the Google Colab path `/content/StudentsPerformance.csv`. When running the project locally or directly from the GitHub repository, use the local CSV filename instead.

### 5. Run the Jupyter Notebook

Open:

```text
Student_Performance_Data_DV_Week_07.ipynb
```

and execute the cells sequentially.

---

## Key Findings

Based on the dataset analysis:

* The dataset contains **1,000 student records**.
* There are **8 attributes** in the original dataset.
* No missing values were found.
* No duplicate records were found.
* The average Mathematics score is approximately **66.09**.
* The average Reading score is approximately **69.17**.
* The average Writing score is approximately **68.05**.
* Reading has the highest average score among the three subjects.
* A `Total Score` column was created by combining all three subject scores.
* A `Percentage` column was calculated using the total score.
* Mathematics scores were analyzed for potential outliers using the IQR method.

The dataset exploration, score analysis, total score calculation, percentage calculation, and outlier detection are implemented in the Week 07 Python program.

---

## Learning Outcomes

Through this project, the following concepts were practiced:

* Reading CSV files using Pandas
* Dataset exploration
* Data structure inspection
* Missing value detection
* Duplicate detection
* Descriptive statistical analysis
* Column selection
* Creating calculated columns
* Percentage calculation
* Quartile analysis
* Interquartile Range (IQR)
* Outlier detection
* Basic data analysis using Python

---

## Future Improvements

The project can be further extended by adding:

* Subject-wise performance visualizations
* Gender-based score comparison
* Performance comparison by parental education
* Test preparation course analysis
* Lunch type and academic performance analysis
* Correlation analysis between subjects
* Distribution plots for Mathematics, Reading, and Writing scores
* Additional statistical and visual analysis

---

## Conclusion

This Week 07 project demonstrates the use of **Python and Pandas for student performance analysis**.

The analysis begins with basic dataset exploration and data-quality checks, followed by statistical analysis of Mathematics, Reading, and Writing scores. Additional performance metrics such as **Total Score** and **Percentage** are created, while the **IQR method** is used to identify potential Mathematics score outliers.

Overall, the project provides practical experience in **data exploration, descriptive statistics, calculated fields, and outlier detection using Python**.

---
