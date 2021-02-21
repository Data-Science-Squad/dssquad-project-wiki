---
title: Feature branching Git workflow
author: ''
date: '2021-02-20'
slug: []
categories: []
tags: []
meta_img: images/image.png
description: Description for the page
---

Feature branching describes the process of creating Git branches dedicated to specific features without disturbing the `main` or `develop` branches within a repo. Since the `main` and `develop` branches are used for production and development deployments, developers are not able to commit code directly to these branches in any of the project's repositories.

Feature branching allows developers to create features in dedicated branches then submit Pull Requests to merge the feature branches into the `develop` branch. The repo administrator will review the Pull Request and either approve or reject the merge. If approved, the `develop` branch with its new features will replace the current `main` branch.

## Example using the website repo

The following example demonstrates how to contribute to the website repository using feature branching. The basic steps are as follows:

1. Change the local directory to `dssquad-website` 
2. Pull down the current `develop` branch in GitHub
3. Create a feature branch named `new-hugo-theme`
4. Add files, commit, and push the `new-hugo-theme` branch
5. Sign in to GitHub and submit a Pull Request to merge `new-hugo-theme` into the `develop` branch

#### Pull the current state of the remote develop branch

```
# Change the local directory to `dssquad-website` 
cd dssquad-website

# Pull down the current `develop` branch in GitHub
git checkout develop
git pull origin develop

# Create a feature branch named `new-hugo-theme`
git checkout -b new-hugo-theme

# Add files, commit, and push the feature branch
git add --all
git commit -m "selected a new hugo theme that works with blogdown"
git push origin new-hugo-theme
```

Follow [these instructions] to submit a Pull Request to merge the feature branch into the develop branch following a code review.