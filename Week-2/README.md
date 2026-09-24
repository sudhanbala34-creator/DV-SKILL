#  SuperStore Sales Data Analysis

##  Project Overview

This project performs **Exploratory Data Analysis (EDA)** on a SuperStore sales dataset using Python.

The analysis focuses on understanding sales performance, customer segments, product categories, profitability, inventory levels, payment methods, delivery status, and delivery time.

The project is implemented using a **Google Colab / Jupyter Notebook** and uses Python data analysis and visualization libraries.

---

##  Objectives

The main objectives of this project are:

* Analyze SuperStore sales data
* Understand sales performance across different product categories
* Analyze profit and cost information
* Examine customer segments and regions
* Analyze inventory and reorder information
* Calculate delivery duration
* Identify missing values
* Generate statistical summaries
* Visualize sales performance using charts

---

##  Technologies Used

* **Python**
* **Pandas** – Data manipulation and analysis
* **NumPy** – Numerical operations
* **Matplotlib** – Data visualization
* **Seaborn** – Statistical data visualization
* **Google Colab** – Development environment

---

##  Dataset

The dataset contains **1,000 records** with **26 columns** before feature creation.

Important fields include:

| Column           | Description                     |
| ---------------- | ------------------------------- |
| Order ID         | Unique order identifier         |
| Order Date       | Date when the order was placed  |
| Ship Date        | Date when the order was shipped |
| Customer Name    | Customer name                   |
| Customer ID      | Unique customer identifier      |
| Customer Segment | Customer segment                |
| Category         | Product category                |
| Product Name     | Name of the product             |
| Product ID       | Unique product identifier       |
| Region           | Sales region                    |
| State            | Customer state                  |
| City             | Customer city                   |
| Quantity         | Quantity ordered                |
| Unit Price       | Price per unit                  |
| Discount (%)     | Discount applied                |
| Sales Amount     | Total sales amount              |
| Cost Price       | Product cost                    |
| Profit           | Profit generated                |
| Stock Left       | Remaining inventory             |
| Auto Reorder     | Reorder status                  |
| Reorder Quantity | Quantity to reorder             |
| Supplier Name    | Supplier information            |
| Supplier Email   | Supplier email                  |
| Payment Mode     | Payment method                  |
| Delivery Status  | Current delivery status         |
| Sales            | Sales value                     |

---

##  Data Analysis Process

### 1. Import Libraries

The project uses:

```python
import pandas as pd
import numpy as np
import matplotlib.pyplot as plt
import seaborn as sns
```

### 2. Load the Dataset

The dataset is loaded into a Pandas DataFrame.

```python
df = pd.read_csv("SuperStore.csv.csv")
```

### 3. Explore the Dataset

Initial exploration is performed using:

```python
df.head()
df.info()
df.describe()
```

The dataset contains:

* **1,000 rows**
* **26 original columns**
* Numerical and categorical features
* No missing values in the analyzed columns

### 4. Date Conversion

The `Order Date` and `Ship Date` columns are converted into datetime format.

```python
df['Order Date'] = pd.to_datetime(df['Order Date'])
df['Ship Date'] = pd.to_datetime(df['Ship Date'])
```

### 5. Delivery Time Analysis

A new feature called `Delivery Days` is created to calculate the number of days between ordering and shipping.

```python
df['Delivery Days'] = (
    df['Ship Date'] - df['Order Date']
).dt.days
```

### 6. Missing Value Analysis

Missing values are checked using:

```python
df.isnull().sum()
```

The analysis shows **0 missing values** across the dataset.

---

##  Sales Analysis

Sales are grouped by product category using:

```python
category_sales = (
    df.groupby('Category')['Sales Amount'].sum()
)
```

The analyzed categories are:

* Electronics
* Furniture
* Grocery
* Office Supplies

### Category Sales

| Category        | Sales Amount |
| --------------- | -----------: |
| Electronics     | 3,140,596.45 |
| Furniture       | 2,859,123.35 |
| Grocery         | 3,130,717.80 |
| Office Supplies | 3,196,907.70 |

A bar chart is also generated to visualize sales performance by category.

---

##  Visualizations

The notebook includes data visualization using Matplotlib and Seaborn.

Current analysis includes:

*  Sales by Category
*  Statistical analysis
*  Inventory-related analysis
*  Delivery-related analysis

---
## Data Visualisation

This project uses data visualization to convert the raw sales data into easy-to-understand graphs. Each graph focuses on a different aspect of the business, such as sales performance, profitability, and relationships between numerical variables.

1. Sales by Category
Graph Type: Bar Chart
<img width="691" height="560" alt="image" src="https://github.com/user-attachments/assets/b883a17d-c380-4ec5-bb61-d7b89c4505e1" />

<img width="695" height="470" alt="image" src="https://github.com/user-attachments/assets/c4730e90-cf8b-4be6-86d2-ad4e0ce82dad" />

This graph compares the total sales amount generated by each product category.

It shows which product categories generate the most sales.
It allows easy comparison between different categories.
Office Supplies has the highest total sales.
Furniture has the lowest total sales among the four categories.
Purpose
This graph helps identify the best-performing product categories in terms of sales.

