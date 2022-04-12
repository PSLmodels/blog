---
title: 'Demo Day: Using synthimpute for data fusion'
author: "Max Ghenis"
description: The synthimpute Python package fuses and synthesizes economic datasets with machine learning.
categories: [demo-days, python, data-fusion, synthimpute]
layout: post
toc: true
---

{% include youtube.html content='https://youtu.be/e_sk-_yWamY' %}
---

Suppose a policy analyst sought to estimate the impact of a policy that changed income tax rates and benefit rules while also adding a progressive wealth tax.
The standard approach is to use a _microsimulation_ model, where the rules are programmed as code, and then to run that program over a representative sample of households.
Unfortunately, no single US government survey captures all the households characteristics needed to analyze this policy; in particular, the reliable tax and benefit information lies in surveys like the Current Population Survey (CPS), while wealth lies in the Survey of Consumer Finances (SCF).

Assuming the analyst wanted to start with the CPS, they have several options to estimate wealth for households to levy the progressive wealth tax.
Two typical approaches include:
1. Linear regression, predicting wealth from other household characteristics common to the CPS and SCF.
2. Matching, in which each CPS household is matched with the most similar household in the SCF.

Neither of these approaches, however, aim to estimate the _distribution_ of wealth conditional on other characteristics.
Linear regression explicitly estimates the mean prediction, but that could miss the tails of wealth from whom most of the wealth tax revenue will be collected.

Instead, the analyst could apply _quantile regression_ to estimate the distribution of wealth conditional on other characteristics, and then measure the effectiveness of the estimation using _quantile loss_.

In this Demo Day, I present the concepts of microsimulation, imputation, and quantile loss to motivate the `synthimpute` Python package I've developed with my PolicyEngine colleague Nikhil Woodruff.
In an experiment predicting wealth on a holdout set from the SCF, my former colleague Deepak Singh and I found that random forests significantly outperform OLS and matching for quantile regression, and this is the approach applied in `synthimpute` for both data fusion and data synthesis.
The `synthimpute` API will be familiar to users of `scikit-learn` and `statsmodels` , with the difference being that `synthimpute` 's `rf_impute` function returns a random value from the predicted distribution; it can also skew the predictions to meet a target total.

We've used `synthimpute` to fuse data for research reports at the [UBI Center](https://ubicenter.org) and to enhance the [PolicyEngine](https://policyengine.org) web app for UK tax and benefit simulation, and we welcome new users and contributors.
Feel free to explore the repository or contact me with questions at [max@policyengine.org](mailto:max@policyengine.org).

Resources:
* [`synthimpute` package on GitHub](https://github.com/PolicyEngine/synthimpute)
* [Presentation slides](https://docs.google.com/presentation/d/1Hw0zIkbnXZluW8ntjbw_NXryRvjVcg6DDp-btkXXV_o)
* [UBI Center report on land value taxation in the UK](https://www.ubicenter.org/uk-lvt), using `synthimpute` to impute land value from the UK Wealth and Assets Survey to the Family Resources Survey
* [PolicyEngine UK carbon tax example](http://policyengine.org/uk/population-impact?carbon_tax=100), using `synthimpute` to impute carbon emissions from the Living Costs and Food Survey to the Family Resources Survey
* [Notebook comparing random forests to matching and other techniques](https://colab.research.google.com/drive/1E8F7S1Uvfw_3PmpS226Sl1LWV5NBi0CE) using a holdout set from the US Survey of Consumer Finances
* [My blog post on quantile regression for Towards Data Science](https://towardsdatascience.com/quantile-regression-from-linear-models-to-trees-to-deep-learning-af3738b527c3), which laid the groundwork for `synthimpute`
