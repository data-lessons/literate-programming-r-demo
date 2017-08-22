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

We see elements of an reference entry: `@Article` is the type, `cite:4` is citation-key, and other more elements of a reference. To tell RStudio to use our BibTex file we add `bibliography` key to our document header. 

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

The actually cite one of our bibtex entries we use the `@` symbol in a couple of ways.  To use an in-text citation use the following: 

```
The rest of this paper is organized as follows. We motivate the need for
vacuum tubes. We place our work in context with the related work in this
area @darwin.
```

The rest of this paper is organized as follows. We motivate the need for
vacuum tubes. We place our work in context with the related work in this
area @darwin.


Notice that 
