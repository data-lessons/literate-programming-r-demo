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

<pre><code>## [1] -0.66386327 -1.62717975  0.06098557  1.29772208  0.41090427 -0.31804688
</code></pre>

<p><code>knitr</code> offers a lot of control over representing different
types of output. We can also have inline <code>R</code> expressions
computed on the fly.</p>

<p>The mean \(\bar{x} = \frac{1}{n} \sum_{i=1}^{n} x_{i}\) of the
1000 random variates we generated is
-0.013.</p>

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
