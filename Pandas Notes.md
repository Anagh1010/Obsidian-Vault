# Pandas

## 1. Inspecting Data

### `df.head(<n>)`

Shows the first `n` rows of the dataset.

- Default: `n = 5`
- Works on both **DataFrame** and **Series**.

```python
df.head()
df.head(10)
```

---

### `df.tail(<n>)`

Shows the last `n` rows of the dataset.

- Default: `n = 5`
- Works on both **DataFrame** and **Series**.

```python
df.tail()
df.tail(10)
```

---

### `df.shape`

Returns the number of rows and columns as a tuple.

```python
df.shape
# (number_of_rows, number_of_columns)
```

Individual dimensions can be accessed using indexing:

```python
df.shape[0]    # Number of rows
df.shape[1]    # Number of columns
```

---

### `df.info()`

Displays information about the DataFrame, including:

- Number of rows
- Column names
- Number of non-null values in each column
- Data type of each column
- Memory usage

It is useful for identifying **missing values** because it shows the number of non-null values in every column.

```python
df.info()
```

---

### `df.describe()`

Returns descriptive statistics for numerical columns by default.

It includes:

- `count` → Number of non-null values
- `mean` → Mean
- `std` → Standard deviation
- `min` → Minimum value
- `25%` → First quartile
- `50%` → Median
- `75%` → Third quartile
- `max` → Maximum value

```python
df.describe()
```

---

# 2. Selecting Columns

## Selecting a Single Column

### `df['column_name']`

Selects a single column from the DataFrame.

The result is a **Series**.

```python
df['column_name']
```

Example:

```python
df['Age']
```

---

## Selecting Multiple Columns

### `df[['col1', 'col2', 'col3']]`

Selects multiple columns.

The result is a **DataFrame**.

```python
df[['col1', 'col2', 'col3']]
```

> **Important:** Double square brackets are required when selecting multiple columns.

---

# 3. Selecting Rows

## `df.iloc[]`

`iloc` is used for **integer-position based indexing**.

The positions start from `0`.

### Selecting a Single Row

```python
df.iloc[2]
```

Returns the row at integer position `2`.

The result is a **Series**.

### Selecting Multiple Specific Rows

```python
df.iloc[[1, 3, 5]]
```

Returns rows at positions `1`, `3`, and `5`.

The result is a **DataFrame**.

### Selecting a Range of Rows

```python
df.iloc[min_row_index : max_row_index + 1 : step_size]
```

Example:

```python
df.iloc[1:5]
```

Selects rows:

```text
1, 2, 3, 4
```

The ending index is **exclusive**.

Example with step size:

```python
df.iloc[1:10:2]
```

Selects:

```text
1, 3, 5, 7, 9
```

The `step_size` is optional.

---

## Selecting Rows and Columns with `iloc`

```python
df.iloc[
    min_row_index : max_row_index + 1 : step_size,
    min_col_index : max_col_index + 1 : step_size
]
```

Example:

```python
df.iloc[1:5, 0:3]
```

Selects:

- Rows `1` through `4`
- Columns `0` through `2`

The result is a **DataFrame**.

---

# 4. `loc` vs `iloc`

## `iloc`

Used for **integer-position based indexing**.

```python
df.iloc[2]
df.iloc[1:5]
df.iloc[[1, 3, 5]]
```

Think:

> `iloc` → **integer location**

---

## `loc`

Used for **label-based indexing**.

```python
df.loc[row_label]
```

Example:

```python
df.loc['B']
```

Selects the row whose index label is `'B'`.

Multiple labels:

```python
df.loc[['A', 'C', 'D']]
```

### `loc` with Rows and Columns

```python
df.loc[row_labels, column_labels]
```

Example:

```python
df.loc[['A', 'C'], ['Name', 'Age']]
```

### Important Difference

```text
iloc → position
loc  → label
```

---

# 5. Filtering Data

## Boolean Conditions

A condition applied to a column produces a **Boolean Series** containing `True` and `False`.

```python
df['column_name'] == value
df['column_name'] > value
df['column_name'] < value
df['column_name'] >= value
df['column_name'] <= value
df['column_name'] != value
```

Example:

```python
df['Age'] > 25
```

Possible result:

```text
0     True
1    False
2     True
3    False
```

Each `True` means that the corresponding row satisfies the condition.

---

## Boolean Mask

The Boolean Series can be stored in a variable called a **mask**.

```python
mask = df['Age'] > 25
```

Then:

```python
df[mask]
```

returns only the rows where the condition is `True`.

This can also be written directly:

```python
df[df['Age'] > 25]
```

---

# 6. Multiple Conditions

Multiple conditions can be combined using Boolean operators.

```text
&  → AND
|  → OR
~  → NOT
```

### AND

```python
df[(df['Age'] > 25) & (df['Salary'] > 50000)]
```

Both conditions must be `True`.

### OR

```python
df[(df['Age'] > 25) | (df['Salary'] > 50000)]
```

At least one condition must be `True`.

### NOT

```python
df[~(df['Age'] > 25)]
```

Selects rows where `Age` is **not greater than 25**.

> **Important:** When using multiple conditions with pandas Series, use `&` and `|` instead of Python's `and` and `or`.

