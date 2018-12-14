
Python Pandas - Function Application


To apply your own or another library’s functions to Pandas objects, you should be aware of the three important methods. The methods have been discussed below. The appropriate method to use depends on whether your function expects to operate on an entire DataFrame, row- or column-wise, or element wise.


Table wise Function Application: pipe()
Row or Column Wise Function Application: apply()
Element wise Function Application: applymap()

Table-wise Function Application
Custom operations can be performed by passing the function and the appropriate number of parameters as pipe arguments. Thus, operation is performed on the whole DataFrame.
For example, add a value 2 to all the elements in the DataFrame. Then,
adder function
The adder function adds two numeric values as parameters and returns the sum.


```python
def adder(ele1,ele2):
  return ele1+ele2
```




We will now use the custom function to conduct operation on the DataFrame.


```python
df = pd.DataFrame(np.random.randn(5,3),columns=['col1','col2','col3'])
df.pipe(adder,2)
Let’s see the full program −

```


```python
import pandas as pd
import numpy as np

def adder(ele1,ele2):
   return ele1+ele2

df = pd.DataFrame(np.random.randn(5,3),columns=['col1','col2','col3'])
df.pipe(adder,2)
print df.apply(np.mean)
```

### Row or Column Wise Function Application
Arbitrary functions can be applied along the axes of a DataFrame or Panel using 
the ``apply()`` method, which, like the descriptive statistics methods, takes an optional 
axis argument. By default, the operation performs column wise, taking each column as an array-like.


#### Example 1



```python
import pandas as pd
import numpy as np

df = pd.DataFrame(np.random.randn(5,3),columns=['col1','col2','col3'])
df.apply(np.mean)
print df.apply(np.mean)
Its output is as follows −
      col1       col2        col3                                                      
0   0.343569  -1.013287    1.131245 

1   0.508922  -0.949778   -1.600569 

2  -1.182331  -0.420703   -1.725400

3   0.860265   2.069038   -0.537648

4   0.876758  -0.238051    0.473992
By passing axis parameter, operations can be performed row wise.

```

#### Example 2


```python

import pandas as pd
import numpy as np

df = pd.DataFrame(np.random.randn(5,3),columns=['col1','col2','col3'])
df.apply(np.mean,axis=1)
print df.apply(np.mean)
Its output is as follows −
     col1         col2         col3
	
0  0.543255    -1.613418    -0.500731   
           
1  0.976543    -1.135835    -0.719153   
                
2  0.184282    -0.721153    -2.876206    
              
3  0.447738     0.268062    -1.937888
                
4 -0.677673     0.177455     1.397360  
```


```python
Example 3
import pandas as pd
import numpy as np

df = pd.DataFrame(np.random.randn(5,3),columns=['col1','col2','col3'])
df.apply(lambda x: x.max() - x.min())
print df.apply(np.mean)
```


```python
### Element Wise Function Application
Not all functions can be vectorized (neither the NumPy arrays which return another array nor any value), the methods applymap() on DataFrame and analogously map() on Series accept any Python function taking a single value and returning a single value.




```

## Example 1



```python
import pandas as pd
import numpy as np
df = pd.DataFrame(np.random.randn(5,3),columns=['col1','col2','col3'])

# My custom function
df['col1'].map(lambda x:x*100)
print df.apply(np.mean)

```

## Example 2


```python

import pandas as pd
import numpy as np

# My custom function
df = pd.DataFrame(np.random.randn(5,3),columns=['col1','col2','col3'])
df.applymap(lambda x:x*100)
print df.apply(np.mean)

```
