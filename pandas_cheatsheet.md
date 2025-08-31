# Pandas Cheat Sheet

This cheat sheet provides a quick reference for the most common and useful pandas functions and methods.

## Installation

To install pandas, use pip:

```bash
pip install pandas
```

## Data Structures

Pandas has two main data structures: **Series** and **DataFrame**.

### Series

A **Series** is a one-dimensional labeled array capable of holding any data type.

**Create a Series:**

```python
import pandas as pd
import numpy as np

s = pd.Series([1, 3, 5, np.nan, 6, 8])
print(s)
```

**Output:**

```
0    1.0
1    3.0
2    5.0
3    NaN
4    6.0
5    8.0
dtype: float64
```

### DataFrame

A **DataFrame** is a two-dimensional labeled data structure with columns of potentially different types. It is like a spreadsheet or SQL table, or a dict of Series objects.

**Create a DataFrame:**

```python
import pandas as pd
import numpy as np

dates = pd.date_range('20230101', periods=6)
df = pd.DataFrame(np.random.randn(6, 4), index=dates, columns=list('ABCD'))
print(df)
```

**Output:**

```
                   A         B         C         D
2023-01-01 -0.422572  0.725375 -0.192563  0.879234
2023-01-02  1.454556 -0.364277 -0.542289 -0.520977
2023-01-03 -0.587786  0.311773 -0.236561 -0.237227
2023-01-04  0.222284 -0.134937  1.181673  0.265512
2023-01-05 -0.443683 -0.923157 -0.408793  0.642051
2023-01-06 -0.126410  0.379427 -0.463661  0.312211
```

## Data Import and Export

Pandas supports reading and writing data in many formats.

**CSV:**

```python
# Writing to a CSV file
df.to_csv('foo.csv')

# Reading from a CSV file
pd.read_csv('foo.csv')
```

**Excel:**

```python
# Writing to an Excel file
df.to_excel('foo.xlsx', sheet_name='Sheet1')

# Reading from an Excel file
pd.read_excel('foo.xlsx', 'Sheet1', index_col=None, na_values=['NA'])
```

## Data Inspection

**View the top and bottom rows of the frame:**

```python
df.head()
```

**Output:**

```
                   A         B         C         D
2023-01-01  0.469112 -0.282863 -1.509059 -1.135632
2023-01-02  1.212112 -0.173215  0.119209 -1.044236
2023-01-03 -0.861849 -2.104569 -0.494929  1.071804
2023-01-04  0.721555 -0.706771 -1.039575  0.271860
2023-01-05 -0.424972  0.567020  0.276232 -1.087401
```

```python
df.tail(3)
```

**Output:**

```
                   A         B         C         D
2023-01-04  0.721555 -0.706771 -1.039575  0.271860
2023-01-05 -0.424972  0.567020  0.276232 -1.087401
2023-01-06 -0.673690  0.113648 -1.478427  0.524988
```

**Display the index, columns, and underlying NumPy data:**

```python
df.index
```

**Output:**

```
DatetimeIndex(['2023-01-01', '2023-01-02', '2023-01-03', '2023-01-04',
               '2023-01-05', '2023-01-06'],
              dtype='datetime64[ns]', freq='D')
```

```python
df.columns
```

**Output:**

```
Index(['A', 'B', 'C', 'D'], dtype='object')
```

```python
df.to_numpy()
```

**Output:**

```
array([[ 0.4691123 , -0.28286334, -1.5090585 , -1.13563237],
       [ 1.21211203, -0.17321465,  0.11920913, -1.04423592],
       [-0.86184885, -2.1045693 , -0.49492928,  1.07180359],
       [ 0.72155527, -0.70677118, -1.03957501,  0.2718602 ],
       [-0.42497248,  0.56702028,  0.27623168, -1.08740107],
       [-0.6736904 ,  0.11364843, -1.47842681,  0.52498793]])
```

**Get a quick statistical summary of your data:**

```python
df.describe()
```

**Output:**

```
              A         B         C         D
count  6.000000  6.000000  6.000000  6.000000
mean   0.073711 -0.431125 -0.687758 -0.249769
std    0.849265  0.941349  0.742296  0.943939
min   -0.861849 -2.104569 -1.509059 -1.135632
25%   -0.611511 -0.600794 -1.368714 -1.076610
50%    0.022070 -0.228039 -0.767252 -0.386188
75%    0.658444  0.041933 -0.034326  0.461706
max    1.212112  0.567020  0.276232  1.071804
```

**Transpose your data:**

```python
df.T
```

**Output:**

```
   2023-01-01  2023-01-02  2023-01-03  2023-01-04  2023-01-05  2023-01-06
A    0.469112    1.212112   -0.861849    0.721555   -0.424972   -0.673690
B   -0.282863   -0.173215   -2.104569   -0.706771    0.567020    0.113648
C   -1.509059    0.119209   -0.494929   -1.039575    0.276232   -1.478427
D   -1.135632   -1.044236    1.071804    0.271860   -1.087401    0.524988
```

**Sort by an axis:**

```python
df.sort_index(axis=1, ascending=False)
```

