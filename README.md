# Data Analysis of Zameen.com Dataset

[GitHub Repository Link]

## Reading the CSV File
First, we read the data into a pandas DataFrame named 'zf':
```python
import pandas as p
zf = p.read_csv("zameen.csv")
```

## Analyzing the Data
We performed initial data exploration using the following methods:
- Viewed first 5 rows using `zf.head()`
- Viewed last 5 rows using `zf.tail()`
- Sampled 3 random rows using `zf.sample(3)`
- Generated data summary using `zf.describe()`
- Checked data types using `zf.info()`

## Data Filtering
The following operations were performed:
```python
# Removed duplicate entries
zf.drop_duplicates(inplace=True)

# Filtered houses only
zf[zf['property_type'] == 'House']

# Filtered properties under 10 million
zf[zf['price'] < 10000000]

# Renamed columns
zf.rename(columns={'page_url': 'URL', 'province_name': 'province'}, inplace=True)
```

## Data Cleaning
1. Checked for missing values using `zf.isnull().sum()`
2. Handled missing values:
   ```python
   zf['agency'].fillna(value="Not Mentioned", inplace=True)
   zf['agent'].fillna(value="Not Mentioned", inplace=True)
   ```
3. Dropped unnecessary columns:
   ```python
   zf.drop(columns=["Unnamed: 0", "purpose"], inplace=True)
   ```
4. Created grouped statistics using `groupby('province')`

## Data Visualization
Created various plots to visualize the data:
1. Bar plot of property types
2. Line plot of cities
3. Horizontal bar plot of provinces
4. Pie chart of area categories

## Data Export
Finally, saved the cleaned dataset:
```python
zf.to_csv("Zameen_Updated.csv", index=False)
```
