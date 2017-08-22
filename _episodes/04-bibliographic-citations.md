---
title: "Adding citations to your R Markdown manuscript"
author: "Tim Dennis"
date: "August 20, 2017"
bibliography: decoupling-dns.bib
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




## Defining your bibliography

Out of the box, RStudio and Knitr use the built-in citation rendering that pandoc provides. We set this in the `YAML` header information at the top of our R Markdown document. Pandoc can read a bibliographic file in various formats, including: MODS, BibLaTex, BibTex, RIS, EndNote, MEDLINE, etc. These are formats that provide a structured way to store a list of references. Let's take a look at the BibTex file we provided for this workshop:


~~~
head -n 10 decoupling-dns.bib
~~~
{: .r}

We see elements of an reference entry: `@Article` is the type, `darwin` is citation-key, and other more elements of a reference. To tell RStudio to use our BibTex file we add `bibliography` key to our document header. 

```
---
title: "Adding citations to your R Markdown manuscript"
author: "Tim Dennis"
date: "August 20, 2017"
bibliography: decoupling-dns.bib
output: html_document
---
```

This will read `decoupling-dns.bib` file and use to create citations and a bibliography for our file when we render it using our `Knit` button. Let's walk through what that looks like. 

## Creating a Citation

The actually cite one of our bibtex entries we use the `@` symbol in a couple of ways.  To maek a citation use the following: 

```
The rest of this paper is organized as follows. We motivate the need for
vacuum tubes. We place our work in context with the related work in this
area [@darwin].
```

>The rest of this paper is organized as follows. We motivate the need for
vacuum tubes. We place our work in context with the related work in this
area [@darwin].

## Placement of the Bibliography

Notice that when we knitted the document, a bibliography was added to the end of the document at the end. We should probably add an appropriate header to the end of the document.

```
## References
```
Now when we knit again our bibliography will be added below the Reference header. 

## Multi-author citations

Ok let's add a multi-author citation to the mix. We'll pull another quote from our dummy paper and add three citation-keys from our bibliography file separated by a semi-colon inside brackets. We can Knit again. 

```
Another compelling aim in this area is the visualization of evolutionary
programming. Unfortunately, trainable epistemologies might not be the
panacea that end-users expected. Next, it should be noted that Nag
studies reliable archetypes [@nehru; @dennis05; @chomsky].
```

>Another compelling aim in this area is the visualization of evolutionary
programming. Unfortunately, trainable epistemologies might not be the
panacea that end-users expected. Next, it should be noted that Nag
studies reliable archetypes [@nehru; @dennis05; @chomsky].

Notice that more references were added to our bibliography and sorted by alpha. 

## What about page numbers? 

We need to add page numbers and chapters with a comma following our citation-keys like so: 

```
The rest of this paper is organized as follows. We motivate the need for
vacuum tubes. We place our work in context with the related work in this
area [@darwin, pp. 3-5].
```

>The rest of this paper is organized as follows. We motivate the need for
vacuum tubes. We place our work in context with the related work in this
area [@darwin, pp. 3-5].

We can do this in a multi-author context as well: 

```
Another compelling aim in this area is the visualization of evolutionary
programming. Unfortunately, trainable epistemologies might not be the
panacea that end-users expected. Next, it should be noted that Nag
studies reliable archetypes [@nehru, pp. 4-6; @dennis05; @chomsky, ch. 1].
```

>Another compelling aim in this area is the visualization of evolutionary
programming. Unfortunately, trainable epistemologies might not be the
panacea that end-users expected. Next, it should be noted that Nag
studies reliable archetypes [@nehru, pp. 4-6; @dennis05; @chomsky, ch. 1].

## Omitting the author's name

We can also omit the author's name in the citation by using the minus sign `-`. 

```
Dennis proposed a “smart” tool for synthesizing 802.11b, which he call Nag [-@dennis05].
```

Dennis proposed a “smart” tool for synthesizing 802.11b, which he call Nag [-@dennis05].

## In-text citation style 

We also can use in-text style citations: 

```
@dekker03 [p. 33] suggested a scheme for enabling “smart” configurations, but
did not fully realize the implications of forward-error correction at
the time.
```
@dekker03 [p. 33] suggested a scheme for enabling “smart” configurations, but
did not fully realize the implications of forward-error correction at
the time.

## Adding uncited items

Adding references to your bibliography you don't site. We can use some special syntax to add items to our references that we aren't going to cite in the paper: 

```
---
nocite: | 
  @qian, @minsky
...
```
---
nocite: | 
  @qian, @minsky
...

## Zotero integration 

Now we have the basics down, let's think about our bibliography file again. Bibtex is nice and provides structure so a machine can read it, but we don't really want to write it ourself. We can let Zotero do that for us and keep an up-to-date synched Bibtex file in our project folder. That way we can use the more user friendly tool to create and mantain references and always have the latest copy in our project so R can read. 

What do we need? 

1. Zotero with the BetterBibTex plugin installed
2. A bibliography 



## References
