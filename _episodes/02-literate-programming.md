---
title: "Literate programming"
teaching: 30
exercises: 10
questions:
- "What tools are available to easily disseminate our work?"
- "How can we make our work more reproducible?"
objectives:
- "Learn the basics of `RMarkdown` and `knitr`"
- "Learn to integrate `R` code with text and images."
keypoints:
- "`RMarkdown` and `knitr` are powerful tools."
- "Output can be rendered in many formats."
- "You don't need to know HTML!"
output:
      html_document
---



> ## 2. Literate programming
>
> - Organize your work
> - make work more pleasant for yourself? (less tedium, less manual, less ...)
> - reduce friction for collaboration?
> - reduce friction for communication?
> - make your work navigable, interpretable, and repeatable by others?
{: .objectives}

#### Getting the analysis right is only one link

Process, packaging, and presentation are often the weak links in the chain.
![](../media/brokenChain.jpg)


## Markdown

### What is Markdown?

- `Markdown` is a particular type of markup language. Markup languages are designed to produce documents from plain text.
- You may be familiar with `LaTeX`, another (though less human friendly) text markup language.
- Tools render markdown to different formats (for example, HTML/pdf/Word).
  - The main tool for rendering Markdown is [pandoc](http://pandoc.org/).

Adapted from [Carson Sievert's markdown slides](http://cpsievert.github.io/slides/markdown/#/1)


### Markdown enables fast publication to the web

- **Markdown** Easy to write and read in an editor.
- **HTML** Easy to publish and read on web.

### Markdown versus HTML code

<div class="row">

<div class="col-md-6">

<pre>
This is a Markdown document.

## Medium header <!-- header 2, actually -->

It's easy to do *italics* or __make things bold__.

> All models are wrong, but some are useful. An approximate answer to the right problem is worth a good deal more than an exact answer to an approximate problem.

Code block below. Just affects formatting here.

```
x <- 3 * 4
```

I can haz equations. Inline equations, such as the average is computed as $\frac{1}{n} \sum_{i=1}^{n} x_{i}$. Or display equations like this:


$$
\begin{equation*}
|x|=
\begin{cases} x & \text{if $x\ge 0$,} \\\\
-x &\text{if $x\lt 0$.}
\end{cases}
\end{equation*}
$$
</pre>

<img src="../media/smiley-face-clipart.png"/>

</div> <!-- end column left -->


<div class="col-md-6">

<pre>

&lt;!DOCTYPE html&gt;
&lt;html&gt;
&lt;head&gt;
&lt;meta http-equiv="Content-Type" content="text/html; charset=utf-8"/&gt;
&lt;title&gt;Title&lt;/title&gt;
&lt;!-- MathJax scripts --&gt;
&lt;script type="text/javascript" src="..."&gt;&lt;/script&gt;
&lt;style type="text/css"&gt;
body {
   font-family: Helvetica, arial, sans-serif;
   font-size: 14px;
...
&lt;/style&gt;
&lt;/head&gt;
&lt;body&gt;
&lt;p&gt;This is a Markdown document.&lt;/p&gt;

&lt;h2&gt;Medium header&lt;/h2&gt;

&lt;p&gt;It's easy to do &lt;em&gt;italics&lt;/em&gt; or &lt;strong&gt;make things bold&lt;/strong&gt;.&lt;/p&gt;

&lt;blockquote&gt;&lt;p&gt;All models are wrong, but some are...&lt;/p&gt;&lt;/blockquote&gt;

&lt;p&gt;Code block below. Just affects formatting here.&lt;/p&gt;

&lt;pre&gt;&lt;code&gt;x &lt;- 3 * 4&lt;/code&gt;&lt;/pre&gt;

</pre>
 <img src="../media/frowny-face-clipart.png"/>
</div> <!-- end column right -->
</div> <!-- end 2-column row -->

### Markdown versus rendered HTML

<div class="row">
<div class="col-md-6">
<pre>

This is a Markdown document.

## Medium header <!-- header 2, actually -->

It's easy to do *italics* or __make things bold__.

> All models are wrong, but some are useful. An approximate answer to the right problem is worth a good deal more than an exact answer to an approximate problem.

Code block below. Just affects formatting here.


```r
x <- 3 * 4
```

I can haz equations. Inline equations, such as the average is computed as $\frac{1}{n} \sum_{i=1}^{n} x_{i}$. Or display equations like this:

$$
\begin{equation*}
|x|=
\begin{cases} x & \text{if $x\ge 0$,} \\
-x &\text{if $x\lt 0$.}
\end{cases}
\end{equation*}
$$

</pre>

<img src="../media/smiley-face-clipart.png"/>

</div>

<div class="col-md-6">

<p>This is a Markdown document.</p>

<h2>Medium header</h2>

<p>It&#39;s easy to do <em>italics</em> or <strong>make things bold</strong>.</p>

<blockquote>
<p>All models are wrong, but some are useful. An approximate answer to the right problem is worth a good deal more than an exact answer to an approximate problem.</p>
</blockquote>

<p>Code block below. Just affects formatting here.</p>

<p><code>x &lt;- 3 * 4</code></p>

<p>I can haz equations. Inline equations, such as the average is computed as \(\frac{1}{n} \sum_{i=1}^{n} x_{i}\).</p>

<p>Or display equations like this:</p>

<p>\[
  \begin{equation*}
    |x|=
         \begin{cases}
      x & \text{if $x\ge 0$,} \
      -x & \text{if $x\lt 0$.}
        \end{cases}
   \end{equation*}
   \]</p>
<img src="../media/smiley-face-clipart.png"/>
</div>
</div>


## Markdown can be rendered to multiple formats

- `pandoc` is a Swiss-army knife tool for conversion`

![](../media/pandoc-diagram.jpg)



## RMarkdown

`RMarkdown` is rendered to Markdown. The strength of RMarkdown, is that with an easy syntax, it is possible to mix ideas, code, and generated results seamlessly.


### Input

````
This is an R Markdown document.

```{r sec_3}
x <- rnorm(1000)
head(x)
```

`knitr` offers a lot of control over representing different
types of output. We can also have inline `R` expressions
computed on the fly.

The mean $\bar{x} = \frac{1}{n} \sum_{i=1}^{n} x_{i}$ of the
`r length(x)` random variates we generated is
`r round(mean(x), 3)`.

This figure is computed on-the-fly as well. No more
copy-paste, including for figures:

```{r sec_4}
plot(density(x))
```
````


### Output

<p>This is an R Markdown document.</p>

<pre><code class="r">x &lt;- rnorm(1000)
head(x)
</code></pre>

<pre><code>## [1] -1.2685124  1.1099356 -1.0160079 -0.2135524  1.7670491  0.2663367
</code></pre>

<p><code>knitr</code> offers a lot of control over representing different
types of output. We can also have inline <code>R</code> expressions
computed on the fly.</p>

<p>The mean \(\bar{x} = \frac{1}{n} \sum_{i=1}^{n} x_{i}\) of the
1000 random variates we generated is
0.073.</p>

<p>This figure is computed on-the-fly as well. No more
copy-paste, including for figures:</p>

<pre><code class="r">plot(density(x))
</code></pre>

<p><img src="data:image/png;base64,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" title="plot of chunk sec_4" alt="plot of chunk sec_4" style="display: block; margin: auto;" /></p>



## Rendering can be automated is thus repeatable

![](../media/knitrButton-screenshot.png)


From within `R`:

`rmarkdown::render("filename.Rmd")`

From the command line:

`$ Rscript -e "rmarkdown::render('filename.Rmd')"`


## Summary

- `RMarkdown` enables ideas and questions, the code that implements them, and the results generated by the implementation, to all stay together.
- `RMarkdown` toolchain allows automated, repeatable rendering
  - for publishing to the web and viewing through a browser
  - and (through `LaTeX`) to obtain a submittable manuscript (in PDF or Word).
- `knitr` is not limited to executing `R` code. See the book Dynamic documents with `R` and `knitr` by Yihui Xie, part of the CRC Press / Chapman & Hall R Series (2013). [ISBN](http://www.isbnsearch.org/isbn/9781482203530)
