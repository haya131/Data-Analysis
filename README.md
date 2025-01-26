# Readme
# Haya Muazzam 
# SU92-BSAIM-F24-058
# Quality of Life Dataset - Pandas Exploration

This document provides an in-depth explanation of the Python script used for analyzing the `quality_of_life_dataset.csv` file using Pandas. Below is a step-by-step guide to each operation performed in the script.

---

## 1. Importing Libraries and Dataset 

```python
import pandas as pd

df = pd.read_csv("quality_of_life_dataset.csv")
```
- **Purpose**: Load the dataset into a Pandas DataFrame.
- **Dataset**: Contains columns such as `Country`, `Income_Level_USD`, `Health_Index`, etc.

---

## 2. Previewing the Dataset

### Display the DataFrame
```python
df
```
- Displays the entire DataFrame.

### First and Last Few Rows
```python
df.head()
df.tail()
```
- `df.head()`: Shows the first 5 rows.
- `df.tail()`: Shows the last 5 rows.

---

## 3. Dataset Statistics

### Descriptive Statistics
```python
df.describe()
```
- Outputs summary statistics for numerical columns, including:
  - **Mean**
  - **Standard Deviation**
  - **Min and Max Values**

### DataFrame Shape and Types
```python
df.shape


df.dtypes


df.info()

```
- **Significance**: Highlights the number of rows, columns, and missing data.

---

## 4. Working with Columns

### Accessing Columns
```python
df['Crime_Rate']  
df[['Crime_Rate', 'Working_Hours_Week']]  
df.columns  
```

### Renaming Columns
```python
df.rename(columns={'Working_Hours_Week': 'Working_Hours'}, inplace=True)
```
- Renames the column `Working_Hours_Week` to `Working_Hours`.

---

## 5. Handling Missing Data

### Identifying Missing Values
```python
df.isnull().sum()
```
- Checks for missing values in each column.

### Dropping Missing Data
```python
df.dropna(axis=1)  
df.dropna(axis=0) 
```

---

## 6. Filtering and Subsetting Data

### Filter Rows
```python
df[df['Country'].isin(['USA', 'Canada'])]
```
- Filters rows where the `Country` is either `USA` or `Canada`.

### Dropping Columns
```python
df.drop(columns=['Country'], inplace=True)
```
- Removes the `Country` column.

---

## 7. Working with Duplicates

### Checking and Removing Duplicates
```python
df.duplicated().sum() 
df.drop_duplicates(inplace=True)  
```

---

## 8. Sorting Data

### Single Column Sorting
```python
df.sort_values(by='Income_Level_USD', ascending=True)
```
- Sorts by `Income_Level_USD` in ascending order.

### Multiple Column Sorting
```python
df.sort_values(by=['Happiness_Score', 'Income_Level_USD'], ascending=[True, False])
```
- Sorts by `Happiness_Score` (ascending) and `Income_Level_USD` (descending).

---

## 9. Grouping Data

### Grouping and Aggregating
```python
df.groupby('Access_Clean_Water')['Income_Level_USD'].mean()
```
- Groups rows by `Access_Clean_Water` and calculates the mean `Income_Level_USD` for each group.

---

### 10. Importing Libraries
Before working with Pandas, import the required libraries:
```python
import pandas as pd
import matplotlib.pyplot as plt
```

### 11. Sorting Values
#### By Single Column (`Income_Level_USD`):
Sort the DataFrame based on income levels.
```python
df.sort_values(by='Income_Level_USD', inplace=True)
```

#### By Multiple Columns (`Happiness_Score` and `Income_Level_USD`):
Sort the DataFrame based on happiness score and income level in ascending order.
```python
df.sort_values(by=['Happiness_Score', 'Income_Level_USD'], inplace=True)
```

---

### 12. Setting an Index
Set the country as the index of the DataFrame.
```python
df.set_index('Country', inplace=True)
```

---

### 13. Visualization

#### Bar Plot:
Plot happiness scores for each country as a vertical bar chart.
```python
df['Happiness_Score'].plot(kind='bar')
plt.show()
```

#### Horizontal Bar Plot:
Plot happiness scores as a horizontal bar chart.
```python
df['Happiness_Score'].plot(kind='barh')
plt.show()
```

#### Scatter Plot:
Show the relationship between income levels and happiness scores.
```python
df.plot(kind='scatter', x='Income_Level_USD', y='Happiness_Score')
plt.show()
```

#### Histogram:
Visualize the distribution of the health index.
```python
df['Health_Index'].plot(kind='hist')
plt.show()
```

#### Box Plot:
Display the distribution of crime rates.
```python
df['Crime_Rate'].plot(kind='box')
plt.show()
```

#### Box Plot (Multiple Columns):
Compare income levels and health indices.
```python
df[['Income_Level_USD', 'Health_Index']].plot(kind='box')
plt.show()
```

#### Line Plot:
Plot income levels against happiness scores.
```python
df.plot(kind='line', x='Income_Level_USD', y='Happiness_Score')
plt.show()
```

#### Area Plot:
Visualize the trend of happiness scores.
```python
df.plot(kind='area', x='Income_Level_USD', y='Happiness_Score')
plt.show()
```

#### Pie Chart:
Show the distribution of access to clean water.
```python
df['Access_Clean_Water'].value_counts().plot(kind='pie')
plt.show()
```

#### Hexbin Plot:
Visualize density between income levels and happiness scores.
```python
df.plot(kind='hexbin', x='Income_Level_USD', y='Happiness_Score', gridsize=25)
plt.show()
```

#### KDE Plot:
Visualize the density distribution of the health index.
```python
df['Health_Index'].plot(kind='kde')
plt.show()
```

#### Scatter Matrix:
Create a matrix of scatter plots for all numerical columns.
```python
pd.plotting.scatter_matrix(df, figsize=(10, 6), diagonal='hist')
plt.show()
```

---

### 14. Pivot Table
Create a pivot table summarizing happiness scores by country and access to clean water.
```python
df.pivot_table(index='Country', columns='Access_Clean_Water', values='Happiness_Score', aggfunc='mean')
```

---

### 15. Reset Index
Reset the DataFrame index to default numeric indexing.
```python
df.reset_index(inplace=True)
```

---

### Usage Notes
- Always ensure you have the necessary libraries installed (`pandas` and `matplotlib`).
- Use `inplace=True` for methods like `sort_values` and `reset_index` to modify the original DataFrame.
- Use `plt.show()` to render visualizations in your environment.


## Summary

- The dataset contains **10 rows** and **11 columns**.
- Columns like `Access_Clean_Water` and `Internet_Access` are entirely missing.
- Pandas operations help efficiently clean, filter, and analyze the data.