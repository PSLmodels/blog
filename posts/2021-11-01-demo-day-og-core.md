---
aliases:
- /demo-days/python/macroeconomics/overlapping-generations/2021/11/01/demo-day-og-core
author: Jason DeBacker
categories:
- demo-days
- python
- macroeconomics
- overlapping-generations
date: '2021-11-01'
description: A Python platform for building country-specific overlapping generations
  general equilibrium models.
layout: post
title: 'Demo Day: The OG-Core platform'
toc: true

---

{{< video https://youtu.be/y1vSgmEtgxs >}}
---

The [OG-Core](https://pslmodels.github.io/OG-Core/) model is a general equilibrium, overlapping generations (OG) model suitable for evaluating fiscal policy.
Since the work of Alan Auerbach and Laurence Kotlikoff in the 1980s, this class of model has become a standard in the macroeconomic analysis of tax and spending policy.
This is for good reason.
OG models are able to capture the impacts of taxes and spending in the short and long run, examine incidence of policy across generations of people (not just short run or steady state analysis of a cross-section of the economy), and capture important economic dynamics (e.g., crowding out effects of deficit-financed policy).

In the PSL Demo Day presentation linked above, I cover the basics of OG-Core: its history, its API, and how country-specific models can use OG-Core as a dependency.
In brief, OG-Core provides a general overlapping generations framework, from which parameters can be calibrated to represent particular economies.
Think of it this way: an economic model is just a set of parameters plus a system of equations.
OG-Core spells out all of the equations to represent an economy with heterogeneous agents, production and government sectors, open economy options, and detailed policy rules.
OG-Core also includes default values for all parameters, along with parameter metadata and parameter validation rules.
A country specific application is then just a particular parameterization of the general OG-Core model.

As an example of a country-specific application, one can look at the [OG-USA model](https://pslmodels.github.io/OG-USA).
This model provides a calibration of OG-Core to the United States.
The source code in that project allows one to go from raw data sources to the estimation and calibration procedures used to determine parameter values representing the United States, to parameter values in formats suitable for use in OG-Core.
Country-specific models like OG-USA include (where available) links to microsimulation models of tax and spending programs to allow detailed microdata of actual and counterfactual policies to inform the net tax-transfer functions used in the OG-Core model.
For those interested in building their own country-specific model, the OG-USA project provides a good example to work from.

We encourage you to take a look at OG-Core and related projects.
New contributions and applications are always welcome.
If you have questions or comments, reach out through the relevant repositories on Github to me, [@jdebacker](https://github.com/jdebacker/), or Rick Evans, [@rickecon](https://github.com/rickecon).

Resources:

* [OG-Core documentation](https://pslmodels.github.io/OG-Core/content/intro/intro.html)
* [OG-USA documentation](https://pslmodels.github.io/OG-USA) package for unit testing in Python
* [Tax-Calculator documentation](http://taxcalc.pslmodels.org)
* [OG-UK repository](https://github.com/PSLmodels/OG-UK)
* [OpenFisca-UK repository](https://github.com/PolicyEngine/openfisca-uk)
* [Slides from the Demo Day presentation](https://docs.google.com/presentation/d/1AT3SYNJ6JieAB1HrPT6HPSBC6-2A1QNtIdBDO-3PSCI/edit?usp=sharing)
