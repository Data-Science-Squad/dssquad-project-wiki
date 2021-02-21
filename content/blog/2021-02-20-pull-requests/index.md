---
title: Pull Requests
author: ''
weight: 5
date: '2021-02-20'
slug: []
categories: []
tags: []
meta_img: images/image.png
description: Description for the page
---

A Pull Request (PR) is a way to merge code from one branch into another through a formal review process. For example, if you develop code in a feature branch that needs to be merged into the `develop` branch, you will need to submit a PR and the repo administrator will either accept or reject the merge. This is the approach we will take to ensure the protected branches (`main` and `develop`) are maintained at a high standard.

Follow these steps to submit a Pull Request:

1. Create a feature branch
2. Add files, commit, and push the feature branch
3. Sign in to the GitHub repo and click on the 'Pull requests' tab
4. Click 'New pull request'
5. Configure branch comparison using `base:develop` *<-* `compare:your-feature-branch`
6. Click 'Create pull request'
7. Leave a comment describing the PR and click `Create pull request` to finalize
