

```python

Python Pandas - Categorical Data

Often in real-time, data includes the text columns, which are repetitive. Features like gender, country, and codes are always repetitive. These are the examples for categorical data.
Categorical variables can take on only a limited, and usually fixed number of possible values. Besides the fixed length, categorical data might have an order but cannot perform numerical operation. Categorical are a Pandas data type.
The categorical data type is useful in the following cases −
A string variable consisting of only a few different values. Converting such a string variable to a categorical variable will save some memory.
The lexical order of a variable is not the same as the logical order (“one”, “two”, “three”). By converting to a categorical and specifying an order on the categories, sorting and min/max will use the logical order instead of the lexical order.
As a signal to other python libraries that this column should be treated as a categorical variable (e.g. to use suitable statistical methods or plot types).

```


```python
Object Creation
Categorical object can be created in multiple ways. The different ways have been described below −
category
By specifying the dtype as "category" in pandas object creation.
import pandas as pd
s = pd.Series(["a","b","c","a"], dtype="category")
print s
```


```python

Its output is as follows −
0  a
1  b
2  c
3  a
dtype: category
Categories (3, object): [a, b, c]
```


```python
The number of elements passed to the series object is four, but the categories are only three. Observe the same in the output Categories.
pd.Categorical
Using the standard pandas Categorical constructor, we can create a category object.
pandas.Categorical(values, categories, ordered)
Let’s take an example −
import pandas as pd
cat = pd.Categorical(['a', 'b', 'c', 'a', 'b', 'c'])
print cat
Its output is as follows −
[a, b, c, a, b, c]
Categories (3, object): [a, b, c]
```


```python

Let’s have another example −
import pandas as pd
cat = cat=pd.Categorical(['a','b','c','a','b','c','d'], ['c', 'b', 'a'])
print cat
Its output is as follows −
[a, b, c, a, b, c, NaN]
Categories (3, object): [c, b, a]
```


```python

Here, the second argument signifies the categories. Thus, any value which is not present in the categories will be treated as NaN.
Now, take a look at the following example −
import pandas as pd
cat = cat=pd.Categorical(['a','b','c','a','b','c','d'], ['c', 'b', 'a'],ordered=True)
print cat
Its output is as follows −
[a, b, c, a, b, c, NaN]
Categories (3, object): [c < b < a]
Logically, the order means that, a is greater than b and b is greater than c.
```


```python


Description
Using the .describe() command on the categorical data, we get similar output to a Series or DataFrame of the type string.
import pandas as pd
import numpy as np

cat = pd.Categorical(["a", "c", "c", np.nan], categories=["b", "a", "c"])
df = pd.DataFrame({"cat":cat, "s":["a", "c", "c", np.nan]})
print df.describe()

print df["cat"].describe()
Its output is as follows −
       cat s
count    3 3
unique   2 2
top      c c
freq     2 2
count     3
unique    2
top       c
freq      2
Name: cat, dtype: object
```


```python

Get the Properties of the Category
obj.cat.categories command is used to get the categories of the object.
import pandas as pd
import numpy as np

s = pd.Categorical(["a", "c", "c", np.nan], categories=["b", "a", "c"])
print s.categories
Its output is as follows −
Index([u'b', u'a', u'c'], dtype='object')
obj.ordered command is used to get the order of the object.
import pandas as pd
import numpy as np

cat = pd.Categorical(["a", "c", "c", np.nan], categories=["b", "a", "c"])
print cat.ordered
Its output is as follows −
False
The function returned false because we haven't specified any order.
```


```python
Renaming Categories
Renaming categories is done by assigning new values to the series.cat.categoriesseries.cat.categories property.
import pandas as pd

s = pd.Series(["a","b","c","a"], dtype="category")
s.cat.categories = ["Group %s" % g for g in s.cat.categories]

print s.cat.categories
Its output is as follows −
Index([u'Group a', u'Group b', u'Group c'], dtype='object')
Initial categories [a,b,c] are updated by the s.cat.categories property of the object.

```


```python
Appending New Categories
Using the Categorical.add.categories() method, new categories can be appended.
import pandas as pd

s = pd.Series(["a","b","c","a"], dtype="category")
s = s.cat.add_categories([4])
print s.cat.categories
Its output is as follows −
Index([u'a', u'b', u'c', 4], dtype='object')
```


```python
Removing Categories
Using the Categorical.remove_categories() method, unwanted categories can be removed.

```


```python
import pandas as pd

s = pd.Series(["a","b","c","a"], dtype="category")
print ("Original object:")
print (s)

print ("After removal:")
print (s.cat.remove_categories("a"))
```

    Original object:
    0    a
    1    b
    2    c
    3    a
    dtype: category
    Categories (3, object): [a, b, c]
    After removal:
    0    NaN
    1      b
    2      c
    3    NaN
    dtype: category
    Categories (2, object): [b, c]



```python



Comparison of Categorical Data
Comparing categorical data with other objects is possible in three cases −
comparing equality (== and !=) to a list-like object (list, Series, array, ...) of the same length as the categorical data.
all comparisons (==, !=, >, >=, <, and <=) of categorical data to another categorical Series, when ordered==True and the categories are the same.
all comparisons of a categorical data to a scalar.
Take a look at the following example −
import pandas as pd

cat = pd.Series([1,2,3]).astype("category", categories=[1,2,3], ordered=True)
cat1 = pd.Series([2,2,2]).astype("category", categories=[1,2,3], ordered=True)

print cat>cat1
Its output is as follows −
0  False
1  False
2  True
dtype: bool



```
