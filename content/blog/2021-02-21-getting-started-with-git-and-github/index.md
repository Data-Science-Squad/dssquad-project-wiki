---
title: Getting started with Git and our GitHub repositories
author: Danny Morris
date: '2021-02-20'
slug: []
categories: []
tags: []
meta_img: images/image.png
description: Description for the page
weight: 1
---

## Download Git and create a GitHub account

- [Download Git](https://git-scm.com/downloads)
- Create a [GitHub account](https://github.com/)

## Using Git on the command line

Team members are encouraged to use Git in their preferred command shell (e.g. Git Bash, macOS Terminal, Linux Terminal). Using a command shell means all interactions with Git are with [Git commands](https://education.github.com/git-cheat-sheet-education.pdf). While there are GUI tools for simplifying the Git experience, the use of universal Git commands promotes consistency throughout the team through the use of a common syntax.

## Data Science Squad GitHub Organization

The [Data Science Squad Organization](https://github.com/Data-Science-Squad) is a centralized collection of official repositories for our project. The Organization contains separate repositories for each project deliverable to promote organization and minimize interference between team members. All team members should accept their invitations to join the Organization. Though team members will work with their primary repositories most often, all team members will have the opportunity to contribute to other repositories.

## Cloning repositories

Cloning a remote GitHub repository means downloading a copy of the repository into a local directory. Once the repository is cloned into a local directory, the link between the local copy and the remote copy is maintained unless explicitly broken or changed. Maintaining the local-remote connection means developers can interact with the remote GitHub repository by making changes to the local copy and submitting these changes through a series of commits. 

```
# switch to local directory where repo will be downloaded
cd documents

# clone `dssquad-ml` via HTTPS
git clone https://github.com/Data-Science-Squad/dssquad-ml.git

# or clone via SSH if preferred
git clone git@github.com:Data-Science-Squad/dssquad-ml.git

# switch to local repo
cd dsquad-ml
```

## Essential Git commands

Expect to use the following Git commands most frequently.

```
# clone a GitHub repo and switch to the local copy
git clone https://github.com/Data-Science-Squad/<repo>.git
cd <repo>

# create a feature branch
# this is useful for several reasons and is at the core of our project's
# Git philosophy
git checkout -b my-feature-branch

# add/change local files ("stage")
# save changes to local Git repo ("commit") 
# upload the feature branch to GitHub ("push")
git add my_new_file.py # add a specific file
git add --all # or add all files that have been created/changed
git commit -m "short and sweet message describing your changes"
git push origin my-feature-branch

# pull the remote GitHub repo to your local directory to get the current
# state of the remote
# this is useful if there are files/changes in the remote GitHub repo
# that you do not have locally
git pull origin <branch-name>
```

## Feature branching and Pull Requests

Feature branching and Pull Requests are standard Git concepts that we will leverage in our project to promote organization and to maintain our production codebase at a high standard. All team members should familiarize themeselves with these concepts.

Sources:

- Feature branching: https://dssquad-wiki.netlify.app/blog/2021-02-20-feature-branching-git-workflow/
- Pull Requests: https://dssquad-wiki.netlify.app/blog/2021-02-20-pull-requests/
