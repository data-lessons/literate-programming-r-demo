This is an R Markdown document.


```r
x <- rnorm(1000)
head(x)
```

```
## [1]  0.4612714  0.4212846 -0.7780861  1.8116113  0.2671053  0.2130036
```

`knitr` offers a lot of control over representing different
types of output. We can also have inline `R` expressions
computed on the fly.

The mean $\bar{x} = \frac{1}{n} \sum_{i=1}^{n} x_{i}$ of the
1000 random variates we generated is
0.021.

This figure is computed on-the-fly as well. No more
copy-paste, including for figures:


```r
plot(density(x))
```

![plot of chunk sec_4](figure/sec_4-1.png)
