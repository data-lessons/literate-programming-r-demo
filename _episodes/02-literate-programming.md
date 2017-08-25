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

<pre><code>## [1]  0.2541665  0.2746722 -1.5741258  0.4530805  1.0870993 -0.3046895
</code></pre>

<p><code>knitr</code> offers a lot of control over representing different
types of output. We can also have inline <code>R</code> expressions
computed on the fly.</p>

<p>The mean \(\bar{x} = \frac{1}{n} \sum_{i=1}^{n} x_{i}\) of the
1000 random variates we generated is
-0.074.</p>

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
