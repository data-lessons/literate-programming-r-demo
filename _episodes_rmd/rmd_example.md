This is an R Markdown document.


```r
x <- rnorm(1000)
head(x)
```

```
## [1] -1.65595149 -0.04217995 -0.58489357  0.33215404  0.33348650 -0.31246516
```

`knitr` offers a lot of control over representing different
types of output. We can also have inline `R` expressions
computed on the fly.

The mean $\bar{x} = \frac{1}{n} \sum_{i=1}^{n} x_{i}$ of the
1000 random variates we generated is
-0.039.

This figure is computed on-the-fly as well. No more
copy-paste, including for figures:


```r
plot(density(x))
```

<img src="../figure/sec_4-1.png" title="plot of chunk sec_4" alt="plot of chunk sec_4" style="display: block; margin: auto;" />
