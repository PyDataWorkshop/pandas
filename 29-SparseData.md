

## Python Pandas - Sparse Data

Sparse objects are “compressed” when any data matching a specific value (NaN / missing value, though any value can be chosen) is omitted. A special SparseIndex object tracks where data has been “sparsified”. This will make much more sense in an example. 

All of the standard Pandas data structures apply the ``to_sparse`` method −



```python
import pandas as pd
import numpy as np

ts = pd.Series(np.random.randn(10))
ts[2:-2] = np.nan
sts = ts.to_sparse()
print(sts)
```

    0   -1.097459
    1    0.937604
    2         NaN
    3         NaN
    4         NaN
    5         NaN
    6         NaN
    7         NaN
    8   -0.460228
    9    0.190611
    dtype: float64
    BlockIndex
    Block locations: array([0, 8], dtype=int32)
    Block lengths: array([2, 2], dtype=int32)


#### BlockIndex
Block locations: array([0, 8], dtype=int32)
Block lengths: array([2, 2], dtype=int32)
The sparse objects exist for memory efficiency reasons.
Let us now assume you had a large NA DataFrame and execute the following code −


```python

import pandas as pd
import numpy as np

df = pd.DataFrame(np.random.randn(10000, 4))
df.iloc[:9998] = np.nan
sdf = df.to_sparse()

print(sdf.density)
```

    0.0002


Any sparse object can be converted back to the standard dense form by calling ``to_dense`` −


```python


import pandas as pd
import numpy as np
ts = pd.Series(np.random.randn(10))
ts[2:-2] = np.nan
sts = ts.to_sparse()
print(sts.to_dense())
```

    0    1.007406
    1   -0.115116
    2         NaN
    3         NaN
    4         NaN
    5         NaN
    6         NaN
    7         NaN
    8   -0.360093
    9    0.164599
    dtype: float64


### Sparse Dtypes
Sparse data should have the same dtype as its dense representation. Currently, float64, int64 and booldtypes are supported. Depending on the original dtype, fill_value default changes −
float64 − np.nan
int64 − 0
bool − False
Let us execute the following code to understand the same −


```python


import pandas as pd
import numpy as np

s = pd.Series([1, np.nan, np.nan])
print s

s.to_sparse()
print s
Its output is as follows −
0   1.0
1   NaN
2   NaN
dtype: float64

0   1.0
1   NaN
2   NaN
dtype: float64


```
