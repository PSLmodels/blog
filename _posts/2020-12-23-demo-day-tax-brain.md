---
toc: true
layout: post
description: How to use the Tax-Brain web-app
categories: [demo-days, individual-income-tax, tax-brain]
author: Anderson Frailey
title: "Demo Day: Tax-Brain"
---

 {% include youtube.html content='https://youtu.be/Zc_XEErfO5E' %}

 ------

 For this PSL demo-day I showed how to use the [Tax-Brain web-application](https://www.compute.studio/PSLmodels/Tax-Brain/),
 hosted on [Compute Studio](http://compute.studio), to analyze proposed individual income tax policies.
Tax-Brain integrates the [Tax-Calculator](https://pslmodels.github.io/Tax-Calculator/)
and [Behavioral-Responses](https://github.com/PSLmodels/Behavioral-Responses#readme)
models to make running both static and dynamic analyses of the US federal income
and payroll taxes simple. The web interface for the model makes it possible for
anyone to run their own analyses without writing a single line of code.

We started the demo by simply walking through the interface and features of the
web-app before creating our own sample reform to model. This reform, which to
my knowledge does not reflect any proposals currently up for debate, included
changes to the income and payroll tax rates, bringing back personal exemptions,
modifying the standard deduction, and implementing a universal basic income.

While the model ran, I explained how Tax-Brain validated all of the user inputs,
the data behind the model, and how the final tax liability projections are
determined. We concluded by looking through the variety of tables and graphs
Tax-Brain produces and how they can easily be shared with others.

Resources:
* [Simulation from the demonstration](https://compute.studio/PSLmodels/Tax-Brain/48969/)
* [Tax-Brain GitHub repo](https://github.com/PSLmodels/Tax-Brain)
* [Tax-Calculator documentation](https://pslmodels.github.io/Tax-Calculator/#)
* [Behavioral-Responses documentation](https://pslmodels.github.io/Behavioral-Responses/index.html)
