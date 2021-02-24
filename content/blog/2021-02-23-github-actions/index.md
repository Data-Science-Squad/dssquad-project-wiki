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

GitHub Actions will make it easy to automate and orchestrate various workflows that drive our software. For our purposes, we will use GitHub Actions to automatically deploy and run our production code in GitHub whenever certain actions are performed on a repository.

Examples:

- Every hour, a GitHub Actions workflow will automatically run the production Python script to retrieve new crime incidents from the source API and insert the new records into the production database.

- After new records have been retrieved, an empty commit is pushed to the `dssquad-ml` repository via automation. This will trigger a GitHub Actions workflow to run the production Python script that retrains the model, inserts new forecasts into the database, and logs accuracy metrics.

- After the data and forecasts have been refreshed, an empty commit is pushed to the `dssquad-app` repository. Streamlit Sharing will automatically detect this event and redeploy the web application, resulting in fresh data and forecasts available to app users in the browser.