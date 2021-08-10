---
title: 'Demo Day: Unit Testing for Open Source Projects'
author: "Jason DeBacker"
description: Unit Testing for Open Source Projects
categories:
- demo-days
- R
- Python
- unit-testing
layout: post
toc: true
---

{% include youtube.html content='https://youtu.be/gnYKHtdSqbY' %}
---

Unit testing is the testing of individual units or functions of a software application.
This differs from regression testing that focuses on the verification of final outputs.
Instead, unit testing tests each smallest testable component of your code.
This helps to more easily identify and trace errors in the code.

Writing unit tests is good practice, though not a practice that's always followed.
The biggest barrier to writing unit tests is that doing so takes time.
You might wonder "why am I testing code that runs?"
But there are a number benefits to writing unit tests:
* It ensures that the code does what you expect it to do
* You'll better understand what your code is doing
* You will reduce time tracking down bugs in your code
Often, writing unit tests will save you time in the longer run because it reduces debugging time and because it forces you to think more about what your code does, which often leads to the development of more efficient code.
And for open source projects, or projects with many contributors, writing unit tests is important in reducing the likelihood that errors are introduced into your code.
This is why the [PSL catalog criteria](https://pslmodels.org/Catalog/library_criteria.html) requires projects to provide at least some level of unit testing.

In the PSL Demo Day video linked above, I illustrate how to implement unit tests in R using the [`testthat`](https://testthat.r-lib.org) package.  There are essentially three steps to this process:
1. Create a directory to put your testing script in, e.g., a folder called `tests`
2. Create one or more scripts that define your tests.
   * Each test is represented as a call of the `test_that` function and contain an statement that will evaluate as true or false (e.g., you may use the `expect_equal` function to verify that a function returns expected values given certain inputs).
   * You will want to use `test` in the name of these tests scripts as well as something descriptive of what is tested.
3. Create a script that will run your tests.
   * Here you'll need to import the `testthat` package and you'll need to call the script(s) you are testing to load their functions.
   * Then you'll use the `test_dir` function to pass the directory in which the script(s) you created in Step 2 reside.
Check out the video to see examples of how each of these steps is executed.
I've also found [this blog post](https://towardsdatascience.com/unit-testing-in-r-68ab9cc8d211) on unit tests with `testthat` to be helpful.

Unit testing in Python seems to be more developed and straightforward with the excellent [`pytest`](https://docs.pytest.org/en/6.2.x/) package.
While `pytest` offers many options for parameterizing tests, running tests in parallel, and more, the basic steps remain the same as those outlined above:
1. Create a directory for your test modules (call this folder `tests` as `pytest will look for that name).
2. Create test modules that define each test
   * Tests are defined much like any other function in Python, the but will involve some assertion statement is triggered upon test failure.
   * You will want to use `test` in the name of these tests modules as well as something descriptive of what is tested.
3. You won't need to create a script to run your tests as with `testthat`, but you may create a [`pytest.ini`](https://docs.pytest.org/en/6.2.x/customize.html) file to customize your tests options.

That's about it to get started writing unit tests for your code.  PSL cataloged projects provide many excellent examples of a variety of unit tests, so search them for examples to build from.
In a future Demo Day and blog post, we'll talk about continuous integration testing to help get even more out of you unit tests.


Resources:
* [`testthat`](https://testthat.r-lib.org) package for unit testing in R
* [`pytest`](https://docs.pytest.org/en/6.2.x/) package for unit testing in Python
* [PSL catalog criteria](https://pslmodels.org/Catalog/library_criteria.html)
