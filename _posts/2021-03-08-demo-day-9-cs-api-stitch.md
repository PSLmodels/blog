---
toc: true
layout: post
description: Creating an app with the Compute Studio API
categories: [demo-days, PSL]
author: Hank Doupe
title: "Demo Day: Stitching together Apps on Compute Studio"
---

{% include youtube.html content='https://youtu.be/5I59dyB_2ws' %}

---

In Demo Day 8, I talked about connecting multiple apps on [Compute Studio](https://compute.studio) with [PSL Stitch](https://stitch.hankdoupe.com). The source code for PSL stitch can be found in this [repository](https://github.com/hdoupe/psl-stitch).

Stitch is composed of three components:

- A [python package](https://github.com/hdoupe/psl-stitch/tree/main/psl_stitch) that can be run like a normal Python package.
- A [RESTful API](https://github.com/hdoupe/psl-stitch/tree/main/api) built with [FastAPI](https://fastapi.tiangolo.com) that is called remotely to create simulations on Compute Studio.
- A [GUI](https://github.com/hdoupe/psl-stitch/tree/main/psl-stitch-app) built with [ReactJS](https://reactjs.org/) that makes calls to the REST API to create and monitor simulations.

One of the cool things about this app is that it uses [ParamTools](https://paramtools.dev) to read the JSON files under the hood. This means that it can read links to data in other Compute Studio runs, files on GitHub, or just plain JSON. Here are some example parameters:

- policy parameters: `cs://PSLmodels:Tax-Brain@49779/inputs/adjustment/policy`
- tax-cruncher parameters: `{"sage": [{"value": 25}]}`
- business tax parameters: `{"CIT_rate": [{"value": 0.25, "year": 2021}]}`

After clicking run, three simulations will be created on Compute Studio and the app will update as soon as the simulations have finished:

TODO: add image

Once they are done, the simulations are best viewed and interacted with on Compute Studio, but you can still inspect the JSON response from the Compute Studio API:

TODO: add image

I created this app to show that it's possible to build apps on top of the Compute Studio API. I think PSL Stitch is a neat example of how to do this, but I am even more excited to see what others build next.

Also, this is an open source project and has lots of room for improvement. If you are interested in learning web technologies related to REST APIs and frontend development with JavaScript, then this project could be a good place to start!

Resources:

- [PSL Stitch](https://stitch.hankdoupe.com)
- [Source code](https://pslmodels.org/events.html)
- [Compute Studio API Docs](https://docs.compute.studio/api/guide.html)
