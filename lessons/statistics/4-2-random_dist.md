[Think Stats Chapter 4 Exercise 2](http://greenteapress.com/thinkstats2/html/thinkstats2005.html#toc41) (a random distribution)

### Solution

#### Plotting PMF 
Generate 1000 numbers using `numpy.random.random` and plot their PMF: 

```javascript
# Generate 1000 random numbers
rando = np.random.random(1000)

# Calculate PMF
rando_pmf = thinkstats2.Pmf(rando)

# Plot rando PMF
thinkplot.Pmf(rando_pmf, linewidth=0.1)
thinkplot.Config(xlabel='Random Numbers', ylabel='PMF')
```
It's not that anything *goes wrong* per se; however, because we have a truly random sampling of 1000 numbers between 0 and 1, they have a **uniform distribution** - each number has the same probability of occuring as every other number, which is 0.001 or 0.1%. 

#### Plotting CDF
```javascript
rando_cdf = thinsktats2.Cdf(rando, label='Rando CDF')
thinkplot.Cdf(rando_cdf)
thinkplot.Config(xlabel='Percentile Rank', ylabel='CDF', loc='upper left')
```

Plotting the CDF of `rando` confirms what we saw in the PMF plot - a **uniform distribution**. However rather than seeing each random number in `rando` as having an equal probability of occurance (0.001 or 0.1%), we see a straight line where CDF is approximately equal to Percentile Rank indicating that the distribution of *percentile ranks* is uniform. 


[Link to chapter code and exercises](https://github.com/scrapfishies/ThinkStats2/blob/master/code/chap04ex.ipynb)
