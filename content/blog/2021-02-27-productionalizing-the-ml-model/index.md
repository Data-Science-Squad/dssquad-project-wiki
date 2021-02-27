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

The Machine Learning Engineers should use this document as a guide for converting your model into a production asset and automating it. Note that this process can be started whenever a prototype model is ready, even if you intend to improve upon the model.

The model should be on a **daily release cycle**, meaning each day the forecast model will be automatically re-run using new data (i.e. new crime incidents). This is made possible through the use of [GitHub Actions](https://dssquad-wiki.netlify.app/blog/2021-02-23-github-actions/), which is a feature within GitHub that triggers code to run in response to some "event". In our case, the model code will be triggered whenever there is a push to the main branch.

:raising_hands: The three basic steps to productionize the model include:

1. Convert your Jupyter Notebook into one more Python scripts for training and inference.

2. Create a `requirements.txt` file containing the libraries and their versions needed to run the model.

3. Create a GitHub Actions configuration file that instructs GitHub to run the training/inference script whenever there is a push to the main branch.

For an example of what the production (main) GitHub branch should ultimately look like, vist https://github.com/Data-Science-Squad/dssquad-ml/tree/dm_example_github_actions

### 1. Converting the Jupyter Notebook into Python script(s)

Once you have a working model, convert your Jupyter Notebook into one or more Python scripts for collecting data, training, inference, logging metrics, and inserting predictions in the database. A simple solution is to create a single Python script called `train.py` to perform all of these steps. This file should contain only the essentials for running your model.

Example:

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

This file will enable automation of the model. Read about this file [here](https://github.com/Data-Science-Squad/dssquad-ml/tree/dm_example_github_actions).

