# House Sales Data Visualization and Analysis

## About the Project

This project focuses on analyzing and visualizing house sales data using Python. It explores the relationship between house prices and various property features such as living area, property grade, waterfront availability, and geographical location.

The project uses data analysis and visualization techniques to understand housing price patterns.

## Objectives

- Analyze house sales data using Python.
- Perform data cleaning and preprocessing.
- Understand the relationship between living area and house prices.
- Compare property prices based on property grades.
- Analyze house prices with and without waterfront access.
- Visualize geographical property price distribution.

## Dataset

**Dataset Name:** KC House Sales Dataset

**File Name:** `kc_house_data.csv`

**Total Records:** 21,613

**Total Columns:** 21

### Important Features

- `price` – House selling price
- `bedrooms` – Number of bedrooms
- `bathrooms` – Number of bathrooms
- `sqft_living` – Living area in square feet
- `grade` – Overall property grade
- `waterfront` – Waterfront availability
- `lat` – Latitude
- `long` – Longitude

## Technologies Used

- Python
- Pandas
- NumPy
- Matplotlib
- Seaborn
- Google Colab
- Jupyter Notebook

## Data Preprocessing

The following preprocessing techniques were performed:

1. Loaded the dataset using Pandas.
2. Inspected the dataset using `head()`, `tail()`, `info()`, and `describe()`.
3. Removed unnecessary spaces from column names.
4. Converted selected columns into numeric data types.
5. Handled missing values by removing incomplete records.
6. Removed records with non-positive house prices and living areas.

## Data Visualizations

### 1. Living Area vs Property Price
A regression plot is used to analyze the relationship between living area and house prices.

### 2. Price Distribution Across Property Grades
A box plot is used to compare house prices across different property grades.

### 3. Price by Waterfront Status
A box plot compares prices of waterfront and non-waterfront properties.

### 4. Geographic Property Price Distribution
A scatter plot displays geographical property locations using latitude and longitude, with colors representing house prices.

## Project Structure

```text
House-Sales-Data-Visualization/
│
├── README.md
├── kc_house_data.csv
├── house_sales_data_dv_week_10.py
└── House_Sales_Data_DV_Week_10.ipynb
```

## Installation and Execution

### Step 1: Clone the Repository

```bash
git clone https://github.com/your-username/House-Sales-Data-Visualization.git
```

### Step 2: Install Required Libraries

```bash
pip install pandas numpy matplotlib seaborn
```

### Step 3: Load the Dataset

Place `kc_house_data.csv` in the project directory.

### Step 4: Run the Project

Open the `.ipynb` file using Google Colab or Jupyter Notebook and execute all cells.

For running the Python script locally, update the dataset path to:

```python
df = pd.read_csv("kc_house_data.csv")
```

Then execute:

```bash
python house_sales_data_dv_week_10.py
```

## Key Insights

- Living area is an important factor to explore when analyzing house prices.
- Property grades help compare property price distributions.
- Waterfront availability provides another factor for price comparison.
- Geographical visualization helps identify property price variations across locations.

## Project Details

- **Project Name:** House Sales Data Visualization and Analysis
- **Week:** Week 10
- **Domain:** Data Analytics
- **Category:** Data Visualization
- **Language:** Python
