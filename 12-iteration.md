

```python

### Python Pandas - Iteration



The behavior of basic iteration over Pandas objects depends on the type. When iterating over a Series, it is regarded as array-like, and basic iteration produces the values. Other data structures, like DataFrame and Panel, follow the dict-like convention of iterating over the keys of the objects.
In short, basic iteration (for i in object) produces −
Series − values
DataFrame − column labels
Panel − item labels
Iterating a DataFrame
Iterating a DataFrame gives column names. Let us consider the following example to understand the same.

```


```python
import pandas as pd
import numpy as np
 
N=20

df = pd.DataFrame({
    'A': pd.date_range(start='2016-01-01',periods=N,freq='D'),
    'x': np.linspace(0,stop=N-1,num=N),
    'y': np.random.rand(N),
    'C': np.random.choice(['Low','Medium','High'],N).tolist(),
    'D': np.random.normal(100, 10, size=(N)).tolist()
    })

for col in df:
   print(col)
```

    A
    C
    D
    x
    y


To iterate over the rows of the DataFrame, we can use the following functions −

* ``iteritems()`` - to iterate over the (key,value) pairs
* ``iterrows()`` - iterate over the rows as (index,series) pairs
* ``itertuples()`` - iterate over the rows as namedtuples
* ``iteritems()`` - Iterates over each column as key, value pair with label as key and column value as a Series object.


```python
import pandas as pd
import numpy as np
 
df = pd.DataFrame(np.random.randn(4,3),columns=['col1','col2','col3'])
for key,value in df.iteritems():
    print(key,value)
```

    col1 0    1.141317
    1    0.289031
    2   -1.269689
    3   -1.668425
    Name: col1, dtype: float64
    col2 0    1.561011
    1    0.391033
    2    0.083089
    3    0.106299
    Name: col2, dtype: float64
    col3 0   -0.436407
    1    0.136565
    2    0.444321
    3    0.738629
    Name: col3, dtype: float64



```python

Observe, each column is iterated separately as a key-value pair in a Series.
iterrows()
iterrows() returns the iterator yielding each index value along with a series containing the data in each row.
```


```python
import pandas as pd
import numpy as np

df = pd.DataFrame(np.random.randn(4,3),columns = ['col1','col2','col3'])
for row_index,row in df.iterrows():
    print("\n")
    print(row_index,row)
```

    
    
    0 col1   -0.469367
    col2   -1.466803
    col3    0.493435
    Name: 0, dtype: float64
    
    
    1 col1    0.686016
    col2   -1.293819
    col3   -1.087791
    Name: 1, dtype: float64
    
    
    2 col1    0.646084
    col2   -0.312096
    col3    1.518408
    Name: 2, dtype: float64
    
    
    3 col1   -2.464781
    col2    0.211235
    col3   -0.238992
    Name: 3, dtype: float64



Note − Because iterrows() iterate over the rows, it doesn't preserve the data type across the row. 0,1,2 are the row indices and col1,col2,col3 are column indices.



```python
itertuples()
itertuples() method will return an iterator yielding a named tuple for each row in the DataFrame. The first element of the tuple will be the row’s corresponding index value, while the remaining values are the row values.


```


```python
import pandas as pd
import numpy as np

df = pd.DataFrame(np.random.randn(4,3),columns = ['col1','col2','col3'])
for row in df.itertuples():
    print("\n")
    print(row)
```

    
    
    Pandas(Index=0, col1=-0.9771341226396765, col2=0.2724475615802741, col3=-0.6589499024186599)
    
    
    Pandas(Index=1, col1=1.6177467086432253, col2=-0.9763868574908899, col3=0.08317561529190409)
    
    
    Pandas(Index=2, col1=-0.988445247281908, col2=-0.6366889592765412, col3=0.3956289433362847)
    
    
    Pandas(Index=3, col1=-0.19595952598665276, col2=-0.13115863172857256, col3=-0.04519796025813786)




Note − Do not try to modify any object while iterating. Iterating is meant for reading and the iterator returns a copy of the original object (a view), thus the changes will not reflect on the original object.





```python
import pandas as pd
import numpy as np

df = pd.DataFrame(np.random.randn(4,3),columns = ['col1','col2','col3'])

for index, row in df.iterrows():
    row['a'] = 10

print(df)

```

           col1      col2      col3
    0  0.325979  0.892602 -1.034127
    1  2.267333 -0.356288 -2.088448
    2 -1.159300  1.004701  0.742375
    3  0.132715 -1.565420 -1.142597



```python
Observe, no changes reflected.

```
