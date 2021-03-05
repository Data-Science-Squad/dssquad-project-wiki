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
 
This document defines the basic requirements for putting the Streamlit app into production. Note that this process can be started whenever a prototype app is ready, even if you intend to make improvements.

### Minimum assets needed for production

1. `streamlit_app.py` file containing the app logic.

2. `requirements.txt` file containing the libraries and their versions needed to run the app.

### Merging assets into production

All assets required to run the app must be merged from the `develop` branch into the `main` branch with a [Pull Request](https://dssquad-wiki.netlify.app/blog/2021-02-20-pull-requests/).

This means the app must be deployed, tested, and reviewed in the `develop` branch first before merging into the `main` branch. This will allow team members to test the app and give feedback before the final merge into production.

### Automating the build and deployment

Streamlit Sharing will deploy apps directly from both the `develop` branch (for testing) and the `main` branch (for production) of the `dssquad-app` repository. If needed, other branches can be linked to Streamlit Sharing during development. Streamlit Sharing builds and deploys the app in response to a repository `push` event, i.e. anytime a commit is pushed the app with build and and deploy.

