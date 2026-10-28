# House Sales Data Analysis – Week 09

## Project Overview

This project focuses on cleaning and preprocessing house sales data using Python. It explores property-related information, handles missing and duplicate records, converts date values, creates new analytical features, and identifies potential outliers in house prices.

The project demonstrates essential data preprocessing and data quality techniques using Pandas, NumPy, and Python.

## Objectives

- Explore and understand the house sales dataset.
- Inspect dataset dimensions, columns, and statistical summaries.
- Identify missing values and duplicate records.
- Convert date values into a proper datetime format.
- Clean invalid and missing values in important numerical columns.
- Create new features related to property age and renovation history.
- Calculate price per square foot for living space and lot area.
- Detect potential house price outliers using the Interquartile Range (IQR) method.
- Export the cleaned dataset for further analysis.

## Dataset Description

The project uses the `kc_house_data.csv` dataset, which contains **21,613 records and 21 columns** before preprocessing.

### Important Dataset Columns

| Column | Description |
|---|---|
| id | Unique property identifier |
| date | Date of the house sale |
| price | Sale price of the house |
| bedrooms | Number of bedrooms |
| bathrooms | Number of bathrooms |
| sqft_living | Interior living area in square feet |
| sqft_lot | Total lot area in square feet |
| floors | Number of floors |
| waterfront | Indicates waterfront property status |
| view | Property view rating |
| condition | Overall property condition |
| grade | Overall construction and design grade |
| sqft_above | Area above ground level |
| sqft_basement | Basement area |
| yr_built | Year the property was built |
| yr_renovated | Year of renovation, if applicable |
| zipcode | Property ZIP code |
| lat | Latitude |
| long | Longitude |
| sqft_living15 | Living area of nearby properties |
| sqft_lot15 | Lot area of nearby properties |

## Technologies Used

- **Python** – Programming language
- **Pandas** – Data manipulation and cleaning
- **NumPy** – Numerical operations and conditional calculations
- **Matplotlib** – Data visualization library
- **Seaborn** – Statistical visualization library
- **Jupyter Notebook** – Interactive data analysis environment

## Project Workflow

### 1. Data Loading and Exploration

- Load the CSV dataset into a Pandas DataFrame.
- Display the first and last records.
- Inspect dataset information and dimensions.
- Examine column names and descriptive statistics.

### 2. Data Quality Checks

- Identify missing values in each column.
- Count duplicate records.
- Remove duplicate rows from the dataset.

### 3. Date Preprocessing

- Convert the sale date column into datetime format.
- Extract sale year, month, and day.
- Prepare date-related information for further analysis.

### 4. Numerical Data Cleaning

- Convert selected numerical columns into numeric data types.
- Remove records with missing values in price, living area, and lot area.
- Filter out records with non-positive prices, living areas, or lot areas.

### 5. Feature Engineering

Create additional features to support further analysis:

- `sale_year` – Year of the property sale.
- `sale_month` – Month of the property sale.
- `property_age` – Difference between the sale year and the construction year.
- `is_renovated` – Indicates whether the property has a recorded renovation year.
- `years_since_renovation` – Difference between the sale year and renovation year for renovated properties.
- `price_per_sqft_living` – House price divided by living area.
- `price_per_sqft_lot` – House price divided by lot area.

### 6. Outlier Detection

Use the Interquartile Range (IQR) method to identify potential outliers in house prices.

The method calculates the first quartile (Q1), third quartile (Q3), and interquartile range:

`IQR = Q3 - Q1`

Potential outliers are identified using these limits:

- Lower limit: `Q1 - 1.5 × IQR`
- Upper limit: `Q3 + 1.5 × IQR`

The program counts the house records whose prices fall outside these limits. These records are identified for analysis rather than automatically removed.

### 7. Final Validation and Export

- Display descriptive statistics after preprocessing.
- Check the final dataset dimensions.
- Review missing values in the processed dataset.
- Export the cleaned dataset as `House_Sales_Data_Cleaned_Week_09.csv`.

## Project Structure

```text
House-Sales-Data-Analysis/
|
|-- house_sales_data_dv_week_09.py
|-- House_Sales_Data_DV_Week_09.ipynb
|-- kc_house_data.csv
|-- House_Sales_Data_Cleaned_Week_09.csv
|-- README.md
```

The cleaned CSV file is generated when the Python program or notebook reaches the export step.

## Installation and Setup

### Prerequisites

Install Python and the required libraries before running the project.

### Step 1: Clone the Repository

```bash
git clone <your-repository-url>
cd House-Sales-Data-Analysis
```

### Step 2: Install Dependencies

```bash
pip install pandas numpy matplotlib seaborn jupyter
```

### Step 3: Run Using Jupyter Notebook

```bash
jupyter notebook
```

Open `House_Sales_Data_DV_Week_09.ipynb` and execute the cells sequentially.

### Step 4: Run the Python Script

Make sure the CSV file path points to the dataset in your local project directory.

Replace the Google Colab path:

```python
df = pd.read_csv("/content/kc_house_data.csv")
```

with:

```python
df = pd.read_csv("kc_house_data.csv")
```

Then execute:

```bash
python house_sales_data_dv_week_09.py
```

After successful execution, the cleaned dataset will be saved in the working directory as `House_Sales_Data_Cleaned_Week_09.csv`.

## Key Learning Outcomes

- Understanding real-world dataset structures.
- Performing data quality checks and preprocessing.
- Handling missing values and duplicate records.
- Converting and extracting date information.
- Applying feature engineering techniques.
- Calculating property-related metrics using numerical operations.
- Detecting potential outliers using statistical methods.
- Exporting processed data for future analysis.

## Future Enhancements

- Visualize house price distributions and outliers.
- Analyze price trends by year and month.
- Compare house prices by location, property size, and condition.
- Explore relationships between house prices and property features.
- Build an interactive dashboard using Plotly or Tableau.
- Develop a predictive model for house prices.

