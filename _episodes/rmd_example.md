This is an R Markdown document.


```r
x <- rnorm(1000)
head(x)
```

```
## [1] -1.16375140 -0.48232892 -0.04950121 -1.94006228 -0.16842030  0.87071515
```

`knitr` offers a lot of control over representing different
types of output. We can also have inline `R` expressions
computed on the fly.

The mean $\bar{x} = \frac{1}{n} \sum_{i=1}^{n} x_{i}$ of the
1000 random variates we generated is
0.051.

This figure is computed on-the-fly as well. No more
copy-paste, including for figures:


```r
plot(density(x))
```

![plot of chunk sec_4](figure/sec_4-1.png)
