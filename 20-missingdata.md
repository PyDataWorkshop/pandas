
Python Pandas - Missing Data
Missing data is always a problem in real life scenarios. Areas like machine learning and data mining face severe issues in the accuracy of their model predictions because of poor quality of data caused by missing values. In these areas, missing value treatment is a major point of focus to make their models more accurate and valid. When and Why Is Data Missed? Let us consider an online survey for a product. Many a times, people do not share all the information related to them. Few people share their experience, but not how long they are using the product; few people share how long they are using the product, their experience but not their contact information. Thus, in some or the other way a part of data is always missing, and this is very common in real time. Let us now see how we can handle missing values (say NA or NaN) using Pandas.
import the pandas library



```python
import pandas as pd 
import numpy as np
df = pd.DataFrame(np.random.randn(5, 3), index=['a', 'c', 'e', 'f', 'h'],columns=['one', 'two', 'three'])
df = df.reindex(['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h'])
print(df)
```

            one       two     three
    a  0.526562 -1.088106 -0.782926
    b       NaN       NaN       NaN
    c  0.024854 -0.189596  0.777768
    d       NaN       NaN       NaN
    e  1.546276  0.313778  0.157720
    f -2.041777  0.497763  1.240035
    g       NaN       NaN       NaN
    h -0.359819  0.851079  0.413367



Using reindexing, we have created a DataFrame with missing values. In the output, NaN means Not a Number. Check for Missing Values To make detecting missing values easier (and across different array dtypes), Pandas provides the isnull() and notnull() functions, which are also methods on Series and DataFrame objects − Example 1 import pandas as pd import numpy as np



```python
df = pd.DataFrame(np.random.randn(5, 3), index=['a', 'c', 'e', 'f', 'h'],columns=['one', 'two', 'three'])
df = df.reindex(['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h'])
print( df['one'].isnull() )
```

    a    False
    b     True
    c    False
    d     True
    e    False
    f    False
    g     True
    h    False
    Name: one, dtype: bool



```python
### Example 2 
import pandas as pd 
import numpy as np
df = pd.DataFrame(np.random.randn(5, 3), index=['a', 'c', 'e', 'f', 'h'],columns=['one', 'two', 'three'])
df = df.reindex(['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h'])
print( df['one'].notnull())
```

    a     True
    b    False
    c     True
    d    False
    e     True
    f     True
    g    False
    h     True
    Name: one, dtype: bool


### Calculations with Missing Data 
When summing data, NA will be treated as Zero If the data are all NA, then the result will be NA 

#### Example 1


```python
import pandas as pd 
import numpy as np
df = pd.DataFrame(np.random.randn(5, 3), index=['a', 'c', 'e', 'f', 'h'],columns=['one', 'two', 'three'])
df = df.reindex(['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h'])
print( df['one'].sum() )
```

    -1.838451822493456


#### Example 2


```python
import pandas as pd 
import numpy as np
df = pd.DataFrame(index=[0,1,2,3,4,5],columns=['one','two']) 
print( df['one'].sum() )

```

    0



Its output is as follows − nan Cleaning / Filling Missing Data Pandas provides various methods for cleaning the missing values. 

The fillna function can “fill in” NA values with non-null data in a couple of ways, which we have illustrated in the following sections. 

#### Replace NaN with a Scalar Value 

The following program shows how you can replace "NaN" with "0". 



```python
import pandas as pd 
import numpy as np 
df = pd.DataFrame(np.random.randn(3, 3), index=['a', 'c', 'e'],columns=['one', 'two', 'three']) 
df = df.reindex(['a', 'b', 'c']) 
print(df)
```

            one       two     three
    a -0.974112 -0.107202  0.948507
    b       NaN       NaN       NaN
    c  1.349075 -0.230786 -0.301775



```python

print ("NaN replaced with '0':") 
print(df.fillna(0)) 
```

    NaN replaced with '0':
            one       two     three
    a -0.974112 -0.107202  0.948507
    b  0.000000  0.000000  0.000000
    c  1.349075 -0.230786 -0.301775



```python
 Here, we are filling with value zero; instead we can also fill with any other value.
```

 Fill NA Forward and Backward Using the concepts of filling discussed in the ReIndexing Chapter we will fill the missing values. Method Action pad/fill Fill methods Forward bfill/backfill Fill methods Backward Example 1 import pandas as pd import numpy as np



```python
df = pd.DataFrame(np.random.randn(5, 3), index=['a', 'c', 'e', 'f', 'h'],columns=['one', 'two', 'three']) 
df = df.reindex(['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h'])
print(df.fillna(method='pad'))
```

            one       two     three
    a -0.120354 -0.567879 -1.488691
    b -0.120354 -0.567879 -1.488691
    c  0.498990  1.137989  1.399107
    d  0.498990  1.137989  1.399107
    e -0.727994 -0.459767 -1.197081
    f  0.045633  0.783227  1.091397
    g  0.045633  0.783227  1.091397
    h -0.211237  1.594067  1.379605


#### Example 2


```python
import pandas as pd 
import numpy as np
df = pd.DataFrame(np.random.randn(5, 3), index=['a', 'c', 'e', 'f', 'h'],columns=['one', 'two', 'three'])
df = df.reindex(['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h']) 
print( df.fillna(method='backfill') )

```

            one       two     three
    a -3.315833 -0.561261 -0.939571
    b  2.091537  3.090447 -0.222618
    c  2.091537  3.090447 -0.222618
    d  1.364167  1.067958 -1.786327
    e  1.364167  1.067958 -1.786327
    f -0.142454 -0.718423  0.814255
    g -0.684668  0.563114 -0.302664
    h -0.684668  0.563114 -0.302664


#### Drop Missing Values 

If you want to simply exclude the missing values, then use the dropna function along with the axis argument. By default, axis=0, i.e., along row, which means that if any value within a row 
is NA then the whole row is excluded.

#### Example 1 


```python

import pandas as pd 
import numpy as np
df = pd.DataFrame(np.random.randn(5, 3), index=['a', 'c', 'e', 'f', 'h'],columns=['one', 'two', 'three'])
```


```python
df = df.reindex(['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h']) 
print df.dropna() 
```

#### Example 2 


```python
import pandas as pd 
import numpy as np
df = pd.DataFrame(np.random.randn(5, 3), index=['a', 'c', 'e', 'f', 'h'],columns=['one', 'two', 'three'])
df = df.reindex(['a', 'b', 'c', 'd', 'e', 'f', 'g', 'h']) 
print df.dropna(axis=1) 
Its output is as follows − Empty DataFrame Columns: [ ] Index: [a, b, c, d, e, f, g, h] Replace Missing (or) Generic Values Many times, we have to replace a generic value with some specific value. We can achieve this by applying the replace method. Replacing NA with a scalar value is equivalent behavior of the fillna() function. Example 1 import pandas as pd import numpy as np df = pd.DataFrame({'one':[10,20,30,40,50,2000], 'two':[1000,0,30,40,50,60]}) print df.replace({1000:10,2000:60}) Its output is as follows − one two 0 10 10 1 20 0 2 30 30 3 40 40 4 50 50 5 60 60 Example 2 import pandas as pd import numpy as np df = pd.DataFrame({'one':[10,20,30,40,50,2000], 'two':[1000,0,30,40,50,60]}) print df.replace({1000:10,2000:60}) Its output is as follows − one two 0 10 10 1 20 0 2 30 30 3 40 40 4 50 50 5 60 60

        
```
