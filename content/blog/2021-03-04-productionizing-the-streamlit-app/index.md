---
title: Requirements to productionize the Streamlit app
author: Danny Morris
date: '2021-03-04'
slug: []
categories: []
tags: []
meta_img: images/image.png
description: Description for the page
---
 
This document serves as a guide for putting the Streamlit app into production. Note that this process can be started whenever a prototype app is ready, even if you intend to make improvements.

The app will be automatically re-deployed daily whenever there is a push to the `main` branch of the `dssquad-app` repository. The push event will be configured using GitHub Actions (more details to come).

:raising_hands: The three basic steps to productionize the model include:

1. Create a `streamlit_app.py` file containing the app logic.

2. Create a `requirements.txt` file containing the libraries and their versions needed to run the app.

3. Merge these assets (plus any others needed for the app) from the `develop` branch into the `main` branch with a [Pull Request](https://dssquad-wiki.netlify.app/blog/2021-02-20-pull-requests/).

Example production branch: https://github.com/Data-Science-Squad/dssquad-app/tree/dm-test

**Important**: The app should be deployed and tested using the `develop` branch first before merging into the `main` branch. This will allow team members to test the app and give feedback before merging into production.

