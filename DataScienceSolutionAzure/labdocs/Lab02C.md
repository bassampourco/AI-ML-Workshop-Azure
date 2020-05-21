# Lab 2C: Automated ML-UI

Automated machine learning, also referred to as automated ML, is the process of automating the time consuming, iterative tasks of machine learning model development. It allows data scientists, analysts, and developers to build ML models with high scale, efficiency, and productivity all while sustaining model quality.

Apply automated ML when you want Azure Machine Learning to train and tune a model for you using the target metric you specify. Automated ML democratizes the machine learning model development process, and empowers its users, no matter their data science expertise, to identify an end-to-end machine learning pipeline for any problem.

![How it Works](https://docs.microsoft.com/en-us/azure/machine-learning/media/concept-automated-ml/automl-concept-diagram2.png)

## Before You Start

Before you start this lab, ensure that you have completed [Lab 1A](Lab01A.md) and [Lab 1B](Lab01B.md), which include tasks to create the Azure Machine Learning workspace and other resources used in this lab.

## Task 1: Create and run the experiment

![How it Works](https://docs.microsoft.com/en-us/azure/machine-learning/media/tutorial-first-experiment-automated-ml/get-started.png)

1- New Automated ML run

2- Select **diabetes dataset**

3- Experiement name: **AutoML-UI**

4- Target column: **Diabetic**

5- Training cluster: **aml-cluster**

6- select **Classification**

7- On View additional configuration setting :

1. Primary metric: **AUC weighted**

2. Exit criterion , Training job time (hours) : **1**

3. Run


[![Watch the video](https://amlworkshop.blob.core.windows.net/mlworkshop/8-AutoML-UI.png)](https://amlworkshop.blob.core.windows.net/mlworkshop/8-AutoML-UI.mp4)


