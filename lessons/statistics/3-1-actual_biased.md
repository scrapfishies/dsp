[Think Stats Chapter 3 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2004.html#toc31) (actual vs. biased)

#### Solution: 

1. PMF calculation for `numkdhh`: 
```javascript
num_kids = thinkstats2.Pmf(resp.numkdhh, label='numkdhh')
```

2. Plotting actual distribution of PMF of numkdhh: 
```javascript
thinkplot.Hist(num_kids)
thinkplot.Config(xlabel='Number of kids per HH', ylabel='Pmf')
```

3. Calculating *Biased* distribution for `numkidhh`
```javascript
biased_num_kids = BiasPmf(num_kids, label='biased')
```

4. Plotting both distributions: 
```javascript
thinkplot.PrePlot(2)
thinkplot.Pmfs([num_kids, biased_num_kids])
thinkplot.Config(xlabel='Number of kids per HH', ylabel='PMF')
```

5. Calculating means of actual and biased
```javascript
print("Actual Mean: {}".format(num_kids.Mean()))
print("Biased Mean: {}".format(biased_num_kids.Mean()))
```
Returns: 
>> Actual Mean: 1.024205155043831

>> Biased Mean: 2.403679100664282
