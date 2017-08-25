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

<pre><code>## [1]  0.1470681  0.2522050 -1.0190714  0.2975389 -0.4204491 -0.2769255
</code></pre>

<p><code>knitr</code> offers a lot of control over representing different
types of output. We can also have inline <code>R</code> expressions
computed on the fly.</p>

<p>The mean \(\bar{x} = \frac{1}{n} \sum_{i=1}^{n} x_{i}\) of the
1000 random variates we generated is
-0.041.</p>

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
