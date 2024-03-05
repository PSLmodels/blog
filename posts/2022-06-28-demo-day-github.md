---
aliases:
- /demo-days/github/git/workflow/getting-started/2022/06/28/demo-day-github
author: Jason DeBacker
categories:
- demo-days
- github
- git
- workflow
- getting-started
date: '2022-06-28'
description: The basics of forking and cloning repositories and working on branches.
layout: post
title: 'Demo Day: Getting Started with GitHub'
toc: true

---

{{< video https://youtu.be/ENl3AkZZgRQ >}}

---

Git and GitHub often present themselves as barriers to entry to would-be contributors to PSL projects, even for those who are otherwise experienced with policy modeling.
But these tools are critical to collaboration on open source projects.
In the Demo Day video linked above, I cover some of the basics to get set up and begin contributing to an open source project.

There are four steps I outline:

1. Create a "[fork](https://docs.github.com/en/get-started/quickstart/fork-a-repo)" of the repository you are interested in.
A fork is a copy of the source code that resides on GitHub (i.e., in the cloud).
A fork gives you control over a copy of the source code.  You will be able to merge in changes to the code on this fork, even if you don't have permissions to do so with the original repository.
1. "[Clone](https://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository)" the fork.
Cloning will download a copy of the source code from your fork onto your local machine.
But cloning is more than just downloading the source code.
It will include the version history of the code and automatically create a link between the local files and the remote files on your fork.
1. Configure your local files to talk to both your fork (which has a default name of `origin`) and the original repository you forked from (which typically has the default name of `upstream`).
Do this by using your command prompt or terminal to navigate to the directory you just cloned.
From there, run:
```
git remote add upstream URL_to_original_repo.git
```
And check that this worked by giving the command:
```
git remote -v
```

If things worked, you should see URLs to your fork and the upstream repository with "(fetch)" and "(push)" by them
More info on this is in the [Git docs](https://git-scm.com/book/en/v2/Git-Basics-Working-with-Remotes).

4. Now that you have copies of the source code on your fork and on your local machine, you are ready to begin contributing.
As you make changes to the source code, you'll want to work on [development branches](https://git-scm.com/book/en/v2/Git-Branching-Basic-Branching-and-Merging).
Branches are copies of the code. Ideally, you keep your "main" (or "master") branch clean (i.e., your best version of the code) and develop the code on branches.
When you've completed the development work (e.g., adding a new feature) you will them merge this into the "main" branch.

I hope this helps you get started contributing to open source projects.
Git and GitHub are valuable tools and there is lots more to learn, but these basics will get you going.
For more information, see the links below.
If you want to get started working with a project in the Library, feel free to reach out to me through the relevant repo ([@jdebacker on GitHub](https://github.com/jdebacker/)) or drop into a PSL Community Call (dates on the [PSL Calendar](http://pslmodels.org/events.html)).


Resources:

* [PSL Git Tutorial](https://pslmodels.github.io/Git-Tutorial/content/intro.html)
* [Git Basics](https://git-scm.com/book/en/v2/Git-Basics-Getting-a-Git-Repository)
