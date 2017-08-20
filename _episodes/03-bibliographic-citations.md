---
title: "Adding citations to your Rmardown manuscript"
author: "Tim Dennis"
date: "August 20, 2017"
teaching: 45
questions:
- "How do I add citations to my RMarkdown document?"
- "How can I integrate Zotero citations into my RMarkdown document?"
objectives:
- "Define a bibliography in RMarkdown header"
- "Apply citations inline in document text"
- "Use an existing Zotero bibliography in RStudio"
keypoints:
- ""
output: html_document
---




## R Markdown

This is an R Markdown document. Markdown is a simple formatting syntax for authoring HTML, PDF, and MS Word documents. For more details on using R Markdown see <http://rmarkdown.rstudio.com>.

When you click the **Knit** button a document will be generated that includes both content as well as the output of any embedded R code chunks within the document. You can embed an R code chunk like this:


~~~
summary(cars)
~~~
{: .r}



~~~
     speed           dist       
 Min.   : 4.0   Min.   :  2.00  
 1st Qu.:12.0   1st Qu.: 26.00  
 Median :15.0   Median : 36.00  
 Mean   :15.4   Mean   : 42.98  
 3rd Qu.:19.0   3rd Qu.: 56.00  
 Max.   :25.0   Max.   :120.00  
~~~
{: .output}

## Including Plots

You can also embed plots, for example:

<img src="../fig/rmd-03-pressure-1.png" title="plot of chunk pressure" alt="plot of chunk pressure" style="display: block; margin: auto;" />

Note that the `echo = FALSE` parameter was added to the code chunk to prevent printing of the R code that generated the plot.
