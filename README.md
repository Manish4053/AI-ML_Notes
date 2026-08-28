# NumPy & Pandas — Quick Revision Notes

A short, practical cheat sheet for learning the most important **NumPy and Pandas commands** for AI/ML in less time.

---

# 🐍 NumPy Short Notes

```python
import numpy as np
```

## 1. Creating Arrays

| Command | Use | Example |
|---|---|---|
| `np.array()` | Create array | `np.array([1,2,3])` |
| `np.zeros()` | Array of zeros | `np.zeros(5)` |
| `np.ones()` | Array of ones | `np.ones(5)` |
| `np.arange()` | Range of numbers | `np.arange(1,10,2)` |
| `np.linspace()` | Evenly spaced values | `np.linspace(0,1,5)` |

```python
a = np.array([10,20,30,40])
```

---

## 2. Array Information ⭐

```python
a.ndim       # Number of dimensions
a.shape      # Rows, columns
a.size       # Total elements
a.dtype      # Data type
```

Example:

```python
a = np.array([[1,2,3],[4,5,6]])

a.shape      # (2,3)
a.ndim       # 2
a.size       # 6
```

---

## 3. Indexing & Slicing

```python
a[0]         # First element/row
a[-1]        # Last element
a[1:4]       # Slice
```

For 2D:

```python
a[0,1]       # Row 0, Column 1
a[:,1]       # All rows, column 1
a[0,:]       # Row 0, all columns
```

---

## 4. Reshaping ⭐

```python
a.reshape(2,3)
```

Change the shape without changing the data.

```python
a.flatten()
```

Convert multidimensional array → 1D.

```python
a.T
```

Transpose: rows ↔ columns.

---

## 5. Mathematical Operations ⭐

```python
np.sum(a)
np.mean(a)
np.median(a)
np.min(a)
np.max(a)
np.std(a)
np.var(a)
np.sqrt(a)
```

Example:

```python
np.mean([10,20,30])    # 20
```

---

## 6. Axis ⭐⭐⭐

```python
np.sum(a, axis=0)   # Column-wise
np.sum(a, axis=1)   # Row-wise
```

Remember:

```text
axis=0 → down → columns
axis=1 → across → rows
```

---

## 7. Matrix Operations ⭐

```python
A + B
A - B
A * B          # Element-wise multiplication
A @ B          # Matrix multiplication
np.dot(A,B)    # Dot product
```

---

## 8. Random Numbers

```python
np.random.rand(3,2)          # Random floats
np.random.randint(1,10,5)    # Random integers
np.random.seed(42)           # Reproducible results
```

---

## 9. Filtering ⭐

```
---

## 1. NumPy Reference (`import numpy as np`)

### Array Creation
- `np.array([1, 2, 3])` — Create a 1D array from a list.
- `np.zeros((3, 3))` — Create a $3 \times 3$ array populated with zeros.
- `np.ones((2, 4))` — Create a $2 \times 4$ array populated with ones.
- `np.arange(0, 10, 2)` — Generate an array across an interval with a specified step size (`[0, 2, 4, 6, 8]`).
- `np.linspace(0, 1, 5)` — Generate 5 evenly spaced float values between 0 and 1.
- `np.random.rand(2, 2)` — Create a $2 \times 2$ array of uniform random values between 0 and 1.

### Array Manipulation & Inspection
- `arr.shape` — Return a tuple showing the array dimensions.
- `arr.dtype` — Inspect the data type of array elements.
- `arr.reshape(2, 5)` — Change array dimensions without altering underlying data.
- `arr.flatten()` — Collapse a multi-dimensional array into 1D.
- `np.concatenate([a, b], axis=0)` — Join arrays along a specified axis.

### Math & Statistics
- `arr.sum(axis=0)` / `arr.mean()` — Compute sum or mean (column-wise when `axis=0`).
- `arr.min()` / `arr.max()` — Find minimum and maximum elements.
- `arr.std()` — Calculate standard deviation.
- `np.dot(a, b)` — Compute matrix/vector dot product.
- `arr > 5` — Element-wise boolean comparison and masking.

---

## 2. Pandas Reference (`import pandas as pd`)

### Data Ingestion & Creation
- `pd.DataFrame({'A': [1, 2], 'B': [3, 4]})` — Construct a DataFrame from a dictionary.
- `pd.read_csv('file.csv')` — Ingest data from a CSV file.
- `pd.read_excel('file.xlsx')` — Ingest data from an Excel spreadsheet.
- `df.to_csv('output.csv', index=False)` — Export DataFrame to a CSV file without row indices.

### Exploration & Inspection
- `df.head(n)` / `df.tail(n)` — Inspect first/last $n$ rows (default is 5).
- `df.info()` — Display column types, memory usage, and non-null entry counts.
- `df.describe()` — Output summary statistics (count, mean, std, min, percentiles, max) for numeric columns.
- `df.shape` — Return row and column counts as a tuple `(rows, cols)`.
- `df['col'].value_counts()` — Count occurrences of each unique value in a Series.

### Selection & Filtering
- `df['col']` — Select a single column (returns a Series).
- `df[['col1', 'col2']]` — Select multiple columns (returns a DataFrame).
- `df.loc[0:5, 'col1']` — Label-based slicing and indexing (inclusive).
- `df.iloc[0:5, 0:2]` — Integer position-based indexing and slicing.
- `df[df['age'] > 25]` — Filter rows based on a boolean condition.

### Data Cleaning & Aggregation
- `df.dropna()` — Drop rows containing missing (`NaN`) values.
- `df.fillna(value)` — Impute missing values with a scalar or computed metric.
- `df.drop(columns=['col1'])` — Remove specified column(s).
- `df.rename(columns={'old': 'new'})` — Rename columns with a mapping dictionary.
- `df.groupby('category')['value'].mean()` — Group by unique keys and compute aggregates.
- `pd.merge(df1, df2, on='id', how='inner')` — Execute SQL-style table joins.

---

## 34. One Complete Example

Here is a small example that combines the core concepts: creating a dataset, inspecting it, handling missing values, creating derived columns, filtering, and sorting.

```python
import pandas as pd

