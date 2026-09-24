## WEEK 5

# Healthcare Dataset Analysis

# Healthcare Dataset Analysis

## Project Overview

This project performs basic **data cleaning and analysis** on a healthcare dataset using Python and Pandas in Google Colab.

The dataset contains patient details, medical conditions, admission information, billing amounts, and discharge dates.

## Dataset

The dataset contains:

* 500 patient records
* 9 columns

### Columns

* Patient_ID
* Gender
* Age
* Medical_Condition
* Admission_Date
* Admission_Type
* Medical_Code
* Billing_Amount
* Discharge_Date

## Technologies Used

* Python
* Pandas
* Matplotlib
* Seaborn
* Google Colab

## Data Cleaning

The following data-cleaning operations were performed:

1. Loaded the healthcare dataset using Pandas.
2. Checked the first and last records.
3. Checked column names and data types.
4. Checked the dataset size.
5. Checked for missing values.
6. Replaced missing `Medical_Code` values with `"Unknown"`.
7. Converted `Admission_Date` and `Discharge_Date` into datetime format.
8. Cleaned `Admission_Type` using `strip()` and `lower()`.

The dataset initially contained 15 missing values in the `Medical_Code` column.

## Data Analysis

### 1. Admission Type Analysis

The number of patients for each admission type was calculated using `value_counts()`.

* Routine: 196
* Emergency: 188
* Urgent: 116

### 2. Billing Amount Analysis

Statistical analysis was performed on the `Billing_Amount` column.

| Measure            |    Value |
| ------------------ | -------: |
| Count              |      500 |
| Mean               | 7249.001 |
| Standard Deviation | 3198.969 |
| Minimum            |     2300 |
| Q1                 |     4400 |
| Median             |     6950 |
| Q3                 |     9400 |
| Maximum            |    14200 |

These values were calculated using the Pandas `describe()` function.

### 3. Hospital Stay Analysis

A new column called `Hospital_Stay_Days` was created by calculating the difference between admission date and discharge date.

```python
df["Hospital_Stay_Days"] = (
    df["Discharge_Date"] - df["Admission_Date"]
).dt.days
```

The hospital-stay statistics were calculated using `describe()`.

* Average stay: 2.744 days
* Minimum stay: 1 day
* Maximum stay: 10 days
* Median stay: 2 days

### 4. Medical Condition and Gender Analysis

A cross-tabulation was created using:

```python
pd.crosstab(
    df["Medical_Condition"],
    df["Gender"]
)
```

This shows the number of male and female patients for each medical condition.

## Objectives

The main objectives of this project are:

* Understand the healthcare dataset.
* Identify and handle missing values.
* Clean categorical data.
* Convert date columns into proper date format.
* Calculate hospital stay duration.
* Analyze billing amounts using statistical measures.
* Compare medical conditions by gender.
* Practice basic data analysis using Pandas.

## Project Structure

```text
Healthcare-Dataset-Analysis/
│
├── healthcare_dataset.csv
├── Healthcare_Analysis.ipynb
└── README.md
```

## How to Run

1. Open Google Colab.
2. Upload the notebook.
3. Upload `healthcare_dataset.csv`.
4. Run the cells from top to bottom.
5. View the outputs and analysis.

## Conclusion

This project demonstrates how Python and Pandas can be used to perform basic healthcare data cleaning, statistical analysis, and data exploration. It also shows how to calculate hospital stay duration and analyze relationships between medical conditions and gender.
