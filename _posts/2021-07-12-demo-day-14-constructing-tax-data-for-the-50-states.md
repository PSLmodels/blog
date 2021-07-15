---
title: 'Demo Day: Constructing Tax Data for the 50 States'
author: "Don Boyd"
description: Constructing Tax Data for the 50 States
categories:
- demo-days
- individual-income-tax
- policy-simulation-library
- PSL
layout: post
toc: true
---

{% include youtube.html content='https://youtu.be/gnYKHtdSqbY' %}
---

Federal income tax reform impacts can vary dramatically across states. 

The cap on state and local tax deductions (SALT) is a well-known example, but other policies also have differential effects because important tax-relevant features vary across states such as the income distribution, relative importance of wage, business, and retirement income, and family size and structure.

Analyzing how policy impacts vary across states requires data that faithfully represent the characteristics of the 50 states.



This Demo Day described a method and software for constructing state weights for microdata files that (1) come as close as possible to targets for individual states, while (2) ensuring that the state weights for each tax record sum to its national weight.

The latter objective ensures that the sum of state impacts for a tax reform equals the national impact. 



This project developed state weights for a data file with more than 200,000 microdata records.

The weighted data file comes within 0.01% of desired values for more than 95% of approximately 10,000 targets.



The goal of the [slides](https://github.com/donboyd5/slides/blob/master/2021-07-12_Boyd_PSL_Demo_Constructing_State_Tax_Weights_For_PUF.pdf) and [video](https://youtu.be/gnYKHtdSqbY) was to enable a motivated python-skilled user of the PSL [TaxData](https://github.com/PSLmodels/taxdata) and [Tax-Calculator](https://taxcalc.pslmodels.org) projects to reproduce project results: 50-state weights for TaxData's primary output, the puf.csv microdata file (based primarily on an IRS Public Use File), using early-stage open-source software developed in the project.

Thus, the demo is technical and focused on nuts and bolts.



The methods and software can also be used to:



* Create geographic-area weights for other microdata files
* Apportion state weights to Congressional Districts or counties, if suitable targets can be developed
* Create state-specific microdata files suitable for modeling state income taxes



The main topics covered in the slides and video are:

* Creating national and state targets from IRS summary data
* Preparing a national microdata file for state weighting
* Approaches to constructing geographic weights
* Running software that implements the Poisson-modeling approach used in the project
* Measures of quality of the results
