---
title: 'Demo Day: Analyzing tax competitiveness with Cost-of-Capital-Calculator'
author: "Jason DeBacker"
description: Using Cost-of-Capital-Calculator with data on international business tax policies.
categories: [demo-days, cost-of-capital-calculator,   business-taxation.   corporate-income-tax, taxes]
layout: post
toc: true
---

{% include youtube.html content='https://youtu.be/JbVXRSbb2Dk' %}
---

In the Demo Day video shared here, I show how to use open source tools to analyze international corporate tax competitiveness.
The two main tools illustrated are the [Cost-of-Capital-Calculator](https://ccc.pslmodels.org/content/intro.html) (CCC), a model to compute measures of the tax burden on new investments, and [Tax Foundation's International Tax Competitiveness Index](https://taxfoundation.org/publications/international-tax-competitiveness-index/) (ITCI).

Tax Foundation has made many helpful resources available online.
Their measures of international business tax policy are a great example of this.
The ICTI outputs and inputs are all well documented, with source code to reproduce results [available on GitHub](https://github.com/TaxFoundation/international-tax-competitiveness-index/).

I plug Tax Foundation's country-by-country data into CCC functions using it's Python API.
Because CCC is designed to flexibly take array or scalar data, operating on rows of tabular data, such as that in the ITCI, is relatively straight-forward.
The Google [Colab notebook](https://colab.research.google.com/drive/1t_NDNqP5-Aq_vsOkGO9SE1Qj4oEVCqCN?usp=sharing) I walk through in this Demo Day, can be a helpful example to follow if you'd like to do something similar to this with the Tax Foundation data - or your own data source.
From the basic building blocks there (reading in data, calling CCC functions), you can extend the analysis in a number of ways.
For example adding additional years of data (Tax Foundation posts their data back to 2014), modifying economic assumptions, or creating counter-factual policy experiments across sets of countries.

If you find this example useful, or have questions or suggestions about this type of analysis, please feel free to [reach out to me](mailto:jason.debacker@gmail.com).

Resources:
* [Colab Notebook](https://colab.research.google.com/drive/1t_NDNqP5-Aq_vsOkGO9SE1Qj4oEVCqCN?usp=sharing)
* [Tax Foundation International Tax Competitiveness Index 2021](https://taxfoundation.org/publications/international-tax-competitiveness-index/)
* [GitHub repo for Tax Foundation ITCI data](https://github.com/TaxFoundation/international-tax-competitiveness-index/tree/master/final_data)
* [Cost-of-Capital-Calculator documentation](https://ccc.pslmodels.org/content/intro.html)
