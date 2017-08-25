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

<pre><code>## [1] -1.65595149 -0.04217995 -0.58489357  0.33215404  0.33348650 -0.31246516
</code></pre>

<p><code>knitr</code> offers a lot of control over representing different
types of output. We can also have inline <code>R</code> expressions
computed on the fly.</p>

<p>The mean \(\bar{x} = \frac{1}{n} \sum_{i=1}^{n} x_{i}\) of the
1000 random variates we generated is
-0.039.</p>

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
