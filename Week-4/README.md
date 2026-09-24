## WEEK 4

# Healthcare Dataset Analysis

## Project Overview

This project performs basic data cleaning and analysis on a healthcare dataset using Python and Pandas in Google Colab.

The dataset contains information about patients, their medical conditions, admission details, medical codes, billing amounts, and discharge dates.

## Dataset

The dataset contains:

* 500 rows
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

The following operations were performed:

1. Loaded the healthcare dataset using Pandas.
2. Checked the dataset using `head()` and `tail()`.
3. Checked column names and data types.
4. Checked the number of rows and columns.
5. Checked missing values.
6. Replaced missing `Medical_Code` values with `Unknown`.
7. Converted admission and discharge dates into datetime format.
8. Cleaned `Admission_Type` using `strip()` and `lower()`.

There were 15 missing values in the `Medical_Code` column before cleaning.

## Data Analysis

### Admission Type

The admission types were analyzed using `value_counts()`.

* Routine: 196
* Emergency: 188
* Urgent: 116

### Billing Amount

The `Billing_Amount` column was analyzed using statistical measures such as:

* Mean
* Standard deviation
* Minimum
* Maximum
* Quartiles
* Median

### Hospital Stay

Hospital stay duration was calculated using the admission date and discharge date.

```python
df["Hospital_Stay_Days"] = (
    df["Discharge_Date"] - df["Admission_Date"]
).dt.days
```

### Medical Condition and Gender

A cross-tabulation was used to analyze the relationship between medical conditions and gender.

```python
pd.crosstab(
    df["Medical_Condition"],
    df["Gender"]
)
```

## Objectives

* Understand the healthcare dataset.
* Clean and prepare the data.
* Handle missing values.
* Convert date columns into the correct format.
* Analyze admission types.
* Analyze billing amounts.
* Calculate hospital stay duration.
* Analyze medical conditions based on gender.

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
2. Upload the `.ipynb` notebook.
3. Upload `healthcare_dataset.csv`.
4. Run the notebook cells in order.
5. View the results and analysis.

## Conclusion

This project demonstrates basic healthcare data analysis using Python and Pandas. It covers data cleaning, mi
