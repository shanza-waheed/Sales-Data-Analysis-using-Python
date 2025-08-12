# Python_Project_of_Sales_Analysis

```python?code_reference&code_event_index=2
import json

with open("Diwali_Sales_Analysis.ipynb", "r", encoding='utf-8') as f:
    notebook_content = json.load(f)

cells = notebook_content.get("cells", [])

code_cells = [cell['source'] for cell in cells if cell['cell_type'] == 'code']
markdown_cells = [cell['source'] for cell in cells if cell['cell_type'] == 'markdown']

print("Code Cells:")
for i, code in enumerate(code_cells):
    print(f"--- Code Cell {i+1} ---")
    print("".join(code))

print("\nMarkdown Cells:")
for i, markdown in enumerate(markdown_cells):
    print(f"--- Markdown Cell {i+1} ---")
    print("".join(markdown))
```

```text?code_stdout&code_event_index=2
Code Cells:
--- Code Cell 1 ---
# import python libraries

import numpy as np 
import pandas as pd 
import matplotlib.pyplot as plt # visualizing data
%matplotlib inline
import seaborn as sns
--- Code Cell 2 ---
# import csv file
df = pd.read_csv('Diwali Sales Data.csv', encoding= 'unicode_escape')
--- Code Cell 3 ---
df.shape
--- Code Cell 4 ---
df.head()
--- Code Cell 5 ---
df.info()
--- Code Cell 6 ---
#drop unrelated/blank columns
df.drop(['Status', 'unnamed1'], axis=1, inplace=True)
--- Code Cell 7 ---
#check for null values
pd.isnull(df).sum()
--- Code Cell 8 ---
# drop null values
df.dropna(inplace=True)
--- Code Cell 9 ---
# change data type
df['Amount'] = df['Amount'].astype('int')
--- Code Cell 10 ---
df['Amount'].dtypes
--- Code Cell 11 ---
df.columns
--- Code Cell 12 ---
#rename column
df.rename(columns= {'Marital_Status':'Shaadi'})
--- Code Cell 13 ---
# describe() method returns description of the data in the DataFrame (i.e. count, mean, std, etc)
df.describe()
--- Code Cell 14 ---
# use describe() for specific columns
df[['Age', 'Orders', 'Amount']].describe()
--- Code Cell 15 ---
# plotting a bar chart for Gender and it's count

ax = sns.countplot(x = 'Gender',data = df)

for bars in ax.containers:
    ax.bar_label(bars)
--- Code Cell 16 ---
# plotting a bar chart for gender vs total amount

sales_gen = df.groupby(['Gender'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False)

sns.barplot(x = 'Gender',y= 'Amount' ,data = sales_gen)
--- Code Cell 17 ---
ax = sns.countplot(data = df, x = 'Age Group', hue = 'Gender')

for bars in ax.containers:
    ax.bar_label(bars)
--- Code Cell 18 ---
# Total Amount vs Age Group
sales_age = df.groupby(['Age Group'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False)

sns.barplot(x = 'Age Group',y= 'Amount' ,data = sales_age)
--- Code Cell 19 ---
# total number of orders from top 10 states

sales_state = df.groupby(['State'], as_index=False)['Orders'].sum().sort_values(by='Orders', ascending=False).head(10)

sns.set(rc={'figure.figsize':(15,5)})
sns.barplot(data = sales_state, x = 'State',y= 'Orders')
--- Code Cell 20 ---
# total amount/sales from top 10 states

sales_state = df.groupby(['State'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False).head(10)

sns.set(rc={'figure.figsize':(15,5)})
sns.barplot(data = sales_state, x = 'State',y= 'Amount')
--- Code Cell 21 ---
ax = sns.countplot(data = df, x = 'Marital_Status')

sns.set(rc={'figure.figsize':(7,5)})
for bars in ax.containers:
    ax.bar_label(bars)
--- Code Cell 22 ---
sales_state = df.groupby(['Marital_Status', 'Gender'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False)

sns.set(rc={'figure.figsize':(6,5)})
sns.barplot(data = sales_state, x = 'Marital_Status',y= 'Amount', hue='Gender')
--- Code Cell 23 ---
sns.set(rc={'figure.figsize':(20,5)})
ax = sns.countplot(data = df, x = 'Occupation')

for bars in ax.containers:
    ax.bar_label(bars)
--- Code Cell 24 ---
sales_state = df.groupby(['Occupation'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False)

sns.set(rc={'figure.figsize':(20,5)})
sns.barplot(data = sales_state, x = 'Occupation',y= 'Amount')
--- Code Cell 25 ---
sns.set(rc={'figure.figsize':(20,5)})
ax = sns.countplot(data = df, x = 'Product_Category')

for bars in ax.containers:
    ax.bar_label(bars)
--- Code Cell 26 ---
sales_state = df.groupby(['Product_Category'], as_index=False)['Amount'].sum().sort_values(by='Amount', ascending=False).head(10)

sns.set(rc={'figure.figsize':(20,5)})
sns.barplot(data = sales_state, x = 'Product_Category',y= 'Amount')
--- Code Cell 27 ---
sales_state = df.groupby(['Product_ID'], as_index=False)['Orders'].sum().sort_values(by='Orders', ascending=False).head(10)

sns.set(rc={'figure.figsize':(20,5)})
sns.barplot(data = sales_state, x = 'Product_ID',y= 'Orders')
--- Code Cell 28 ---
# top 10 most sold products (same thing as above)

fig1, ax1 = plt.subplots(figsize=(12,7))
df.groupby('Product_ID')['Orders'].sum().nlargest(10).sort_values(ascending=False).plot(kind='bar')

Markdown Cells:
--- Markdown Cell 1 ---
# Exploratory Data Analysis
--- Markdown Cell 2 ---
### Gender
--- Markdown Cell 3 ---
*From above graphs we can see that most of the buyers are females and even the purchasing power of females are greater than men*
--- Markdown Cell 4 ---
### Age
--- Markdown Cell 5 ---
*From above graphs we can see that most of the buyers are of age group between 26-35 yrs female*
--- Markdown Cell 6 ---
### State
--- Markdown Cell 7 ---
*From above graphs we can see that most of the orders & total sales/amount are from Uttar Pradesh, Maharashtra and Karnataka respectively*

--- Markdown Cell 8 ---
### Marital Status
--- Markdown Cell 9 ---
*From above graphs we can see that most of the buyers are married (women) and they have high purchasing power*
--- Markdown Cell 10 ---
### Occupation
--- Markdown Cell 11 ---
*From above graphs we can see that most of the buyers are working in IT, Healthcare and Aviation sector*
--- Markdown Cell 12 ---
### Product Category
--- Markdown Cell 13 ---
*From above graphs we can see that most of the sold products are from Food, Clothing and Electronics category*
--- Markdown Cell 14 ---
## Conclusion:

### 
--- Markdown Cell 15 ---
*Married women age group 26-35 yrs from UP,  Maharastra and Karnataka working in IT, Healthcare and Aviation are more likely to buy products from Food, Clothing and Electronics category*
--- Markdown Cell 16 ---
Thank you!

```

## Sales Analysis Report
-----

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
