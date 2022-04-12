---
toc: true
layout: post
description: Analyzing US wealth data in a web-based Python notebook.
categories: [demo-days, microdf, scf]
author: Max Ghenis
title: "Demo Day: Running the scf and microdf Python packages in Google Colab"
---

 {% include youtube.html content='https://youtu.be/Zlws_gC9HeY' %}

 ------

 For Monday's PSL Demo Day, I showed how to use the `scf` and `microdf` PSL Python packages from the [Google Colab](http://colab.research.google.com) web-based Jupyter notebook interface.

 The `scf` package extracts data from the Federal Reserve's Survey of Consumer Finances, the canonical source of US wealth microdata.
`scf` has a single function: `load(years, columns)` , which then returns a `pandas`  `DataFrame` with the specified column(s), each record's survey weight, and the year (when multiple years are requested).

 The `microdf` package analyzes survey microdata, such as that returned by the `scf.load` function.
 It offers a consistent paradigm for calculating statistics like means, medians, sums, and inequality statistics like the Gini index.
 Most functions are structured as follows: `f(df, col, w, groupby)` where `df` is a `pandas`  `DataFrame` of survey microdata, `col` is a column(s) name to be summarized, `w` is the weight column, and `groupby` is the column(s) to group records in before summarizing.

 Using Google Colab, I showed how to use these packages to quickly calculate mean, median, and total wealth from the SCF data, without having to install any software or leave the browser.
 I also demonstrated how to use the `groupby` argument of `microdf` functions to show how different measures of wealth inequality have changed over time.
 Finally, I previewed some of what's to come with `scf` and `microdf` : imputations, extrapolations, inflation, visualization, and documentation, to name a few priorities.

Resources:
* [Slides](https://docs.google.com/presentation/d/1bXWD_8wjbvG4J-Tq8PvlP7xK7Kz2X0oVpsOnjFZ_6zY)
* [Demo notebook in Google Colab](https://colab.research.google.com/drive/1WLOYxAtC347g2tIyO_iJJQUAZmwL4raB?usp=sharing)
* [Simulation from the demonstration](https://compute.studio/PSLmodels/Tax-Brain/48969/)
* [`scf` GitHub repo](https://github.com/PSLmodels/scf)
* [`microdf` GitHub repo](https://github.com/PSLmodels/microdf)
* [`microdf` documentation](https://pslmodels.github.io/microdf)
