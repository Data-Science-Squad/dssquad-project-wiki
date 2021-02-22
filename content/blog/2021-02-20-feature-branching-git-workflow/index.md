---
title: Using the Feature Branching strategy to safely and rapidly introduce new features into the codebase
author: ''
date: '2021-02-20'
slug: []
categories: []
tags: []
meta_img: images/image.png
description: Description for the page
weight: 2
---

Feature branching describes the process of creating Git branches dedicated to specific project features without disturbing the `main` or `develop` branches within a repo. For example, website developers may create a feature branch called `home-page` for building the home page of the website. Once a Pull Request and code review have been completed, the feature branch is merged into the production codebase.

The `main` and `develop` branches in each repository should always be "deployable", meaning these branches should only contain working code for either production (`main`) or dev/testing (`develop`). Developers are not able to commit code directly to these branches in any of the project's repositories, thus feature branching is needed.

Feature branches can be merged into the `develop` and `main` branches through Pull Requests. Developers submit Pull Requests when the feature branch is complete and needs to be reviewed. The repo administrator will review the Pull Request and either approve or reject the merge. If accepted, the feature branch can be deleted.

## Example feature branching using the website repo

The following example demonstrates how to contribute to the website repository using feature branching. The basic steps are as follows:

1. Change your local directory to the `dssquad-website` project.
2. Pull down the current `develop` branch in GitHub.
3. Create a feature branch named `new-hugo-theme`.
4. Add files, commit, and push the `new-hugo-theme` branch.
5. Once complete, sign in to GitHub and submit a Pull Request to merge `new-hugo-theme` into the `develop` branch

A full code sample...

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

To merge the `new-hugo-theme` feature branch, [submit a Pull Request](https://dssquad-wiki.netlify.app/blog/2021-02-20-pull-requests/).

## Recommended feature branching strategies for each team

**Data Engineering:** Create a feature branch (e.g. `datakit`) for version 1 of the datakit. Have a team member push this feature branch and submit a Pull Request to merge `datakit` into the `develop` branch. Continue to use feature branches and merge into `develop` as needed. An administrator will review the feature branch and it's functionality.

**Machine Learning:** Create branches for individual members (e.g. `gayatri_dobhal` and `nisrine_hammout`) for all development purposes (e.g. notebooks for EDA, training, testing, etc.). When version 1 of the model is ready for integration into dev and prod environments, coordinate with Danny to gather requirements for a feature branch.

**Web application:** Configure Streamlit Sharing to deploy the `main` and `develop` branches to separate URLs. Use the `main` branch for the final production app and the `develop` branch for a development version. Develop new features using feature branches (e.g. `date_range_slider`), then submit Pull Requests to merge feature branches into the `develop` branch. An administrator will review the feature branch and it's functionality.

**Website:** Configure Netlify to deploy the `main` branch and the `develop` to separate URLs. Use the `main` branch for the production website and the `develop` branch for development website. Develop new features using feature branches (e.g. `meet_the_team_page`), then submit a Pull Request to merge feature branches into the `develop` branch. An administrator will review the feature branch and it's functionality. All team members can contribute to the website (e.g. personal articles) by following this workflow.
