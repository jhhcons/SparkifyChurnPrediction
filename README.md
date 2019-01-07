# Readme - Data Science Capstone - Churn Prediction at Sparkify

# Project Definition

## Overview

This project is part of my Data Science nano-degree at Udacity. In this final project, i will attempt to create a machine learning model, which will be able to predict when users at Sparkify are about to churn. Sparkify is a fictional music service much like spotify, and to aid me in my creation of this model, they have served me 12GBs of event data.

The possible event types are:

+--------------------------+

|                    Cancel|

|          Submit Downgrade|

|               Thumbs Down|

|                      Home|

|                 Downgrade|

|               Roll Advert|

|                    Logout|

|             Save Settings|

| Cancellation Confirmation|

|                     About|

|                  Settings|

|           Add to Playlist|

|                Add Friend|

|                  NextSong|

|                 Thumbs Up|

|                      Help|

|                   Upgrade|

|                     Error|

|            Submit Upgrade|

+--------------------------+

Where the type 'Cancellation Confirmation' is set equal to users churning.


## Problem

The problem is a fairly straightforward modeling problem. 

The real challenge in this project is that because of the large amout of data, all of our data wrangeling and model creating has to be done using Apache Spark. This adds another level of abstraction on top of the allready well-established process, but it does enable us to work with bigger data than we would otherwise be able to.

## Expected Results

At the end of this project, a model for churn prediction should have been created and evaluated. The model should have been trained and tested on a subset of the 12GB of data, and the final testing should happen on completely seperate validation set. A accuracy, F1-Score confusion matrix will be used to evaluate the performance and feasibility of the model.

# Actual Results

At the end of this project, two main iteration on a churn-prediction model were implemented and evaluated. The first model
used a simple pivot of the evnet that seemed to contain the most relevant difference between churning and non-churning users. 

Three models were trained with this data, givin the following F1 Values:

Gradient Boosted Trees - 68.9%

Random Forest - 68.4%

SVM - 68.4%

While the values look promising, inspection of the confusion matricies revealed that SVM and Random Forest classified all users as non-churning, but because of the the relative low number of churned users, the F1 score was still fairly high.

The best performing model for the first iteration was Gradient Boosted Trees, which managed to predict 17 churners correctly.

For the second iteration, two new features were introduced. Number of sessions and days from first to last recorded event.

Using these features, the Graident Boosted Trees algorithm was once agian trained.

The results were much better than the inital attempt. With a F1-score of 89.1% for validation data, and 294 correcly identified churners, the second iteration of the model is a great first model which could be fine-tuned and improved even more.

# Files
Files included in this project are:

README.md - This readme

Sparkify.html/ipynb - notebook used for POC in Udacity Workspace

JHH_Udacity_Notebook.html/ipynb - notebook used for managing spark cluster on full dataset in AWS

# References

For this project, the couse material at Udacity has been used for reference. On top of that, the official pySpark documentation has also been used ( https://spark.apache.org/docs/latest/api/python/index.html )


# Blog Post

The blogpost descriping this project can be found at https://medium.com/@jhhcons/distributed-machine-learning-at-sparkify-578719e627fe

