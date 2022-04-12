---
toc: false
layout: post
description: How to deploy apps on Compute Studio using the new automated deployments feature.
categories: [demo-days, policy-simulation-library, compute-studio]
author: Hank Doupe
title: "Demo Day: Deploying apps on Compute Studio"
---

------

{% include youtube.html content='https://youtu.be/P1mzhZkwRt0' %}

------

Compute Studio (C/S) is a platform for publishing and sharing computational models and data visualizations. In this demo day, I show how to publish your own project on C/S using the new automated deployments feature. You can find an in depth guide to publishing on C/S
in the [developer docs](https://docs.compute.studio/publish/guide.html).

C/S supports two types of projects: models and data visualizations. Models are fed some inputs and return a result. Data visualizations are web servers  backed by popular open-source libraries like Bokeh, Dash, or Streamlit. Models are good for long-running processes and producing archivable results that can be shared and returned to easily. Data visualizations are good for highly interactive and custom user experiences.

Now that you've checked out the [developer docs](https://docs.compute.studio/publish/guide.html) and set up your model or data-viz, you can head over to the C/S publishing page [https://compute.studio/new/](https://compute.studio/new/) to publish your project. Note that this page is still very much under construction and may look different in a few weeks.

![Publish page](../images/cs-auto-deploy/publish_page.png)

Next, you will be sent to the second stage in the publish flow where you will provide more details on how to connect your project on C/S:

![Connect Project page](../images/cs-auto-deploy/connect_project_page.png)

Clicking "Connect App" will take you to the project home page:

![Project home page](../images/cs-auto-deploy/project_home_page.png)

Go to the "Settings" button in the top-right corner and this will take you to the project dashboard where you can modify everything from the social preview of your project to the amount of compute resources it needs:

![Project dashboard](../images/cs-auto-deploy/project_dashboard.png)

The "Builds" link in the sidebar will take you to the builds dashboard where you can create your first build:

![Build history dashboard](../images/cs-auto-deploy/build_history_dashboard.png)

It's time to create the first build. You can do so by clicking "New Build". This will take you to the build status page. While the build is being scheduled, the page will look like this:

![Build scheduled page](../images/cs-auto-deploy/build_scheduled_page.png)

You can click the "Build History" link and it will show that the build has been started:

![Build history dashboard](../images/cs-auto-deploy/build_history_dashboard_progress.png)

The build status page should be updated at this point and will look something like this:

![Build status page](../images/cs-auto-deploy/build_status_page_progress.png)

C/S automated deployments are built on top of [Github Actions](https://github.com/features/actions). Unfortunately, the logs in Github Actions are not available through the Github API until after the workflow is completely finished. The build status dashboard will update as the build progresses and once it's done, you will have full access to the logs from the build. These will contain outputs from installing your project and the outputs from your project's tests.

In this case, the build failed. We can inspect the logs to see that an import error caused the failure:

![Build failed status page](../images/cs-auto-deploy/build_status_failed.png)

![Build failed status page with logs](../images/cs-auto-deploy/build_status_failed_logs.png)

I pushed an update to my fork of Tax-Cruncher on Github and restarted the build by clicking "Failure. Start new Build". The next build succeeded and we can click "Release" to publish the project:

![Build status page success](../images/cs-auto-deploy/build_status_page_success.png)

The builds dashboard now shows the two builds:

![Updated build history page](../images/cs-auto-deploy/updated_build_history_page.png)

Finally, let's go run our new model:

![Run project page](../images/cs-auto-deploy/run_project_page_loading.png)

It may take a few seconds for the page to load. This is because the model code and all of its dependencies are being loaded onto the C/S servers for the first time:

![Run project page with inputs form](../images/cs-auto-deploy/run_project_page_success.png)

The steps for publishing a data visualization are very similar. The main idea is that you tell C/S what Python file your app lives in and C/S will know how to run it given your data visualization technology choice.
