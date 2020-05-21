# Lab 8A: Tuning Hyperparameters

Hyperparameters are variables that affect how a model is trained, but which can't be derived from the training data. Choosing the optimal hyperparameter values for model training can be difficult, and usually involved a great deal of trial and error.

In this lab, you'll use Azure Machine Learning to tune hyperparameters by performing multiple training runs in parallel.

## Before You Start

Before you start this lab, ensure that you have completed [Lab 1A](Lab01A.md) and [Lab 1B](Lab01B.md), which include tasks to create the Azure Machine Learning workspace and other resources used in this lab.

## What are hyperparameters?

Hyperparameters are adjustable parameters you choose to train a model that govern the training process itself. For example, to train a deep neural network, you decide the number of hidden layers in the network and the number of nodes in each layer prior to training the model. These values usually stay constant during the training process.

In deep learning / machine learning scenarios, model performance depends heavily on the hyperparameter values selected. The goal of hyperparameter exploration is to search across various hyperparameter configurations to find a configuration that results in the best performance. Typically, the hyperparameter exploration process is painstakingly manual, given that the search space is vast and evaluation of each configuration can be expensive.

## Azure Machine Learning allows you to automate hyperparameter exploration

Azure Machine Learning allows you to automate hyperparameter exploration in an efficient manner, saving you significant time and resources. You specify the range of hyperparameter values and a maximum number of training runs. The system then automatically launches multiple simultaneous runs with different parameter configurations and finds the configuration that results in the best performance, measured by the metric you choose. Poorly performing training runs are automatically early terminated, reducing wastage of compute resources. These resources are instead used to explore other hyperparameter configurations.

## Types of hyperparameters 

 - Continuous hyperparameters
 
 - Discrete hyperparameters
 
 
## Sampling the hyperparameter space

You can also specify the parameter sampling method to use over the hyperparameter space definition. Azure Machine Learning supports random sampling, grid sampling, and Bayesian sampling.

 - Grid sampling
 
 - Random sampling
 
 - Bayesian sampling
 

## Specify early termination policy

Terminate poorly performing runs automatically with an early termination policy. Termination reduces wastage of resources and instead uses these resources for exploring other parameter configurations.

 - Bandit policy
 
 - Median stopping policy
 
 - Truncation selection policy
 
##  azureml.train.hyperdrive package

Contains modules and classes supporting hyperparameter tuning.

Hyperparameters are adjustable parameters you choose for model training that guide the training process. The HyperDrive package helps you automate choosing these parameters. For example, you can define the parameter search space as discrete or continuous, and a sampling method over the search space as random, grid, or Bayesian. Also, you can specify a primary metric to optimize in the hyperparameter tuning experiment, and whether to minimize or maximize that metric. You can also define early termination policies in which poorly performing experiment runs are canceled and new ones started. To define a reusable machine learning workflow for HyperDrive, use hyper_drive_step to create a Pipeline.

https://docs.microsoft.com/en-us/python/api/azureml-train-core/azureml.train.hyperdrive?view=azure-ml-py


## Task 1: Tune Hyperparameters

In this task, you'll run an experiment to optimize hyperparameters for model training.

1. In [Azure Machine Learning studio](https://ml.azure.com), view the **Compute** page for your workspace; and on the **Compute Instances** tab, start your compute instance.
2. When the compute instance is running, refresh the Azure Machine Learning studio web page in your browser to ensure your authenticated session has not expired. Then click the **Jupyter** link to open the Jupyter home page in a new browser tab.
3. In the Jupyter home page, in the **Users/AI-ML-Workshop-Azure/DataSienceSolutionAzure** folder, open the **08A - Tuning Hyperparameters.ipynb** notebook. Then read the notes in the notebook, running each code cell in turn.
4. When you have finished running the code in the notebook, on the **File** menu, click **Close and Halt** to close it and shut down its Python kernel. Then close all Jupyter browser tabs.
5. In Azure Machine Learning studio, on the **Compute** page, select your compute instance and click **Stop** to shut it down.