# 1. Create dataset
df = pd.DataFrame({
    "Name": ["Ram", "Sita", "Hari", "John", "Alex"],
    "Age": [20, 21, None, 23, 22],
    "Marks": [80, 90, 75, None, 85]
})

# 2. Understand dataset
print("--- First 5 Rows ---")
print(df.head())

print("\n--- Dataset Info ---")
print(df.info())

print("\n--- Statistical Summary ---")
print(df.describe())

# 3. Check missing values
print("\n--- Missing Value Count ---")
print(df.isnull().sum())

# 4. Fill missing values (mean imputation)
df["Age"] = df["Age"].fillna(df["Age"].mean())
df["Marks"] = df["Marks"].fillna(df["Marks"].mean())

# 5. Add new column (conditional logic)
df["Pass"] = df["Marks"] >= 40

# 6. Filter students
top_students = df[df["Marks"] >= 80]
print("\n--- Top Students (Marks >= 80) ---")
print(top_students)

# 7. Sort by marks descending
df = df.sort_values("Marks", ascending=False)

print("\n--- Final Processed DataFrame ---")
print(df)
```

> **Summary:** This end-to-end script demonstrates a core data preprocessing workflow: ingestion/definition $\rightarrow$ structural & statistical profiling $\rightarrow$ null-value imputation $\rightarrow$ feature transformation $\rightarrow$ filtering $\rightarrow$ ordering.\n
numpy_pandas_notes_and_example.md
Displaying numpy_pandas_notes_and_example.md.
---

# 🐼 Pandas Short Notes

```python
import pandas as pd
```

## 1. Series & DataFrame ⭐⭐⭐

### Series

```python
s = pd.Series([10,20,30])
```

One-dimensional data.

### DataFrame

```python
df = pd.DataFrame({
    "Name": ["Ram","Sita","Hari"],
    "Marks": [80,90,75]
})
```

Think:

```text
Series     → One column
DataFrame  → Complete table
```

---

# 2. Reading & Saving Data ⭐⭐⭐

```python
pd.read_csv("data.csv")
pd.read_excel("data.xlsx")
```

Save:

```python
df.to_csv("output.csv", index=False)
df.to_excel("output.xlsx", index=False)
```

---

# 3. Understanding Dataset ⭐⭐⭐

These are the **first commands you should use on any new dataset**:

```python
df.head()       # First 5 rows
df.tail()       # Last 5 rows
df.info()       # Structure + data types + nulls
df.describe()   # Statistical summary
df.shape        # Rows, columns
df.columns      # Column names
df.dtypes       # Data types
```

### Remember:

```text
head()      → See data
info()      → Understand structure
describe()  → Statistics
shape       → Size
```

---

# 4. Selecting Columns ⭐⭐⭐

One column:

```python
df["Marks"]
```

Multiple columns:

```python
df[["Name","Marks"]]
```

---

# 5. Selecting Rows

### `iloc` → index based

```python
df.iloc[0]       # First row
df.iloc[0:3]     # First 3 rows
df.iloc[1,2]     # Specific cell
```

### `loc` → label based

```python
df.loc[0]
df.loc[:, "Marks"]
```

Easy way to remember:

```text
iloc → integer position
loc  → label/name
```

---

# 6. Filtering ⭐⭐⭐

```python
df[df["Marks"] > 80]
```

Multiple conditions:

```python
df[(df["Marks"] > 80) & (df["Age"] > 20)]
```

Operators:

```text
&  → AND
|  → OR
~  → NOT
```

---

# 7. Adding/Modifying Columns

Add:

```python
df["Pass"] = df["Marks"] >= 40
```

Modify:

```python
df["Marks"] = df["Marks"] + 5
```

---

# 8. Missing Values ⭐⭐⭐

Check:

```python
df.isnull()
df.isnull().sum()
```

Remove:

```python
df.dropna()
```

Fill:

```python
df["Age"].fillna(df["Age"].mean())
```

Common pattern:

```python
df["Age"] = df["Age"].fillna(df["Age"].mean())
```

---

# 9. Sorting

```python
df.sort_values("Marks")
```

Descending:

```python
df.sort_values("Marks", ascending=False)
```

---

# 10. Duplicates

```python
df.drop_duplicates()
```

---

# 11. Statistics

```python
df["Marks"].mean()
df["Marks"].median()
df["Marks"].min()
df["Marks"].max()
df["Marks"].sum()
df["Marks"].std()
```

---

# 12. Unique Values ⭐

```python
df["Department"].unique()
```

Number of unique values:

```python
df["Department"].nunique()
```

Frequency:

```python
df["Department"].value_counts()
```

---

# 13. GroupBy ⭐⭐⭐

Used to group data and calculate statistics.

```python
df.groupby("Department")["Marks"].mean()
```

Other operations:

```python
df.groupby("Department")["Marks"].sum()
df.groupby("Department")["Marks"].max()
df.groupby("Department")["Marks"].count()
```

Think:

```text
groupby()
   ↓
