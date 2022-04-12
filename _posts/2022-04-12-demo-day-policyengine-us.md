---
title: 'Demo Day: Modeling taxes and benefits with the PolicyEngine US web app'
author: "Max Ghenis"
description: PolicyEngine US is a web app for computing the impact of US tax and benefit policy.
categories:
- demo-days
- apps
- taxes
- benefits
- us
layout: post
toc: true
---

{% include youtube.html content='https://youtu.be/Rgrb-52wS8I' %}
---

[PolicyEngine](https://policyengine.org) is a nonprofit that builds free, open-source software to compute the impact of public policy.
After launching our [UK app](https://policyengine.org/uk) in October 2021, we've just launched our [US app](https://policyengine.org/us), which calculates households' federal taxes and several benefit programs, both under current law and under customizable policy reforms.

In this Demo Day, I provide background on PolicyEngine and demonstrate how to use PolicyEngine US (a Policy Simulation Library cataloged model) to answer a novel policy question:

> How would doubling both (a) the Child Tax Credit and (b) the Supplemental Nutrition Assistance Program (SNAP) net income limit affect a single parent in California with $1,000 monthly rent and $50 monthly broadband costs?

By bringing together tax and benefit models into a web interface, we can answer this question quickly without programming experience, as well as an unlimited array of questions like it.
The result is a table breaking down the household's net income by program, as well as graphs of net income and marginal tax rates as the household's earnings vary.

I close with a quick demo of [PolicyEngine UK](https://policyengine.org/uk), which adds society-wide results like the impact of reforms on the budget, poverty, and inequality, as well as contributed policy parameters.
We're planning to bring those features to PolicyEngine US, along with state tax and benefit programs in all 50 states, over the next two years (if not sooner).

Feel free to explore the app and reach out with any questions at [max@policyengine.org](mailto:max@policyengine.org).

Resources:
* [PolicyEngine US](https://policyengine.org/us)
* [Presentation slides](https://docs.google.com/presentation/d/1ckaxNiPrUZeD1IGhqeqAjLPjjCx1zswhZiIqO0ps72w)
* [PolicyEngine blog post on launching PolicyEngine US](https://blog.policyengine.org/policyengine-comes-stateside-cef88b122e48)
