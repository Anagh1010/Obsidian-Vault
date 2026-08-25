---
tags:
  - pandas
  - python
  - datascience
  - cheatsheet
---

# 🐼 Pandas Quick Reference Guide

> [!INFO] Summary
> Essential Pandas methods and syntax for data exploration, indexing, filtering, and visualization.

---

## 1. Initial Data Inspection

```python
# Show the top N rows (Default: 5) - Works on Series & DataFrames
df.head(n=5)

# Show the bottom N rows (Default: 5) - Works on Series & DataFrames
df.tail(n=5)

# Get dimensions as a tuple: (rows, columns)
# Pass 0 for rows count, 1 for columns count
df.shape
df.shape[0]  # Row count
df.shape[1]  # Column count

# Column summary, non-null counts, & data types (useful for identifying missing values)
df.info()

# Summary statistics for numerical columns (count, mean, std, min, 25%, 50%, 75%, max)
df.describe()
```

---

## 2. Selecting Columns & Indexing

| Syntax | Description | Return Type |
| :--- | :--- | :--- |
| `df['col_name']` | Selects a single column | `pd.Series` |
| `df[['col1', 'col2', 'col3']]` | Selects multiple columns | `pd.DataFrame` |

---

## 3. Position-Based Selection (`iloc`)

```python
# Single row selection by index position
df.iloc[0]  # Returns Series

# Multiple rows selection by list of indices
df.iloc[[0, 1, 2]]  # Returns DataFrame

# Slicing rows: [start_row : end_row_exclusive : step]
df.iloc[0:5:1]

# Slicing both rows AND columns: [row_slice, col_slice]
df.iloc[0:10:1, 0:3:1]
```

---

## 4. Conditional Filtering (Boolean Masking)

```python
# Create a boolean Series (True/False evaluation)
mask = df['column_name'] > 50

# Apply mask to filter DataFrame rows
df[mask]

# Combine multiple conditions using logical operators:
# & (AND), | (OR), ~ (NOT)
mask1 = df['col1'] == 'Value'
mask2 = df['col2'] >= 100

df[mask1 & mask2]
```

---

## 5. Value Counts & Series Properties

```python
# Count unique values in a column (returns a Series)
df['col_name'].value_counts()

# Extract only the unique categorical labels (index of the series)
myseries = df['col_name'].value_counts()
myseries.index

# Direct Visualization (Requires matplotlib.pyplot)
import matplotlib.pyplot as plt

df['col_name'].value_counts().plot(kind='bar')
plt.show()
```

---

## 6. Sorting Data

```python
# Sort by a single column
df.sort_values(by='col_name', ascending=False, inplace=True)

# Sort by multiple columns with independent sort orders
df.sort_values(
    by=['col1', 'col2'], 
    ascending=[False, True], 
    inplace=True
)
```

> [!TIP]
> Setting `inplace=True` modifies the original DataFrame directly without needing to reassign it (`df = df.sort_values(...)`).
