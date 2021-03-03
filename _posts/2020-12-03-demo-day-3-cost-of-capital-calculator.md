---
 toc: true
 layout: post
 description: Computing the impact of taxes on business investment incentives under alternative policy scenarios.
 categories: [demo-days, cost-of-capital-calculator, business-taxation, corporate-income-tax]
 author: Jason DeBacker
 title: "Demo Day: Cost-of-Capital-Calculator Web Application"
---

 {% include youtube.html content='https://youtu.be/KLIuFbYPpNA' %}

 ------

In the PSL Demo Day video linked above, I demonstrate how to use the Cost-of-Capital-Calculator (CCC) web application on [Compute-Studio](https://compute.studio).
CCC computes various measures of the impact of the tax system on business investment.
These include the [Hall-Jorgenson cost of capital](http://piketty.pse.ens.fr/files/HallJorgenson67.pdf), [marginal effective tax rates](http://webarchive.urban.org/UploadedPDF/1000538.pdf), and effective average tax rates (following the methodology of [Devereux and Griffith (1999)](https://www.ifs.org.uk/wps/wp9816.pdf)).

I begin by illustrating the various parameters available for the user to manipulate.
These include parameters of the business and individual income tax systems, as well as parameters representing economic assumptions (e.g., inflation rates and nominal interest rates) and parameters dictating financial and accounting policy (e.g., the fraction of financing using debt).
Note that all default values for tax policy parameters represent the "baseline policy", which is defined as the current law policy in the year being analyzed (which itself is a parameter the user can change).
Other parameters are estimated using historical data following the methodology of [CBO (2014)](https://www.cbo.gov/sites/default/files/113th-congress-2013-2014/reports/49817-taxingcapitalincome0.pdf).

Next, I change a few parameters and run the model.
In this example, I move the corporate income tax rate up to 28% and lower bonus depreciation for assets with depreciable lives of 20 years or less to 50%.

Finally, I discuss how to interpret output.
The web app returns a table and three figures summarizing marginal effective total tax rates on new investments.
This selection of output helps give one a sense of the the overall changes, as well as effects across asset types, industries, and type of financing.
For the full model output, one can click on "Download Results".
Doing so will download four CSV files contain several measures of the impact of the tax system on investment for very fine asset and industry categories.
Users can take these files and create tables and visualizations relevant to their own use case.

Please take the model for a spin and simulate your own reform.
If you have questions, comments, or suggestions, please let me know on the [PSL Discourse](http://discourse.pslmodels.org) (non-technical questions) or by opening an issue in the [CCC GitHub repository](https://github.com/PSLmodels/Cost-of-Capital-Calculator/issues) (technical questions).

Resources:
* [Compute Studio simulation used in the demonstration](https://compute.studio/PSLmodels/Cost-of-Capital-Calculator/104/)
* [Cost-of-Capital-Calculator web app](https://compute.studio/PSLmodels/Cost-of-Capital-Calculator/)
* [Cost-of-Capital-Calculator documentation](https://pslmodels.github.io/Cost-of-Capital-Calculator/content/intro.html)
* [Cost-of-Capital-Calculator GitHub repository](https://github.com/PSLmodels/Cost-of-Capital-Calculator/)
