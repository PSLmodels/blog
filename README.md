[//]: # (This template replaces README.md when someone creates a new repo with the fastpages template.)

![](https://github.com/PSLmodels/blog/workflows/CI/badge.svg)
![](https://github.com/PSLmodels/blog/workflows/GH-Pages%20Status/badge.svg)


# [PSL blog](https://blog.pslmodels.org)


_powered by [Quarto](https://quarto.org)_


## How to contribute

The `PSL blog` accepts posts as Jupyter notebooks or Markdown documents:

* To submit a Jupyter post, create a PR with your `YYYY-MM-DD-post-title.ipynb` file in the `_notebooks` folder.
* To submit a Markdown post, create a PR with your `YYYY-MM-DD-post-title.md` file in the `_posts` folder.

In both cases, please take the following steps:
1. Follow the nbdev guides on writing blogs with R Mardown (`*.qmd`), Jupyter (`*.ipynb`), and Markdown (`*.md`), and include the required "front matter" with metadata (you can the template from past posts).
2. [Preview the blog locally](_fastpages_docs/DEVELOPMENT.md) using the `quarto preview` command from the root directory after drafting your post.
You'll need [Quarto](https://quarto.org/docs/get-started/) installed on your machine to run the command.
1. Include a screenshot of the blog post in your PR.

Please use the [Quarto discussions](https://github.com/quarto-dev/quarto-cli/discussions) on Github for questions about using Quarto.

## Technical guide

* Make URLs concise but descriptive of the post.
* Use lowercase and dashes for all tags.
* Make each new sentence its own line (for easier code review).

## Post formats

Please follow the below guidance for each post type.

### Demo Days recaps

* Tag the post as `demo-days`.
* Title the post `Demo Day: {title}`.
* Show the video at the top of the post.
* Describe the motivation for the demo and what you demonstrated.
* Link materials shown in the demo, including code and/or Compute Studio simulations.

See [PR #10](https://github.com/PSLmodels/blog/pull/10) as an example.

## Style guide

* Focus on PSL software and models; reserve policy analysis for think tank and op-ed reports.
* Write with a neutral tone.
* Favor active over passive voice.
* Capitalize post titles.
* Favor `Mmm DD`, `Mmm DD, YYYY`, or `YYYY-MM-DD` date formats over `MM/DD` and `MM/DD/YYYY`, which can be misinterpreted outside the US.
* Avoid "click here" links; for better [accessibility](https://webaccess.berkeley.edu/resources/tips/web-accessibility#accessible-links) and [SEO](https://www.lamar.edu/web-communication/resources/avoid-using-click-here.html), provide descriptive links.

*Questions? Contact Max Ghenis (mghenis@gmail.com).*
