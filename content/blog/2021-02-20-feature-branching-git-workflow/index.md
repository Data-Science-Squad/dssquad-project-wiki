---
title: Feature Branching
author: ''
date: '2021-02-20'
slug: []
categories: []
tags: []
meta_img: images/image.png
description: Description for the page
weight: 2
---

Feature branching describes the process of creating Git branches for adding new features to the codebase without disturbing the `main` or `develop` branches within a remote repository. For example, website developers may create a feature branch called `home-page` specifically for building the home page of the website. Once completed, this feature branch can be merged into the production codebase through a formal review process.

## Protecting the main and develop branches

The `main` and `develop` branches represent our production (`main`) and development (`develop`) codebases. These branches are **protected**, meaning developers cannot commit code directly to them. They should also be "deployable", meaning these branches should only contain functioning code that produces some desired output. The `main` branch should always deploy production code (e.g. the production website), while the `develop` branch may contain a production alternative for testing new features.

## Merging feature branches into main and develop branches

Feature branches can be merged into the other branches through Pull Requests. When a Pull Request is submitted, the repo administrator will review the Pull Request and either approve or reject the proposed merge. If accepted, the feature branch is merged into the target branch..

Developers should only submit Pull Requests to merge feature branches into the `develop` branch in order to test new features and any other changes made to the codebase. Feature branches will never merged directly into the `main` branch. They must go through the `develop` branch first to be reviewed. Eventually, the `develop` branch codebase will reach a "production state", at which point the `develop` branch will be merged into the production `main` branch.

## Example feature branching using the website repo

The following example demonstrates how to contribute to the website repository using feature branching. The basic steps are as follows:

1. Clone the `dssquad-website` repo and change your directory to the local copy.
2. Pull down the current `develop` branch in GitHub.
3. Create a feature branch named `new-hugo-theme`.
4. Add files, commit, and push the `new-hugo-theme` branch.
5. Once complete, sign in to GitHub and submit a Pull Request to merge `new-hugo-theme` into the `develop` branch

A full code sample...

```
# Clone the repo and switch to the local directory
git clone https://github.com/Data-Science-Squad/dssquad-website.git
cd dssquad-website

# Pull down the current `develop` branch in GitHub
git checkout develop
git pull origin develop

# Create a feature branch named `new-hugo-theme` and switch to it
git checkout -b new-hugo-theme

# Add files, commit, and push the feature branch
git add --all
git commit -m "changed the hugo theme to a more modern style"
git push origin new-hugo-theme
```

To merge the `new-hugo-theme` feature branch into the `develop` branch, [submit a Pull Request](https://dssquad-wiki.netlify.app/blog/2021-02-20-pull-requests/) and the repo administrator will review your code.

## Recommended feature branching strategies for each team

**Data Engineering:** Create a feature branch (e.g. `datakit`) for version 1 of the datakit codebase. Have a team member push this feature branch and submit a Pull Request to merge `datakit` into the `develop` branch. Continue to use feature branches and merge into `develop` as needed. An administrator will review the feature branch and it's functionality.

**Machine Learning:** Create branches for individual members (e.g. `gayatri_dobhal` and `nisrine_hammout`) for all development purposes (e.g. notebooks for EDA, training, testing, etc.). When version 1 of the model is ready for production integration, coordinate with Danny to gather requirements.

**Web application:** Configure Streamlit Sharing to deploy the `main` and `develop` branches to separate URLs. Use the `main` branch for the final production app and the `develop` branch for a development version. Develop new features using feature branches (e.g. `date_range_slider`), then submit Pull Requests to merge feature branches into the `develop` branch. An administrator will review the feature branch and it's functionality.

**Website:** Configure Netlify to deploy the `main` branch and the `develop` branch to separate URLs. Use the `main` branch for the production website and the `develop` branch for development website. Develop new features using feature branches (e.g. `meet_the_team_page`), then submit a Pull Request to merge feature branches into the `develop` branch. An administrator will review the feature branch and it's functionality. All team members can contribute to the website (e.g. personal articles) by following this workflow.