**Output:**

```
                   D         C         B         A
2023-01-01 -1.135632 -1.509059 -0.282863  0.469112
2023-01-02 -1.044236  0.119209 -0.173215  1.212112
2023-01-03  1.071804 -0.494929 -2.104569 -0.861849
2023-01-04  0.271860 -1.039575 -0.706771  0.721555
2023-01-05 -1.087401  0.276232  0.567020 -0.424972
2023-01-06  0.524988 -1.478427  0.113648 -0.673690
```

**Sort by values:**

```python
df.sort_values(by='B')
```

**Output:**

```
                   A         B         C         D
2023-01-03 -0.861849 -2.104569 -0.494929  1.071804
2023-01-04  0.721555 -0.706771 -1.039575  0.271860
2023-01-01  0.469112 -0.282863 -1.509059 -1.135632
2023-01-02  1.212112 -0.173215  0.119209 -1.044236
2023-01-06 -0.673690  0.113648 -1.478427  0.524988
2023-01-05 -0.424972  0.567020  0.276232 -1.087401
```

## Data Selection

Pandas supports a variety of ways to select data.

**Getting a single column:**

```python
df['A']
```

**Output:**

```
2023-01-01    0.469112
2023-01-02    1.212112
2023-01-03   -0.861849
2023-01-04    0.721555
2023-01-05   -0.424972
2023-01-06   -0.673690
Freq: D, Name: A, dtype: float64
```

**Slicing rows:**

```python
df[0:3]
```

**Output:**

```
                   A         B         C         D
2023-01-01  0.469112 -0.282863 -1.509059 -1.135632
2023-01-02  1.212112 -0.173215  0.119209 -1.044236
2023-01-03 -0.861849 -2.104569 -0.494929  1.071804
```

**Selection by label:**

```python
df.loc[dates[0]]
```

**Output:**

```
A    0.469112
B   -0.282863
C   -1.509059
D   -1.135632
Name: 2023-01-01 00:00:00, dtype: float64
```

**Selecting on a multi-axis by label:**

```python
df.loc[:, ['A', 'B']]
```

**Output:**

```
                   A         B
2023-01-01  0.469112 -0.282863
2023-01-02  1.212112 -0.173215
2023-01-03 -0.861849 -2.104569
2023-01-04  0.721555 -0.706771
2023-01-05 -0.424972  0.567020
2023-01-06 -0.673690  0.113648
```

**Showing a label-based slice, both endpoints are *included*:**

```python
df.loc['20230102':'20230104', ['A', 'B']]
```

**Output:**

```
                   A         B
2023-01-02  1.212112 -0.173215
2023-01-03 -0.861849 -2.104569
2023-01-04  0.721555 -0.706771
```

**Selection by position:**

```python
df.iloc[3]
```

**Output:**

```
A    0.721555
B   -0.706771
C   -1.039575
D    0.271860
Name: 2023-01-04 00:00:00, dtype: float64
```

**Slicing rows explicitly:**

```python
df.iloc[3:5, 0:2]
```

**Output:**

```
                   A         B
2023-01-04  0.721555 -0.706771
2023-01-05 -0.424972  0.567020
```

**Slicing columns explicitly:**

```python
df.iloc[[1, 2, 4], [0, 2]]
```

**Output:**

```
                   A         C
2023-01-02  1.212112  0.119209
2023-01-03 -0.861849 -0.494929
2023-01-05 -0.424972  0.276232
```

**Boolean indexing:**

```python
df[df['A'] > 0]
```

**Output:**

```
                   A         B         C         D
2023-01-01  0.469112 -0.282863 -1.509059 -1.135632
2023-01-02  1.212112 -0.173215  0.119209 -1.044236
2023-01-04  0.721555 -0.706771 -1.039575  0.271860
```

**Using `isin()` method for filtering:**

```python
df2 = df.copy()
df2['E'] = ['one', 'one', 'two', 'three', 'four', 'three']
df2[df2['E'].isin(['two', 'four'])]
```

**Output:**

```
                   A         B         C         D      E
2023-01-03 -0.861849 -2.104569 -0.494929  1.071804    two
2023-01-05 -0.424972  0.567020  0.276232 -1.087401   four
```

## Data Cleaning

Pandas provides a comprehensive set of tools for cleaning and preparing data.

**Handling missing data:**

```python
df1 = df.reindex(index=dates[0:4], columns=list(df.columns) + ['E'])
df1.loc[dates[0]:dates[1], 'E'] = 1

# Drop any rows that have missing data
df1.dropna(how='any')
```

**Output:**

```
                   A         B         C         D    E
2023-01-01  0.469112 -0.282863 -1.509059 -1.135632  1.0
2023-01-02  1.212112 -0.173215  0.119209 -1.044236  1.0
```

```python
# Filling missing data
df1.fillna(value=5)
```

**Output:**

```
                   A         B         C         D    E
2023-01-01  0.469112 -0.282863 -1.509059 -1.135632  1.0
2023-01-02  1.212112 -0.173215  0.119209 -1.044236  1.0
2023-01-03 -0.861849 -2.104569 -0.494929  1.071804  5.0
2023-01-04  0.721555 -0.706771 -1.039575  0.271860  5.0
```

