

```python
Python Pandas - Caveats


Caveats means warning and gotcha means an unseen problem.
Using If/Truth Statement with Pandas
Pandas follows the numpy convention of raising an error when you try to convert something to a bool. This happens in an if or when using the Boolean operations, and, or, or not. It is not clear what the result should be. Should it be True because it is not zerolength? False because there are False values? It is unclear, so instead, Pandas raises a ValueError −

```


```python
import pandas as pd

if pd.Series([False, True, False]):
   print 'I am True'
Its output is as follows −
ValueError: The truth value of a Series is ambiguous. Use a.empty, a.bool() a.item(), a.any() or a.all().
In if condition, it is unclear what to do with it. The error is suggestive of whether to use a None or any of those.
```


```python

import pandas as pd
if pd.Series([False, True, False]).any():
   print("I am any")
Its output is as follows −
I am any
To evaluate single-element pandas objects in a Boolean context, use the method .bool() −
import pandas as pd
print pd.Series([True]).bool()
Its output is as follows −
True
```


```python
Bitwise Boolean
Bitwise Boolean operators like == and != will return a Boolean series, which is almost always what is required anyways.
import pandas as pd

s = pd.Series(range(5))
print s==4
Its output is as follows −
0 False
1 False
2 False
3 False
4 True
dtype: bool
```


```python

isin Operation
This returns a Boolean series showing whether each element in the Series is exactly contained in the passed sequence of values.
import pandas as pd

s = pd.Series(list('abc'))
s = s.isin(['a', 'c', 'e'])
print s
Its output is as follows −
0 True
1 False
2 True
dtype: bool
```


```python


Reindexing vs ix Gotcha
Many users will find themselves using the ix indexing capabilities as a concise means of selecting data from a Pandas object −
import pandas as pd
import numpy as np

df = pd.DataFrame(np.random.randn(6, 4), columns=['one', 'two', 'three',
'four'],index=list('abcdef'))

print df
print df.ix[['b', 'c', 'e']]
Its output is as follows −
          one        two      three       four
a   -1.582025   1.335773   0.961417  -1.272084
b    1.461512   0.111372  -0.072225   0.553058
c   -1.240671   0.762185   1.511936  -0.630920
d   -2.380648  -0.029981   0.196489   0.531714
e    1.846746   0.148149   0.275398  -0.244559
f   -1.842662  -0.933195   2.303949   0.677641

          one        two      three       four
b    1.461512   0.111372  -0.072225   0.553058
c   -1.240671   0.762185   1.511936  -0.630920
e    1.846746   0.148149   0.275398  -0.244559
```


```python

This is, of course, completely equivalent in this case to using the reindex method −
import pandas as pd
import numpy as np
df = pd.DataFrame(np.random.randn(6, 4), columns=['one', 'two', 'three',
'four'],index=list('abcdef'))
print df
print df.reindex(['b', 'c', 'e'])
Its output is as follows −
          one        two      three       four
a    1.639081   1.369838   0.261287  -1.662003
b   -0.173359   0.242447  -0.494384   0.346882
c   -0.106411   0.623568   0.282401  -0.916361
d   -1.078791  -0.612607  -0.897289  -1.146893
e    0.465215   1.552873  -1.841959   0.329404
f    0.966022  -0.190077   1.324247   0.678064

          one        two      three       four
b   -0.173359   0.242447  -0.494384   0.346882
c   -0.106411   0.623568   0.282401  -0.916361
e    0.465215   1.552873  -1.841959   0.329404
Some might conclude that ix and reindex are 100% equivalent based on this. This is true except in the case of integer indexing. For example, the above operation can alternatively be expressed as −

```


```python
import pandas as pd
import numpy as np

df = pd.DataFrame(np.random.randn(6, 4), columns=['one', 'two', 'three',
'four'],index=list('abcdef'))

print df
print df.ix[[1, 2, 4]]
print df.reindex([1, 2, 4])
```


```python


Its output is as follows −
          one        two      three       four
a   -1.015695  -0.553847   1.106235  -0.784460
b   -0.527398  -0.518198  -0.710546  -0.512036
c   -0.842803  -1.050374   0.787146   0.205147
d   -1.238016  -0.749554  -0.547470  -0.029045
e   -0.056788   1.063999  -0.767220   0.212476
f    1.139714   0.036159   0.201912   0.710119

          one        two      three       four
b   -0.527398  -0.518198  -0.710546  -0.512036
c   -0.842803  -1.050374   0.787146   0.205147
e   -0.056788   1.063999  -0.767220   0.212476

    one  two  three  four
1   NaN  NaN    NaN   NaN
2   NaN  NaN    NaN   NaN
4   NaN  NaN    NaN   NaN
It is important to remember that reindex is strict label indexing only. This can lead to some potentially surprising results in pathological cases where an index contains, say, both integers and strings.

=

```
