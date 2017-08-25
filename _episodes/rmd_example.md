This is an R Markdown document.


```r
x <- rnorm(1000)
head(x)
```

```
## [1] -2.8270161 -1.0091592 -0.7799536  0.2725977  0.6892072 -0.1488466
```

`knitr` offers a lot of control over representing different
types of output. We can also have inline `R` expressions
computed on the fly.

The mean $\bar{x} = \frac{1}{n} \sum_{i=1}^{n} x_{i}$ of the
1000 random variates we generated is
0.003.

This figure is computed on-the-fly as well. No more
copy-paste, including for figures:


```r
plot(density(x))
```

![plot of chunk sec_4](figure/sec_4-1.png)
