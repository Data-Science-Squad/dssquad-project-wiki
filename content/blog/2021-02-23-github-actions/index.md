---
title: Automating workflows with GitHub Actions
author: Danny Morris
date: '2021-02-23'
slug: []
categories: []
tags: []
meta_img: images/image.png
description: Description for the page
---

GitHub Actions will make it easy to automate and orchestrate the execution of code to build and deploy our software. For our purposes, we will use GitHub Actions to trigger the execution of production code sequentially across multiple repositories to automate our daily build.

GitHub Actions runs "workflows" in response to one or more "events". Common event types to trigger workflows include:

- `schedule` events, i.e. cron expressions run workflows at specific times
- `push` events, i.e. a commit is pushed to the repo and runs the workflow
- `worflow_dispatch`, e.g. the completion of a workflow in one repository triggers the execution of a workflow in another

### Using GitHub Actions for our project

For our project, we will strive for the following production workflow sequence:

1. The `dssquad-datakit` codebase runs via a `schedule` event at [insert time] each day. 

2. Upon completion, a `worflow_dispatch` event is triggered to run the `dssquad-ml` codebase. 

3. Upon completion, another `worflow_dispatch` event is triggered to run the `dssquad-app` codebase.

