# Student Performance Data Analysis – Week 08

## Project Overview

This project focuses on analyzing student performance data using Python and data visualization techniques. It explores students' mathematics, reading, and writing scores and examines how these scores vary based on parental education level, lunch type, and test preparation course.

The project uses Pandas, NumPy, Matplotlib, and Seaborn for data handling, statistical analysis, and visualization.

## Objectives

- Explore and understand the student performance dataset.
- Analyze mathematics, reading, and writing scores.
- Compare average exam scores based on parental education level.
- Examine score differences based on lunch type and test preparation course.
- Visualize relationships between the three subject scores.
- Understand correlations between mathematics, reading, and writing performance.

## Dataset Description

The dataset contains **1,000 student records and 8 columns**.

| Column | Description |
|---|---|
| gender | Student's gender |
| race/ethnicity | Student's group category |
| parental level of education | Parent's education level |
| lunch | Type of lunch |
| test preparation course | Test preparation status |
| math score | Mathematics exam score |
| reading score | Reading exam score |
| writing score | Writing exam score |

## Technologies Used

- **Python** – Programming language
- **Pandas** – Data manipulation and analysis
- **NumPy** – Numerical computing
- **Matplotlib** – Data visualization
- **Seaborn** – Statistical data visualization
- **Jupyter Notebook** – Interactive coding and analysis

## Data Analysis and Visualizations

### 1. Data Exploration
- Display the first and last few records.
- Check dataset information, shape, and column names.
- Explore unique values in categorical columns.
- Review descriptive statistics.

### 2. Grouped Bar Chart
Compare average mathematics, reading, and writing scores across different parental education levels.

### 3. Pair Plot
Visualize the relationships and distributions of mathematics, reading, and writing scores.

### 4. Correlation Heatmap
Display the correlation between the three subject scores using a heatmap.

### 5. Grouped Score Analysis
Calculate and compare average subject scores based on:
- Parental level of education
- Lunch type
- Test preparation course status

## Project Structure

```text
Student-Performance-Data-Analysis/
│
├── student_performance_data_dv_week_08.py
├── Student_Performance_Data_DV_Week_08.ipynb
├── StudentsPerformance(1).csv
└── README.md
```

## Installation and Setup

### Step 1: Clone the repository

```bash
git clone <your-repository-url>
cd Student-Performance-Data-Analysis
```

### Step 2: Install the required libraries

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### Step 3: Run the project

**Option 1: Jupyter Notebook**

```bash
jupyter notebook
```

Open `Student_Performance_Data_DV_Week_08.ipynb` and run the cells.

**Option 2: Python script**

Make sure the CSV file path in the Python script points to the dataset in your project folder. Then run:

```bash
python student_performance_data_dv_week_08.py
```

For a local setup, use:

```python
df = pd.read_csv("StudentsPerformance(1).csv")
```

## Key Outcomes

- Compared average scores across parental education categories.
- Examined score differences across lunch and test preparation groups.
- Explored relationships among mathematics, reading, and writing scores.
- Used correlation analysis to understand how subject scores are associated.

## Future Improvements

- Create an interactive dashboard using Plotly or Tableau.
- Add more visualizations for demographic comparisons.
- Develop a more detailed analysis of factors associated with student performance.
- Improve the presentation of findings with additional charts and insights.

