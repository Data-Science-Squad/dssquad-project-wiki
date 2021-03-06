---
title: Automating the build and deploy of production software
author: Danny Morris
date: '2021-03-03'
slug: []
categories: []
tags: []
meta_img: images/image.png
description: Description for the page
---

This document serves as a guide for all team members as we start to build out production assets and the production automation pipeline.

### High-level overview

The following diagram presents a high-level overview of the production automation lifecycle.

![](images/Production-diagram.png)

Each day, the `datakit` codebase will collect new incidents from the source API and update the database with production data assets. Then, the `dssquad-ml` codebase will retrain the model on fresh data and insert forecasts into the database. Finally, the `dssquad-app` codebase will build and deploy a new version of the Streamlit app using all up-to-date production data assets.

All of this will happen via automation.

### Basic production requirements for each team

Data Engineering - [Requirements]({{< ref "/blog/2021-03-05-requirements-to-productionize-the-datakit" >}} "Requirements")

Machine Learning - [Requirements]({{< ref "/blog/2021-02-27-productionalizing-the-ml-model" >}} "Requirements")

Web application - [Requirements]({{< ref "/blog/2021-03-04-productionizing-the-streamlit-app" >}} "Requirements")

### Automating workflows with GitHub Actions

GitHub Actions will make it easy to automate and orchestrate the execution of our code to build and deploy our software. For our purposes, we will use GitHub Actions to trigger the execution of production code across multiple repositories sequentially to automate our daily builds.

GitHub Actions runs **workflows** to execute code. A workflow is user-defined and contained in a `.yaml` configuration file ([example](https://github.com/Data-Science-Squad/dssquad-ml/blob/dm_example_github_actions/.github/workflows/train_and_predict.yml)) in the repository. Workflows contain a series of instructions, such as installing Python and third-party libraries, that enable the execution of code in an isolated virtual environment. 

**Events** are web-based actions that trigger a workflow to run. Common event types include:

- `schedule`, i.e. the workflow on a schedule defined by a cron expression
- `push`, i.e. the workflow is triggered whenever a commit is pushed
- `worflow_dispatch`, e.g. the completion of a workflow in one repository triggers the execution of a workflow in another

##### Using GitHub Actions for our project

For our project, we will use the following workflows and events to automate our daily builds:

1. The `dssquad-datakit` workflow is triggered by a `schedule` event at [insert time] each day. 

2. Upon completion, the `dssquad-datakit` workflow sends a `worflow_dispatch` event to the `dssquad-ml` workflow for execution. 

3. Upon completion, the `dssquad-ml` workflow sends a `worflow_dispatch` event to the `dssquad-app` repository for execution. 

