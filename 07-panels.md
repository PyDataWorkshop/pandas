

```python
Python Pandas - Panel


A panel is a 3D container of data. The term Panel data is derived from econometrics and is partially responsible for the name pandas − pan(el)-da(ta)-s.
The names for the 3 axes are intended to give some semantic meaning to describing operations involving panel data. They are −

```


```python
items − axis 0, each item corresponds to a DataFrame contained inside.
major_axis − axis 1, it is the index (rows) of each of the DataFrames.
minor_axis − axis 2, it is the columns of each of the DataFrames.
```


```python
####  pandas.Panel()
A Panel can be created using the following constructor −
pandas.Panel(data, items, major_axis, minor_axis, dtype, copy)
```


```python

The parameters of the constructor are as follows −
Parameter
Description
data
Data takes various forms like ndarray, series, map, lists, dict, constants and also another DataFrame
items

axis=0 major_axis 
axis=1 minor_axis axis=2
dtype Data type of each column
copy Copy data. Default, false
```


```python
Create Panel
A Panel can be created using multiple ways like −
```


```python

From ndarrays
From dict of DataFrames
From 3D ndarray
# creating an empty panel
import pandas as pd
import numpy as np

data = np.random.rand(2,4,5)
p = pd.Panel(data)
print p
Its output is as follows −
<class 'pandas.core.panel.Panel'>
```


```python
Dimensions: 2 (items) x 4 (major_axis) x 5 (minor_axis)
Items axis: 0 to 1
Major_axis axis: 0 to 3
Minor_axis axis: 0 to 4
Note − Observe the dimensions of the empty panel and the above panel, all the objects are different.
```


From dict of DataFrame Objects


```python

#creating an empty panel
import pandas as pd
import numpy as np

data = {'Item1' : pd.DataFrame(np.random.randn(4, 3)), 
        'Item2' : pd.DataFrame(np.random.randn(4, 2))}
p = pd.Panel(data)
print(p)
```

    <class 'pandas.core.panel.Panel'>
    Dimensions: 2 (items) x 4 (major_axis) x 3 (minor_axis)
    Items axis: Item1 to Item2
    Major_axis axis: 0 to 3
    Minor_axis axis: 0 to 2


#### Create an Empty Panel
An empty panel can be created using the Panel constructor as follows −



```python



#creating an empty panel
import pandas as pd
p = pd.Panel()
print( p)
```

    <class 'pandas.core.panel.Panel'>
    Dimensions: 0 (items) x 0 (major_axis) x 0 (minor_axis)
    Items axis: None
    Major_axis axis: None
    Minor_axis axis: None



```python

Selecting the Data from Panel
Select the data from the panel using −
Items
Major_axis
Minor_axis


```


```python
Using Items
```


```python

# creating an empty panel
import pandas as pd
import numpy as np
data = {'Item1' : pd.DataFrame(np.random.randn(4, 3)), 
        'Item2' : pd.DataFrame(np.random.randn(4, 2))}
p = pd.Panel(data)
print( p['Item1'])
```

              0         1         2
    0  0.466986  0.113181 -0.101598
    1 -1.580081 -0.486969 -0.635157
    2  0.447368 -0.365751 -1.103188
    3 -2.189870 -1.532149 -0.092267



```python

We have two items, and we retrieved item1. The result is a DataFrame with 4 rows and 3 columns, which are the Major_axis and Minor_axis dimensions.

```

#### Using ``major_axis``
Data can be accessed using the method panel.major_axis(index).


```python

# creating an empty panel
import pandas as pd
import numpy as np
data = {'Item1' : pd.DataFrame(np.random.randn(4, 3)), 
        'Item2' : pd.DataFrame(np.random.randn(4, 2))}
p = pd.Panel(data)
print(p.major_xs(1))
```

          Item1     Item2
    0 -0.123539  0.044385
    1  0.853580 -0.090721
    2  1.467704       NaN



```python
#### Using ``minor_axis``
Data can be accessed using the method panel.minor_axis(index).
```


```python

# creating an empty panel
import pandas as pd
import numpy as np
data = {'Item1' : pd.DataFrame(np.random.randn(4, 3)), 
        'Item2' : pd.DataFrame(np.random.randn(4, 2))}
p = pd.Panel(data)
print(p.minor_xs(1))
```

          Item1     Item2
    0 -0.464770 -0.897153
    1  0.656290 -1.009466
    2 -0.288655 -0.702532
    3 -0.749870 -0.087685



Note − Observe the changes in the dimensions.