Group data
   ↓
Calculate something
```

---

# 14. Rename Columns

```python
df.rename(columns={"Marks":"Score"}, inplace=True)
```

---

# 15. Combining DataFrames

```python
pd.concat([df1, df2])
```

Combine/join based on a column:

```python
pd.merge(df1, df2, on="id")
```

Remember:

```text
concat → combine
merge  → join
```

---

# 🔥 MOST IMPORTANT COMMANDS TO MEMORIZE

If you're short on time, memorize **these first**.

## NumPy

```python
np.array()
np.zeros()
np.ones()
np.arange()
np.linspace()

a.shape
a.ndim
a.size

a.reshape()
a.flatten()
a.T

np.mean()
np.median()
np.sum()
np.min()
np.max()
np.std()

np.random.rand()
np.random.randint()

a[a > value]

A @ B
```

## Pandas

```python
pd.DataFrame()
pd.Series()

pd.read_csv()

df.head()
df.info()
df.describe()
df.shape
df.columns
df.dtypes

df["column"]
df[["col1","col2"]]

df.iloc[]
df.loc[]

df[df["column"] > value]

df.isnull().sum()
df.dropna()
df.fillna()

df.sort_values()
df.drop_duplicates()

df.groupby()
df.unique()
df.value_counts()

pd.merge()
pd.concat()

df.to_csv()
```

---

# 🧠 One-Minute Memory Map

```text
                 NUMPY
                   │
       ┌───────────┼───────────┐
       ↓           ↓           ↓
    Create      Analyze      Modify
       │           │           │
   array()      mean()       reshape()
   zeros()      sum()        flatten()
   ones()       max()        transpose
   arange()     min()
                std()

                 PANDAS
                   │
       ┌───────────┼────────────┐
       ↓           ↓            ↓
     READ        CLEAN        ANALYZE
       │           │            │
  read_csv()    isnull()      groupby()
  head()        fillna()       mean()
  info()        dropna()       value_counts()
  describe()    duplicates     sort_values()
       │
       ↓
   SELECT/FILTER
       │
   loc / iloc
   df["column"]
   df[condition]
```

---

# 🎯 Recommended AI/ML Learning Order

For AI/ML preparation, follow this order:

**NumPy → Pandas → Matplotlib → Data Preprocessing → Scikit-learn → ML Algorithms**

You don't need to master every NumPy/Pandas function before moving ahead. Practice the commands marked ⭐⭐⭐ and use them on a real CSV dataset.
