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

GitHub Actions will make it easy to automate and orchestrate various workflows that drive our software. For our purposes, we will use GitHub Actions to trigger our production code to run in response to some automated event.

Examples:

- Every day, new crime incidents from the source API will be gathered and inserted into the database. This will trigger a "git push" event to the `dssquad-ml` repository.

- When the `dssquad-ml` repo receives the push event, GitHub Actions will automatically run a workflow to retrain the model, inserts new forecasts into the database, and logs accuracy metrics. 

- Once the `dssquad-ml` workflow is complete, this will trigger a "git push" event to the `dssquad-app` repository. Streamlit Sharing will automatically detect this event and redeploy the web application, resulting in fresh data and forecasts available to app users in the browser.