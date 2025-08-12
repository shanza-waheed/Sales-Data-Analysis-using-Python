# Python_Project_Sales_Analysis_ Report

### Project Overview

The project uses the `pandas`, `numpy`, `matplotlib`, and `seaborn` libraries to load, clean, and visualize a dataset containing sales information. The analysis focuses on understanding demographics such as gender, age, marital status, state, and occupation, and how these factors relate to sales, orders, and product categories.

-----

### Data Preparation and Cleaning

The analysis began with the following data cleaning and preparation steps:

  * **Data Loading**: The `Diwali Sales Data.csv` file was loaded into a pandas DataFrame.
  * **Column Removal**: Unnecessary columns, `Status` and `unnamed1`, were removed.
  * **Missing Values**: Null values were identified and dropped from the dataset to ensure data integrity.
  * **Data Type Conversion**: The `Amount` column was converted from a floating-point data type to an integer data type, as it represents a monetary value.

-----

### Key Findings from Exploratory Data Analysis (EDA)

The analysis yielded several key insights into customer behavior:

#### Gender

  * The majority of **buyers are females**, and they have a significantly higher purchasing power compared to men.

#### Age

  * The most active buyers are **females in the 26-35 age group**.

#### State

  * The highest number of orders and total sales amount came from **Uttar Pradesh, Maharashtra, and Karnataka**.

#### Marital Status

  * **Married women** are the most frequent buyers and demonstrate the highest purchasing power.

#### Occupation

  * Customers working in the **IT, Healthcare, and Aviation** sectors were the most frequent buyers.

#### Product Category

  * The most sold products belonged to the **Food, Clothing, and Electronics** categories.

-----

### Conclusion

Based on the analysis, a clear profile of the most likely buyer emerged:

**Married women aged 26-35, from Uttar Pradesh, Maharashtra, and Karnataka, working in the IT, Healthcare, or Aviation sectors, are most likely to buy products from the Food, Clothing, and Electronics categories during Diwali.**

This conclusion provides valuable insights for targeted marketing and inventory management strategies.
