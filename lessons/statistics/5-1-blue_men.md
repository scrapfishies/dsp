[Think Stats Chapter 5 Exercise 1](http://greenteapress.com/thinkstats2/html/thinkstats2006.html#toc50) (blue men)

### Solution

If the mean height of the population is 178cm, then **34%** of the population falls within the range 5'10" and 6'1"

```
# 5'10"
low = dist.cdf(177.8)

# 6'01"
high = dist.cdf(185.4)

print('Low: ', low)
print('High: ', high)
print('Percent in range: ', (high-low))
```

Returns: 
```
Low:  0.48963902786483265
High:  0.8317337108107857
Percent in range:  0.3420946829459531
```
