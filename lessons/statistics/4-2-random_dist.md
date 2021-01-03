[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)

```python
%matplotlib inline
import numpy as np
import nsfg
import first
import thinkstats2
import thinkplot
```


```python
t = np.random.random(1000)
```


```python
pmf = thinkstats2.Pmf(t)
thinkplot.Pmf(pmf, linewidth=0.1)
thinkplot.Config(xlabel='Random variate', ylabel='PMF')
```


    
![png](output_2_0.png)
    



```python
cdf = thinkstats2.Cdf(t)
thinkplot.Cdf(cdf)
thinkplot.Config(xlabel='Random variate', ylabel='CDF')
```


    
![png](output_1_0.png)
