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

<pre><code>## [1] -1.4312432  0.1392884 -0.9480041 -0.2149473 -0.1251113 -1.7540842
</code></pre>

<p><code>knitr</code> offers a lot of control over representing different
types of output. We can also have inline <code>R</code> expressions
computed on the fly.</p>

<p>The mean \(\bar{x} = \frac{1}{n} \sum_{i=1}^{n} x_{i}\) of the
1000 random variates we generated is
0.001.</p>

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
