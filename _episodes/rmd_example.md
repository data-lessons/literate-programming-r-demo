This is an R Markdown document.


```r
x <- rnorm(1000)
head(x)
```

```
## [1] -0.9599859 -0.8732070 -0.4101692  0.1285310  1.5587955 -1.0686579
```

`knitr` offers a lot of control over representing different
types of output. We can also have inline `R` expressions
computed on the fly.

The mean $\bar{x} = \frac{1}{n} \sum_{i=1}^{n} x_{i}$ of the
1000 random variates we generated is
0.012.

This figure is computed on-the-fly as well. No more
copy-paste, including for figures:


```r
plot(density(x))
```

![plot of chunk sec_4](figure/sec_4-1.png)