Also, put each condition inside parentheses.

---

# 7. `value_counts()`

## `df['column_name'].value_counts()`

Counts how many times each unique value appears in a column.

```python
df['column_name'].value_counts()
```

Example:

```python
df['Gender'].value_counts()
```

Possible output:

```text
Male      60
Female    40
```

The result is a **Series**.

In this Series:

```text
Index  → unique values
Values → number of occurrences
```

---

## Storing `value_counts()`

The result can be stored in a variable:

```python
myseries = df['Gender'].value_counts()
```

Now:

```python
myseries
```

contains the frequency of each unique value.

---

## `myseries.index`

Returns the index of the Series.

For a `value_counts()` result, this gives the **unique values**.

```python
myseries.index
```

---

## Mathematical Operations on Series

Since `value_counts()` returns a Series, mathematical operations can be performed on Series.

If two Series have the same indexes, operations are performed **based on matching indexes**.

Example:

```python
series1 + series2
```

Pandas aligns the Series by their index labels before performing the operation.

---

# 8. Plotting

Pandas provides built-in plotting functionality through Matplotlib.

First import Matplotlib:

```python
import matplotlib.pyplot as plt
```

## Plotting a Column

```python
df['column_name'].plot(kind='...')
```

Example:

```python
df['Age'].plot(kind='hist')
```

---

## Plotting `value_counts()`

```python
df['column_name'].value_counts().plot(kind='...')
```

Example:

```python
df['Gender'].value_counts().plot(kind='bar')
```

This is useful for visualizing how frequently different values occur.

---

## Common Plot Types

Some commonly used values for `kind` are:

```text
'line'
'bar'
'barh'
'hist'
'box'
'kde'
'area'
'pie'
'scatter'
```

Example:

```python
df['Age'].plot(kind='hist')
```

---

# 9. Sorting Data

## `df.sort_values()`

Sorts a DataFrame based on the values in one or more columns.

### Syntax

```python
df.sort_values(
    'column_name',
    ascending=True,
    inplace=False
)
```

---

## Sorting by One Column

```python
df.sort_values('Age')
```

By default, sorting is **ascending**.

Equivalent to:

```python
df.sort_values('Age', ascending=True)
```

### Descending Order

```python
df.sort_values('Age', ascending=False)
```

---

## `inplace=True`

If:

```python
df.sort_values('Age', inplace=True)
```

the original DataFrame is modified.

If `inplace=False` (the default), the original DataFrame is not modified and a sorted DataFrame is returned.

Example:

```python
new_df = df.sort_values('Age')
```

Here:

```text
df      → unchanged
new_df  → sorted
```

---

# 10. Sorting by Multiple Columns

Multiple columns can be passed as a list.

```python
df.sort_values(
    ['col1', 'col2'],
    ascending=[False, True]
)
```

Here:

```text
col1 → descending
col2 → ascending
```

Example:

```python
df.sort_values(
    ['Department', 'Salary'],
    ascending=[True, False]
)
```

This means:

1. Sort by `Department` in ascending order.
2. For rows having the same `Department`, sort by `Salary` in descending order.

`sort_values()` also works on a **Series**.

---

# Quick Reference

| Operation | Purpose | Result |
|---|---|---|
| `df.head()` | First 5 rows | DataFrame |
| `df.tail()` | Last 5 rows | DataFrame |
| `df.shape` | Rows and columns | Tuple |
| `df.info()` | DataFrame information | Output |
| `df.describe()` | Numerical statistics | DataFrame |
| `df['col']` | Select one column | Series |
| `df[['col1', 'col2']]` | Select multiple columns | DataFrame |
| `df.iloc[2]` | Select row by position | Series |
| `df.iloc[[1, 3]]` | Select multiple rows | DataFrame |
| `df.iloc[1:5]` | Slice rows by position | DataFrame |
| `df.loc['A']` | Select row by label | Series |
| `df[mask]` | Filter rows | DataFrame |
| `df['col'].value_counts()` | Count unique values | Series |
| `df['col'].plot()` | Plot a column | Plot |
| `df.sort_values('col')` | Sort by column | DataFrame |

---

# Important Things to Remember

### Series vs DataFrame

```python
df['Age']
```

→ **Series**

```python
df[['Age']]
```

→ **DataFrame**

---

### `iloc` vs `loc`

```text
iloc → integer position
loc  → label
```

---

### `head()` vs `tail()`

```python
df.head()
```

→ Top rows

```python
df.tail()
```

→ Bottom rows

---

### Filtering

```python
df[df['Age'] > 25]
```

→ Only rows satisfying the condition.

---

### Multiple Conditions

Use:

```python
&
|
~
```

Not:

```python
and
or
not
```

Example:

```python
df[(df['Age'] > 25) & (df['Salary'] > 50000)]
```

---

### `inplace`

```python
inplace=True
```

→ Modify the original DataFrame.

```python
inplace=False
```

→ Return a modified DataFrame without changing the original DataFrame.

---

### `value_counts()`

```python
df['col'].value_counts()
```

→ Counts occurrences of each unique value.

```text
Index  → unique values
Value  → frequency
```
