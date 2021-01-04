[Think Stats Chapter 2 Exercise 4](http://greenteapress.com/thinkstats2/html/thinkstats2003.html#toc24) (Cohen's d)

```python
import nsfg
import numpy as np
```


```python
preg = nsfg.ReadFemPreg()
live = preg[preg.outcome == 1]
```


```python
firsts = live[live.birthord == 1]
others = live[live.birthord != 1]
```


```python
def CohenEffectSize(group1, group2):
    """Computes Cohen's effect size for two groups.

    group1: Series or DataFrame
    group2: Series or DataFrame

    returns: float if the arguments are Series;
             Series if the arguments are DataFrames
    """
    diff = group1.mean() - group2.mean()

    var1 = group1.var()
    var2 = group2.var()
    n1, n2 = len(group1), len(group2)

    pooled_var = (n1 * var1 + n2 * var2) / (n1 + n2)
    d = diff / np.sqrt(pooled_var)
    return d
```


```python
#investigate whether first babies are lighter or heavier than others
print("First babies have a mean weight of {}".format(firsts.totalwgt_lb.mean()))
print("Other babies have a mean weight of {}".format(others.totalwgt_lb.mean()))
print("The difference in means between first and other babies' weight is {}".format(firsts.totalwgt_lb.mean() - others.totalwgt_lb.mean()))
```

    First babies have a mean weight of 7.201094430437772
    Other babies have a mean weight of 7.325855614973262
    The difference in means between first and other babies' weight is -0.12476118453549034



```python
#Compute Cohen's effect size to quantify the difference between the groups
CohenEffectSize(firsts.totalwgt_lb, others.totalwgt_lb)
```




    -0.088672927072602




```python
#How does it compare to the difference in pregnancy length?
print("First babies have a mean length of {}".format(firsts.prglngth.mean()))
print("Other babies have a mean lenghh of {}".format(others.prglngth.mean()))
print("The difference in means between first and other babies' length is {}".format(firsts.prglngth.mean() - others.prglngth.mean()))
```

    First babies have a mean length of 38.60095173351461
    Other babies have a mean lenghh of 38.52291446673706
    The difference in means between first and other babies' length is 0.07803726677754952



```python
CohenEffectSize(firsts.prglngth, others.prglngth)
```




    0.028879044654449883

