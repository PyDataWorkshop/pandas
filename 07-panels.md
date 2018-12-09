

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


```python

From dict of DataFrame Objects
#creating an empty panel
import pandas as pd
import numpy as np

data = {'Item1' : pd.DataFrame(np.random.randn(4, 3)), 
        'Item2' : pd.DataFrame(np.random.randn(4, 2))}
p = pd.Panel(data)
print p
```


```python



Its output is as follows −
<class 'pandas.core.panel.Panel'>
Dimensions: 2 (items) x 4 (major_axis) x 5 (minor_axis)
Items axis: 0 to 1
Major_axis axis: 0 to 3
Minor_axis axis: 0 to 4
```


```python


Create an Empty Panel
An empty panel can be created using the Panel constructor as follows −
#creating an empty panel
import pandas as pd
p = pd.Panel()
print p
```


```python

Its output is as follows −
<class 'pandas.core.panel.Panel'>
Dimensions: 0 (items) x 0 (major_axis) x 0 (minor_axis)
Items axis: None
Major_axis axis: None
Minor_axis axis: None
Selecting the Data from Panel
Select the data from the panel using −
Items
Major_axis
Minor_axis


```


```python
Using Items
# creating an empty panel
import pandas as pd
import numpy as np
data = {'Item1' : pd.DataFrame(np.random.randn(4, 3)), 
        'Item2' : pd.DataFrame(np.random.randn(4, 2))}
p = pd.Panel(data)
print p['Item1']
```


```python

We have two items, and we retrieved item1. The result is a DataFrame with 4 rows and 3 columns, which are the Major_axis and Minor_axis dimensions.

```


```python
Using major_axis
Data can be accessed using the method panel.major_axis(index).
```


```python

# creating an empty panel
import pandas as pd
import numpy as np
data = {'Item1' : pd.DataFrame(np.random.randn(4, 3)), 
        'Item2' : pd.DataFrame(np.random.randn(4, 2))}
p = pd.Panel(data)
print p.major_xs(1)
Its output is as follows −
      Item1       Item2
0   0.417497    0.748412
1   0.896681   -0.557322
2   0.576657       NaN

```


```python
Using minor_axis
Data can be accessed using the method panel.minor_axis(index).
# creating an empty panel
import pandas as pd
import numpy as np
data = {'Item1' : pd.DataFrame(np.random.randn(4, 3)), 
        'Item2' : pd.DataFrame(np.random.randn(4, 2))}
p = pd.Panel(data)
print p.minor_xs(1)
```


```python

Its output is as follows −
       Item1       Item2
0   -0.128637   -1.047032
1    0.896681   -0.557322
2    0.571668    0.431953
3   -0.144234    1.302466
Note − Observe the changes in the dimensions.

```