2. Profit by Category
Graph Type: Bar Plot
<img width="580" height="455" alt="image" src="https://github.com/user-attachments/assets/6a5a6621-ca42-4d06-9ffe-0fb9da3afa08" />
<img width="589" height="455" alt="image" src="https://github.com/user-attachments/assets/444c4aa0-6590-4a0a-baf2-88eef60bd68f" />


This graph compares the profit generated by different product categories.

It shows how profitable each product category is.
It helps compare profitability rather than just sales.
A category having high sales does not necessarily mean it generates the highest profit.
The graph helps identify categories that contribute more to the company's overall profit.
Purpose
This graph helps understand which product categories are more profitable for the business.

3. Graph type: Box plot
<img width="589" height="455" alt="image" src="https://github.com/user-attachments/assets/291f16b7-1605-43e4-9a23-dbd87be9a055" />
<img width="589" height="455" alt="image" src="https://github.com/user-attachments/assets/7848ed03-5cbf-4aa9-83eb-b1c47bdfd496" />

What it shows: Profit distribution broken down per category, instead of the single combined box in Chart 5.

Explanation: This lets you compare not just average profit (as in Chart 3) but also consistency. A category with a tall box (wide IQR) has unpredictable profit from order to order, while a category with a short, tight box earns more consistent profit per sale. Outlier dots above any box highlight categories that occasionally produce exceptionally profitable orders.


4.Scatter plot
<img width="589" height="455" alt="image" src="https://github.com/user-attachments/assets/dc009d69-5be3-48a0-bbf7-6882fb988552" />


What it shows: Each point is a single order, plotted by the discount percentage it received against the profit earned.

Explanation: The correlation between Discount (%) and Profit in the correlation matrix is -0.08, which is very close to zero. This scatter plot visually confirms that finding: the points don't form a clear downward (or upward) trend — discounts in this dataset (0%, 5%, 10%, 15%, 20%) don't have a strong linear effect on profit. Profit is driven far more by order size (Quantity, Unit Price) than by the discount applied.

5.Correlation Heatmap
Graph Type: Correlation Heatmap
<img width="632" height="540" alt="image" src="https://github.com/user-attachments/assets/b3aa0722-ed41-449a-b6ad-21bff44b3481" />


The correlation heatmap shows the relationships between numerical variables such as:

Quantity
Unit Price
Discount
Sales Amount
Cost Price
Profit
Stock Left
Reorder Quantity
Sales
Delivery Days
The heatmap shows whether two variables have a positive, negative, or weak relationship.

Some important relationships found in the dataset are:

Sales Amount and Cost Price have a very strong positive relationship.
Sales Amount and Profit have a strong positive relationship.
Stock Left and Reorder Quantity have a negative relationship.
Delivery Days and Sales have almost no relationship.
Purpose
This graph helps identify patterns and relationships between different numerical variables and can reveal which factors are closely associated with sales, profit, and inventory.

Overall Explanation
Visualization	What it explains
Sales by Category	Which categories generate the most sales
Profit by Category	Which categories generate more profit
Correlation Heatmap	How numerical variables are related to each other
Together, these visualizations provide a clearer understanding of the dataset by showing sales performance, profitability, and relationships between important business variables

##  Key Dataset Statistics

Some important numerical statistics from the dataset:

| Metric       |   Average |
| ------------ | --------: |
| Quantity     |     5.385 |
| Unit Price   |  2,589.46 |
| Discount     |    9.855% |
| Sales Amount | 12,327.35 |
| Cost Price   |  9,317.24 |
| Profit       |  3,010.10 |
| Stock Left   |     25.61 |

The maximum recorded sales amount is **47,481**, while the maximum recorded profit is **15,935.91**.

---

##  Project Structure

```text
SuperStore-Sales-Analysis/
│
├── SuperStore_Sales_Analysis.ipynb
├── SuperStore.csv
└── README.md
```

---

## How to Run the Project

### Option 1: Google Colab

1. Upload the `.ipynb` file to Google Colab.
2. Upload the `SuperStore.csv` dataset.
3. Update the dataset path if required.
4. Run the notebook cells sequentially.

### Option 2: Jupyter Notebook

Install the required libraries:

```bash
pip install pandas numpy matplotlib seaborn
```

Then open the notebook:

```bash
jupyter notebook
```

Run the cells from top to bottom.

---

##  Insights

The analysis provides an overview of:

* Category-wise sales performance
* Profitability
* Product pricing
* Customer information
* Inventory levels
* Reordering information
* Payment methods
* Delivery status
* Delivery duration

The project demonstrates how Python can be used to transform raw sales data into useful business insights.

---

##  Future Improvements

The project can be extended by adding:

* Monthly and yearly sales trends
* Region-wise sales analysis
* Customer segment analysis
* Top-performing products
* Profit by category
* Delivery status visualization
* Payment mode analysis
* Inventory and reorder analysis
* Correlation analysis
* Interactive dashboards using **Power BI** or **Plotly**

---

##  Author

**Bala Suthan J**

BCA Student

---

