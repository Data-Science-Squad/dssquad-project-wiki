---
title: Logging ML metrics in Neptune
author: Danny Morris
date: '2021-02-27'
slug: []
categories: []
tags: []
meta_img: images/image.png
description: Description for the page
---

[neptune.ai](https://neptune.ai/) is a service for logging and tracking machine learning model metrics and performance. Neptune can be used during development to track experiments and compare models, and it can be used in production to monitor model performance with each new training run.

The following code snippets demonstrates the basic usage of neptune.ai.

### Prerequisites

Set the following environment variables to set a connection to our project workspace in Neptune. Contact Danny to obtain an API token. Alternatively, a team member can create a new account (and project) and manage the credentials.

```
import os
os.environ["NEPTUNE_API_TOKEN"] = ""
os.environ["NEPTUNE_PROJECT_DEV"] = "dannymorris/DS-Squad-Dev"
os.environ["NEPTUNE_PROJECT_PROD"] = "dannymorris/DS-Squad-Prod"
```

### Run experiments and log metrics

Add the following example code to your scripts and notebooks. Modify as needed.

```
# Define lightgbm hyperparameters
LGBM_PARAMS = {
          'boosting_type': 'gbdt',
          'objective': 'multiclass',
          'num_class': 3,
          'num_leaves': 27,
          'learning_rate': 0.01,
          'feature_fraction': 0.2,
          'seed': 1234
          }
          
# Initialize Neptune, provide API token, and connect to project Dev workspace
neptune.init(api_token=os.getenv('NEPTUNE_API_TOKEN'),
             project_qualified_name=os.getenv('NEPTUNE_PROJECT_DEV'))          
          
# Register an experiment in Neptune
experiment_name = 'test-lightgbm'
neptune.create_experiment(experiment_name, params={**LGBM_PARAMS})

# Compute accuracy, RMSE, etc. and log in Neptune
accuracy = accuracy_score(y_test, y_test_pred.argmax(axis=1))
neptune.log_metric('accuracy', accuracy)
```