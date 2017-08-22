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

<pre><code>## [1] -0.7060215 -0.7536301 -2.5110508 -1.8531740  0.8036938 -0.1394521
</code></pre>

<p><code>knitr</code> offers a lot of control over representing different
types of output. We can also have inline <code>R</code> expressions
computed on the fly.</p>

<p>The mean \(\bar{x} = \frac{1}{n} \sum_{i=1}^{n} x_{i}\) of the
1000 random variates we generated is
0.015.</p>

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
