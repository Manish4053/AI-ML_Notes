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

```python
a[a > 10]
```

Example:

```python
a = np.array([5,10,15,20])

a[a > 10]
# [15 20]
```

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
