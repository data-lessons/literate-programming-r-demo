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

<pre><code>## [1]  0.12144253 -0.44967167  1.70512442 -0.44942038  0.04998372 -2.02348204
</code></pre>

<p><code>knitr</code> offers a lot of control over representing different
types of output. We can also have inline <code>R</code> expressions
computed on the fly.</p>

<p>The mean \(\bar{x} = \frac{1}{n} \sum_{i=1}^{n} x_{i}\) of the
1000 random variates we generated is
0.014.</p>

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