```python
# Get the boolean mask where values are nan
pd.isna(df1)
```

**Output:**

```
                A      B      C      D      E
2023-01-01  False  False  False  False  False
2023-01-02  False  False  False  False  False
2023-01-03  False  False  False  False   True
2023-01-04  False  False  False  False   True
```

**Dropping duplicates:**

```python
df2 = pd.DataFrame({'A': [1, 1, 2, 2], 'B': ['a', 'a', 'b', 'b']})
df2.duplicated()
```

**Output:**

```
0    False
1     True
2    False
3     True
dtype: bool
```

```python
df2.drop_duplicates()
```

**Output:**

```
   A  B
0  1  a
2  2  b
```

## Data Manipulation

**Applying functions to the data:**

```python
df.apply(np.cumsum)
```

**Output:**

```
                   A         B         C         D
2023-01-01  0.469112 -0.282863 -1.509059 -1.135632
2023-01-02  1.681224 -0.456078 -1.389850 -2.179868
2023-01-03  0.819375 -2.560647 -1.884779 -1.108065
2023-01-04  1.540931 -3.267418 -2.924354 -0.836204
2023-01-05  1.115958 -2.700398 -2.648122 -1.923605
2023-01-06  0.442268 -2.586750 -4.126549 -1.398618
```

```python
df.apply(lambda x: x.max() - x.min())
```

**Output:**

```
A    2.073961
B    2.671590
C    1.785291
D    2.159205
dtype: float64
```

**String Methods:**

```python
s = pd.Series(['A', 'B', 'C', 'Aaba', 'Baca', np.nan, 'CABA', 'dog', 'cat'])
s.str.lower()
```

**Output:**

```
0       a
1       b
2       c
3    aaba
4    baca
5     NaN
6    caba
7    dog
8     cat
dtype: object
```

## Grouping and Aggregation

**Grouping:**

```python
df = pd.DataFrame({'A': ['foo', 'bar', 'foo', 'bar',
                          'foo', 'bar', 'foo', 'foo'],
                   'B': ['one', 'one', 'two', 'three',
                         'two', 'two', 'one', 'three'],
                   'C': np.random.randn(8),
                   'D': np.random.randn(8)})

df.groupby('A').sum()
```

**Output:**

```
              C         D
A                        
bar -0.076324  0.693481
foo -1.455249 -0.222380
```

**Grouping by multiple columns:**

```python
df.groupby(['A', 'B']).sum()
```

**Output:**

```
                C         D
A   B                      
bar one   -0.562288 -0.233939
    three -0.022539  0.835496
    two    0.508503  0.091924
foo one    0.283121  0.022722
    three -0.488335 -0.638423
    two   -1.250035  0.393321
```

## Merging and Joining

**Concatenating:**

```python
df = pd.DataFrame(np.random.randn(10, 4))
pieces = [df[:3], df[3:7], df[7:]]
pd.concat(pieces)
```

**Output:**

```
          0         1         2         3
0 -0.293291 -0.294923  0.467339 -1.242738
1  0.584954  0.223438 -0.109183  0.279836
2 -0.242830  0.959828 -1.110582 -0.129252
3  0.499444 -0.370557 -1.136453  0.457582
4 -0.061736 -0.182933  1.321113 -0.262514
5  0.308332 -0.458993 -0.433438  1.121397
6  0.941919 -0.876864 -0.151379 -1.025934
7  0.244383  0.273821 -0.569333  0.218693
8  0.697421 -0.271329 -0.407838 -0.368393
9  0.999658 -1.258182 -0.899242  0.129373
```

**Join:**

```python
left = pd.DataFrame({'key': ['foo', 'foo'], 'lval': [1, 2]})
right = pd.DataFrame({'key': ['foo', 'foo'], 'rval': [4, 5]})
pd.merge(left, right, on='key')
```

**Output:**

```
   key  lval  rval
0  foo     1     4
1  foo     1     5
2  foo     2     4
3  foo     2     5
```

## Time Series Analysis

Pandas has simple, powerful, and efficient functionality for performing resampling operations during frequency conversion (e.g., converting secondly data into 5-minutely data).

```python
rng = pd.date_range('1/1/2012', periods=100, freq='S')
ts = pd.Series(np.random.randint(0, 500, len(rng)), index=rng)
ts.resample('5Min').sum()
```

**Output:**

```
2012-01-01    25622
Freq: 5T, Name: None, dtype: int32
```

## Plotting

Pandas uses the `plot()` method to create plots.

```python
ts = pd.Series(np.random.randn(1000), index=pd.date_range('1/1/2000', periods=1000))
ts = ts.cumsum()
# The following line will display a plot in a new window.
ts.plot()
```

**Plotting with a DataFrame:**

```python
df = pd.DataFrame(np.random.randn(1000, 4), index=ts.index,
                  columns=['A', 'B', 'C', 'D'])
df = df.cumsum()
# The following line will display a plot in a new window.
df.plot()
```
