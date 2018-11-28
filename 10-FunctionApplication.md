
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
def adder(ele1,ele2):
return ele1+ele2
We will now use the custom function to conduct operation on the DataFrame.
df = pd.DataFrame(np.random.randn(5,3),columns=['col1','col2','col3'])
df.pipe(adder,2)
Let’s see the full program −
import pandas as pd
import numpy as np

def adder(ele1,ele2):
   return ele1+ele2

df = pd.DataFrame(np.random.randn(5,3),columns=['col1','col2','col3'])
df.pipe(adder,2)
print df.apply(np.mean)
Its output is as follows −
        col1       col2       col3
0   2.176704   2.219691   1.509360
1   2.222378   2.422167   3.953921
2   2.241096   1.135424   2.696432
3   2.355763   0.376672   1.182570
4   2.308743   2.714767   2.130288
Row or Column Wise Function Application
Arbitrary functions can be applied along the axes of a DataFrame or Panel using the apply() method, which, like the descriptive statistics methods, takes an optional axis argument. By default, the operation performs column wise, taking each column as an array-like.
Example 1
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
Example 2
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
Example 3
import pandas as pd
import numpy as np

df = pd.DataFrame(np.random.randn(5,3),columns=['col1','col2','col3'])
df.apply(lambda x: x.max() - x.min())
print df.apply(np.mean)
Its output is as follows −
       col1        col2      col3
                                                   
0   -0.585206   -0.104938   1.424115 
                                   
1   -0.326036   -1.444798   0.196849 
                                              
2   -2.033478    1.682253   1.223152  
                                            
3   -0.107015    0.499846   0.084127
         
4   -1.046964   -1.935617  -0.009919
Element Wise Function Application
Not all functions can be vectorized (neither the NumPy arrays which return another array nor any value), the methods applymap() on DataFrame and analogously map() on Series accept any Python function taking a single value and returning a single value.
Example 1
import pandas as pd
import numpy as np
df = pd.DataFrame(np.random.randn(5,3),columns=['col1','col2','col3'])

# My custom function
df['col1'].map(lambda x:x*100)
print df.apply(np.mean)
Its output is as follows −
       col1      col2       col3    
		
0    0.629348  0.088467  -1.790702 
                                               
1   -0.592595  0.184113  -1.524998

2   -0.419298  0.262369  -0.178849

3   -1.036930  1.103169   0.941882 

4   -0.573333 -0.031056   0.315590
Example 2
import pandas as pd
import numpy as np

# My custom function
df = pd.DataFrame(np.random.randn(5,3),columns=['col1','col2','col3'])
df.applymap(lambda x:x*100)
print df.apply(np.mean)
Its output is as follows −
output is as follows:
         col1         col2         col3
0   17.670426    21.969052    -49.064031
1   22.237846    42.216693     195.392124
2   24.109576   -86.457646     69.643171
3   35.576312   -162.332803   -81.743023
4   30.874333    71.476717     13.028751


