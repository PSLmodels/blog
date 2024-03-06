---
aliases:
- /demo-days/PSL/2021/03/08/demo-day-cs-api-stitch
author: Hank Doupe
categories:
- demo-days
- PSL
date: '2021-03-08'
description: Creating an app with the Compute Studio API.
layout: post
title: 'Demo Day: Stitching together apps on Compute Studio'
toc: true

---

{{< video https://youtu.be/5I59dyB_2ws >}}

---

In Demo Day 8, I talked about connecting multiple apps on [Compute Studio](https://compute.studio) with [PSL Stitch](https://stitch.hankdoupe.com). The source code for PSL stitch can be found in this [repository](https://github.com/hdoupe/psl-stitch).

Stitch is composed of three components:

* A [python package](https://github.com/hdoupe/psl-stitch/tree/main/psl_stitch) that can be run like a normal Python package.
* A [RESTful API](https://github.com/hdoupe/psl-stitch/tree/main/api) built with [FastAPI](https://fastapi.tiangolo.com) that is called remotely to create simulations on Compute Studio.
* A [GUI](https://github.com/hdoupe/psl-stitch/tree/main/psl-stitch-app) built with [ReactJS](https://reactjs.org/) that makes calls to the REST API to create and monitor simulations.

One of the cool things about this app is that it uses [ParamTools](https://paramtools.dev) to read the JSON files under the hood. This means that it can read links to data in other Compute Studio runs, files on GitHub, or just plain JSON. Here are some example parameters:

* policy parameters: `cs://PSLmodels:Tax-Brain@49779/inputs/adjustment/policy`
* tax-cruncher parameters: `{"sage": [{"value": 25}]}`
* business tax parameters: `{"CIT_rate": [{"value": 0.25, "year": 2021}]}`

After clicking run, three simulations will be created on Compute Studio and the app will update as soon as the simulations have finished:

![Getting started](https://user-images.githubusercontent.com/9206065/112211937-ca75db00-8bf2-11eb-856f-41c46e7e8ec5.png)

![CS Simulations](https://user-images.githubusercontent.com/9206065/112211931-c9dd4480-8bf2-11eb-83d8-678fd6d80dd9.png)

Once they are done, the simulations are best viewed and interacted with on Compute Studio, but you can still inspect the JSON response from the Compute Studio API:

![Simulation Complete](https://user-images.githubusercontent.com/9206065/112211930-c944ae00-8bf2-11eb-87dc-949ff3007229.png)

I created this app to show that it's possible to build apps on top of the Compute Studio API. I think PSL Stitch is a neat example of how to do this, but I am even more excited to see what others build next.

Also, this is an open source project and has lots of room for improvement. If you are interested in learning web technologies related to REST APIs and frontend development with JavaScript, then this project could be a good place to start!

Resources:

* [PSL Stitch](https://stitch.hankdoupe.com)
* [Source code](https://github.com/hdoupe/psl-stitch)
* [Compute Studio API Docs](https://docs.compute.studio/api/guide.html)
