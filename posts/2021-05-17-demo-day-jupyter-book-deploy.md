---
aliases:
- /demo-days/jupyter-book/GH-actions/documentation/2021/05/17/demo-day-jupyter-book-deploy
author: Jason DeBacker
categories:
- demo-days
- jupyter-book
- GH-actions
- documentation
date: '2021-05-17'
description: How to keep interactive programmatic notebook-based documentation up-to-date
  in your pull request workflow.
layout: post
title: 'Demo Day: Updating Jupyter Book documentation with GitHub Actions'
toc: true

---

{{< video https://youtu.be/rEG5vGMkDsg >}}

---

Open source projects must maintain clear and up-to-date documentation in order to attract users and contributors.
Because of this, PSL sets minimum standards for documentation among cataloged projects in its [model criteria](https://pslmodels.org/Catalog/library_criteria.html).
A recent innovation in executable books, [Jupyter Book](https://jupyterbook.org/intro.html), has provided an excellent format for model documentation and has been widely adopted by PSL projects (see for example [OG-USA](https://pslmodels.github.io/OG-USA/content/intro/intro.html), [Tax-Brain](http://taxbrain.pslmodels.org/content/intro.html), [Tax-Calculator](https://taxcalc.pslmodels.org)).

Jupyter Book allows one to write documents with executable code and text together, as in Jupyter notebooks.
But Jupyter Book pushes this further by allowing documents with multiple sections, better integration of TeX for symbols and equations, BibTex style references and citations, links between sections, and [Sphinx](https://www.sphinx-doc.org/en/master/) integration (for auto-built documentation of model APIs from source code).
Importantly for sharing documentation, Jupyter Books can easily be compiled to HTML, PDF, or other formats.
Portions of a Jupyter Book that contain executable code can be downloaded as Jupyter Notebooks or opened in [Google Colab](https://research.google.com/colaboratory/) or [binder](https://mybinder.org)

The [Jupyter Book](https://jupyterbook.org/intro.html) documentation is excellent and will help you get started creating your "book" (tip: pay close attention to formatting details, including proper whitespace).
What I do here is outline how you can easily deploy your documentation to the web and keep it up-to-date with your project.

I start from the assumption that you have the source files to build your Jupyter Book checked into the main branch of your project (these maybe `yml` , `md` , `rst` , `ipynb` or other files).
For version control purposes and to keep your repo trim, you generally don't want to check the built documentation files to this branch (tip: consider adding the folder these files will go to (e.g., `/_build` to your `.gitignore` ).
When these files are in place and you can successfully build your book locally, it's time for the first step.

*Step 1*: Add two GH Actions to your project's workflow:
1.  An action to check that your documentation files build without an error.
I like to run this on each push to a PR.
The action won't hang on warnings, but will fail if your Jupyter Book doesn't build at all.
An example of this action from the OG-USA repo is [here](https://github.com/PSLmodels/OG-USA/blob/master/.github/workflows/docs_check.yml):

```

name: Check that docs build
on: [push, pull_request]

jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout
        uses: actions/checkout@v2 # If you're using actions/checkout@v2 you must set persist-credentials to false in most cases for the deployment to work correctly.
        with:
          persist-credentials: false

      - name: Setup Miniconda
        uses: conda-incubator/setup-miniconda@v2
        with:
          activate-environment: ogusa-dev
          environment-file: environment.yml
          python-version: 3.7
          auto-activate-base: false

      - name: Build # Build Jupyter Book
        shell: bash -l {0}
        run: |
          pip install jupyter-book
          pip install sphinxcontrib-bibtex==1.0.0
          pip install -e .
          cd docs
          jb build ./book
```

To use this in your repo, you'll just need to change a few settings such as the name of the environment and perhaps the Python version and path to the book source files.
Note that in the above `yml` file `sphinxcontrib-bibtex` is pinned.
You maybe able to unpin this, but OG-USA needed this pin for documentation to compile property due to changes in the `jupyter-book` and `sphinxcontrib-bibtex` packages.

2. An action that builds and deploys the Jupyter Book to [GH Pages](https://pages.github.com).
The OG-USA project uses the [deploy action from James Ives](https://github.com/JamesIves/github-pages-deploy-action) in [this action](https://github.com/PSLmodels/OG-USA/blob/master/.github/workflows/deploy_docs.yml).
This is something that you will want to run when PRs are merged into your main branch so that the documentation is kept up-to-date with the project.
To modify this action for your repo, you'll need to change the repo name, the environment name, and potentially the Python version, branch name, and path to the book source files.

*Step 2*: Once the action in (2) above is run, your compiled Jupyter Book docs will be pushed to a `gh-pages` branch in your repository (the action will create this branch for you if it doesn't already exist).
At this point, you should be able to see your docs at the url `https://GH_org_name.github.io/Repo_name` .
But it probably won't look very good until you complete this next step.
To have your Jupyter Book render on the web as you see it on your machine, you will want to push and merge an empty file with the name `.nojekyll` into your repo's `gh-pages` branch.

That's it!
With these actions, you'll be sure that your book continues to compile and a new version will be published to the web with with each merge to your main branch, ensuring that your documentation stays up-to-date.

Some additional tips:

* Use [Sphinx](https://www.sphinx-doc.org/en/master/) to document your projects API.
By doing so you'll automate an important part of your project's documentation -- as long as the docstrings are updated when the source code is, the Jupyter Book you are publishing to the web will be kept in sync with no additional work needed.
* You can have your `gh-pages`-hosted documentation point to a custom URL.
* Project maintainers should ensure that docs are updated with PRs that are relevant (e.g., if the PR changes an the source code affecting a user interface, then documentation showing example usage should be updated) and help contributors make the necessary changes to the documentation source files.
