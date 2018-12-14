
Python Pandas - Caveats


Caveats means warning and gotcha means an unseen problem.

### Using If/Truth Statement with Pandas
Pandas follows the numpy convention of raising an error when you try to convert something to a bool. This happens in an if or when using the Boolean operations, and, or, or not. It is not clear what the result should be. Should it be True because it is not zerolength? False because there are False values? It is unclear, so instead, Pandas raises a ValueError −


<pre><code>
import pandas as pd

if pd.Series([False, True, False]):
   print('I am True')
</code></pre>

Its output is as follows −
<pre><code>
ValueError: The truth value of a Series is ambiguous. Use a.empty, a.bool() a.item(), a.any() or a.all().
</code></pre>    
In if condition, it is unclear what to do with it. The error is suggestive of whether to use a None or any of those.


```python
import pandas as pd
if pd.Series([False, True, False]).any():
   print("I am any")
```


```python


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

```


```python
import pandas as pd

s = pd.Series(list('abc'))
s = s.isin(['a', 'c', 'e'])
print(s)
```

    0     True
    1    False
    2     True
    dtype: bool



```python
Reindexing vs ix Gotcha
Many users will find themselves using the ix indexing capabilities as a concise means of selecting data from a Pandas object −

```


```python


import pandas as pd
import numpy as np

df = pd.DataFrame(np.random.randn(6, 4), columns=['one', 'two', 'three',
'four'],index=list('abcdef'))

print (df)
print (df.loc[['b', 'c', 'e']])

```

            one       two     three      four
    a -1.345411  0.970597  0.930269  0.388520
    b -1.387839 -0.487871 -1.102046  0.908156
    c -1.015735  0.316692 -0.751919  0.572387
    d  2.496765  0.400015 -1.630830  1.385007
    e -2.150634  0.648656  0.328425  0.447221
    f -0.595839 -1.675665  0.200536  0.256498
            one       two     three      four
    b -1.387839 -0.487871 -1.102046  0.908156
    c -1.015735  0.316692 -0.751919  0.572387
    e -2.150634  0.648656  0.328425  0.447221



```python
This is, of course, completely equivalent in this case to using the reindex method −
```


```python


import pandas as pd
import numpy as np
df = pd.DataFrame(np.random.randn(6, 4), columns=['one', 'two', 'three',
'four'],index=list('abcdef'))
print(df
print(df.reindex(['b', 'c', 'e'])
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

print(df)
print(df.ix[[1, 2, 4]])
print(df.reindex([1, 2, 4]))
```



It is important to remember that reindex is strict label indexing only. This can lead to some potentially surprising results in pathological cases where an index contains, say, both integers and strings.

=

