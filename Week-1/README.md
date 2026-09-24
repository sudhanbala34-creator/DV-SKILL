## Sample Superstore Sales Analysis

## Project Overview

This project analyzes the Sample Superstore dataset using Python in Google Colab. It performs data loading, cleaning, preprocessing, and exploratory data analysis (EDA) to understand sales performance across different product categories.

## Objectives

- Load and explore the Superstore dataset.
- Check the dataset structure and summary statistics.
- Convert date columns into the correct format.
- Calculate delivery time for each order.
- Check for missing values.
- Analyze total sales by product category.
- Visualize sales trends using charts.

## Technologies Used

- Python
- Google Colab
- Pandas
- NumPy
- Matplotlib
- Seaborn

## Dataset

File Name: "samplesuperstore.csv"

The dataset contains information such as:

- Order Date
- Ship Date
- Category
- Sales
- Customer Details
- Product Details
- Region
- Profit

## Steps Performed

1. Import Libraries

Imported the required Python libraries for data analysis and visualization.

2. Mount Google Drive

Connected Google Drive to access the dataset.

3. Load Dataset

Read the CSV file using Pandas.

4. Explore Data

- Displayed the first few rows.
- Checked dataset information.
- Generated descriptive statistics.

5. Data Preprocessing

- Converted Order Date and Ship Date to datetime format.
- Created a new column named Delivery Days by calculating the difference between Ship Date and Order Date.

6. Data Quality Check

- Identified unique product categories.
- Checked for missing values.

7. Sales Analysis

Calculated the total sales for each product category using the "groupby()" function.

8. Data Visualization

Created:

- Bar Chart showing total sales by category.
- Histogram showing the distribution of sales.

## Output

The project generates:

- Dataset summary
- Delivery Days calculation
- Sales by Category analysis
- Bar chart of category sales
- Histogram of sales distribution

## Conclusion

This project demonstrates basic data preprocessing and exploratory data analysis using the Sample Superstore dataset. It provides insights into category-wise sales performance and overall sales distribution using simple visualizations.
