---
title: Productionizing the ML model
author: Danny Morris
date: '2021-02-27'
slug: []
categories: []
tags: []
meta_img: images/image.png
description: Description for the page
---

This document serves as a guide for putting the ML model into production. Note that this process can be started whenever a prototype model is ready, even if you intend to make improvements.

The model will be retrained daily whenever there is a push to the `main` branch of the `dssquad-ml` repository. This automation is made possible through the use of [GitHub Actions](https://dssquad-wiki.netlify.app/blog/2021-02-23-github-actions/).

:raising_hands: The four basic steps to put the model into production:

1. Convert your Jupyter Notebook into one more Python scripts for importing data, training, and inserting predictions into the database. This could be a single `train.py` file to keep it simple.

2. Create a `requirements.txt` file containing the libraries and their versions needed to run the model.

3. Create a GitHub Actions configuration file located in `.github/workflows/<filename>.yml` that instructs GitHub to run the training/prediction script whenever there is a push to the `main` branch.

4. Merge these assets into the `main` branch with a [Pull Request](https://dssquad-wiki.netlify.app/blog/2021-02-20-pull-requests/).

**Important**: The model and supporting assets should be merged into the `develop` branch (via pull request) first for testing and receiving feedback. Once approved, submit a pull request to merge the `develop` branch into the `main` branch.

For an example of what the production GitHub branch should look like, vist https://github.com/Data-Science-Squad/dssquad-ml/tree/dm_example_github_actions

### 1. Converting the Jupyter Notebook into Python script(s)

Once you have a working model, convert your Jupyter Notebook into one or more Python scripts for collecting data, training, inference, logging metrics, and inserting predictions in the database. A simple solution is to create a single Python script called `train.py` to perform all of these steps. This file should contain only the essentials for running your model.

```
# train.py pseudo-code
import <libraries>
read_data()
train()
predict()
log_metrics()
insert_predictions_into_db()
```

### 2. Create a `requirements.txt` file with your libraries

This file simply contains all necessary libraries and their versions needed to run `train.py`.

```
# requirements.txt example

neptune-client==0.4.130
neptune-contrib==0.27.0
numpy==1.19.0
scikit-learn==0.23.1
mysql-connector-python==8.0.23   
mysqlclient==2.0.3
```

### 3. Create a GitHub Actions configuration file

This file will enable automation of the model. An example file is located [here](https://github.com/Data-Science-Squad/dssquad-ml/blob/dm_example_github_actions/.github/workflows/train_and_predict.yml).

