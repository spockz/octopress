---
layout: post
title: "Combining graphviz (dot) and TikZ with dot2tex"
date: 2013-07-08 23:06
comments: true
categories: Programming
tags:
  - LaTeX
  - TikZ
  - Graphviz
---

* We want good looking documents and figures;
* We want to as much as possibly automatically;
* This is way we use (La)TeX, it creates beautifully typeset
  texts without much effort.
* Similarly, we use graphviz because of the unsurpassed auto-layout and
  we can included generated PDFs manually or use the latex [graphviz package](https://github.com/mprentice/GraphViz-sty).
* One problem however; the results from graphviz just look antiquated. (Although it has the possibility to create unsurpassed nice curvy lines) Furthermore, it is not possible to use (La)TeX inside the graph.

<figure>
	<img src="http://farm8.staticflickr.com/7313/9243796534_60bb926e44_o.png" width="563" height="155" alt="Image with graphviz">
	<figcaption>Foobaar</figcaption>
</figure>

* With TikZ it is possible to create nice looking graphs but you have to do all positioning *manually*!
* Enter [dot2tex](http://www.fauskes.net/code/dot2tex/) it brings all the love of graphviz/dot to
  TikZ.
  * Write your graphs in dot; let dot (or neato or whichever engine you prefer do the layout)
  * run dot2tex transforming the dot into TikZ code.
  * Style your nodes and edges with TikZ styles
  * Optionally fine-tune the graph by adding nice tidbits

<img src="http://farm4.staticflickr.com/3804/9241070475_9d48236aa7_o.png" width="430" height="410" alt="Example of TeX typesetting + TikZ background">

For more TikZ goodness check out the [example site](http://www.texample.net/tikz/examples/).