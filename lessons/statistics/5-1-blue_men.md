[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

```python
%matplotlib inline
import numpy as np
import nsfg
import first
import analytic
import thinkstats2
import thinkplot
import scipy.stats
```


```python
mu = 178
sigma = 7.7
dist = scipy.stats.norm(loc=mu, scale=sigma)
type(dist)
```




    scipy.stats._distn_infrastructure.rv_frozen




```python
dist.mean(), dist.std()
```




    (178.0, 7.7)




```python
#How many people are more than one standard deviation below the mean? 
dist.cdf(mu-sigma)
```




    0.1586552539314574




```python
#How many people are between 5'10" and 6'1"
low = dist.cdf(177.8)    # 5'10"
high = dist.cdf(185.4)   # 6'1"
low, high, high-low
```




    (0.48963902786483265, 0.8317337108107857, 0.3420946829459531)



