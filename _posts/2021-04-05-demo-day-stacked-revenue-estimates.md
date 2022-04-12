---
toc: true
layout: post
description: How to evaluate the cumulative effects of a multi-part tax reform.
categories: [demo-days, individual-income-tax, tax-brain, tax-calculator]
author: Jason DeBacker
title: "Demo Day: Producing stacked revenue estimates with the Tax-Calculator Python API"
---

{% include youtube.html content='https://youtu.be/O79H2Z8CeGc' %}

---

It's often useful to be able to identify the effects of specific provisions individually and not just the overall impact of a proposal with many provisions.
Indeed, when revenue estimates of tax law changes are reported (such as [this JCT analysis](https://www.jct.gov/publications/2021/jcx-14-21/) of the American Rescue Plan Act of 2021), they are typically reported on a provision-by-provision basis.
Finding the provision-by-provision revenue estimates is cumbersome with the [Tax-Brain web application](https://compute.studio/PSLmodels/Tax-Brain/) both because it's hard to iterate over many provisions and because the order matters when stacking estimates, so that one needs to keep this order in mind as parameter values are updated for each additional provision in a full proposal.

In the PSL Demo Day on April 5, 2021, I show how to use the Python API of Tax-Calculator to efficiently produce stacked revenue estimates.
In fact, after some initial setup, this can be done with just 12 lines of code (plus a few more to make the output look nice).
The Google Colab notebook that illustrates this approach can be found [at this link](https://colab.research.google.com/drive/1P-m61lWbPpb_ih42vQKrD2zi9Bpe16BM?usp=sharing), but here I'll walk through the four steps that are involved:

1. *Divide up the full proposal into strings of JSON text that contain each provision you want to analyze*.
My example breaks up the [Biden 2020 campaign proposal](https://github.com/PSLmodels/examples/blob/main/psl_examples/taxcalc/Biden2020.json) into seven provisions, but this is illustrative and you can make more or less provisions depending on the detail you would like to see.
2. *Create a dictionary that contains, as its values, the JSON strings*.
A couple notes on this.
First, the dictionary keys should be descriptive of the provisions as they will become the labels for each provision in the final table of revenue estimates we produce.
Second, order matters here.
You'll want to be sure the current law baseline is first (the value for this will be an empty dictionary).
Then you specify the provisions.
The order you specify will likely affect your revenue estimates from a given provision (for instance, expanding/restricting a deduction has a larger revenue effect when rates are higher), but there are not hard and fast rules on the "right" order.
Traditionally, rate changes are stacked first and tax expenditures later in the order.
3. *Iterate over this dictionary*.
With a dictionary of provisions in hand, we can write a "for loop" to iterate over the provision, simulating the Tax-Calculator model at each step.
Note that when the `Policy` class object in Tax-Calculator is modified, it only needs to be told the changes in tax law parameters relative to its current state.
In other words, when we are stacking provisions, estimating the incremental effect of each, you can think of the `Policy` object having a baseline policy that is represented by the current law baseline plus all provisions that have been analyzed before the provision at the current iteration.
The `Policy` class was created in this way so that one can easily represent policy changes, requiring the user to only input the set of parameters that are modified, not every single parameter's value under the hypothetical policy.
But this also makes it parsimonious to stack provisions as we are doing here.
Notice that the JSON strings for each provision (created in Step 1) can be specified independent of the stacking order.
We only needed to slice the full set of proposals into discrete chunks, we didn't need to worry about creating specifications of cumulative policy changes.
4. *Format output for presentation*.
After we've run a Tax-Calculator simulation for the current law baseline plus each provision (and each year in the budget window), we've got all the output we need.
With this output, we can quickly create a table that will nicely present our stacked revenue estimate.
One good check to do here is to create totals across all provisions and compare this to the simulated revenue effects of running the full set of proposals in one go.
This check helps to ensure that you didn't make an error in specifying your JSON strings.
For example, it's easy to leave out one or more provisions, especially if there are many.

I hope this provides a helpful template for your own analysis.
Note that one can modify this code in several useful ways.
For example, within the for-loops, the [Behavioral-Responses](https://github.com/PSLmodels/Behavioral-Responses) can be called to produce revenue estimates that take into account behavioral feedback.
Or one could store the individual income tax and payroll tax revenue impacts separately (rather than return the combined values as in the example notebook).
Additional outputs (even the full set of microdata after each provision is applied) can be stored for even more analysis.

In the future, look for [Tax-Brain](https://github.com/PSLmodels/Tax-Brain) to add stacked revenue estimates to its capabilities.
It'll still be important for users to carve up their full list of policy changes into sets of provisions as we did in Steps 1 and 2 above, but Tax-Brain will then take care of the rest behind the scenes.

Resources:

* [Colab Notebook with example](https://colab.research.google.com/drive/1P-m61lWbPpb_ih42vQKrD2zi9Bpe16BM?usp=sharing)
* [Biden campaign reform file in PSL Examples](https://github.com/PSLmodels/examples/blob/main/psl_examples/taxcalc/Biden2020.json)
