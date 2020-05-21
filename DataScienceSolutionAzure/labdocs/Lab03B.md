# Lab 3B: Training and Registering Models

Machine Learning is primarily about training models that you can use to provide predictive services to applications; so now it;s time to see how you can use Azure Machine Learning experiments to run training scripts, and how to register the resulting trained models.

## Before You Start

Before you start this lab, ensure that you have completed [Lab 1A](Lab01A.md) and [Lab 1B](Lab01B.md), which include tasks to create the Azure Machine Learning workspace and other resources used in this lab.

Previously, you ran experiment scripts using a **RunConfiguration and a ScriptRunConfig**. You can use the **same approach** to run a training script, but using an **Estimator** is generally easier as it ***abstracts both of these configurations in a single object***.

- **Estimator classes** make it easy to train models based on popular machine learning frameworks. There are estimator classes for **Scikit-learn, PyTorch, TensorFlow, and Chainer**. There is also a generic estimator that can be used with frameworks that do not already have a dedicated estimator class. You don't have to worry about defining a run configuration when using estimators.

https://docs.microsoft.com/en-us/python/api/azureml-train-core/azureml.train.estimator.estimator?view=azure-ml-py

from azureml.train.estimator import Estimator

from azureml.train.sklearn import SKLearn

from azureml.train.dnn import TensorFlow

from azureml.train.dnn import PyTorch

- **Model Registeration** Registering a model creates a logical container for the one or more files that make up your model. In addition to the content of the model file itself, a registered model also stores model metadata, including model description, tags, and framework information, that is useful when managing and deploying the model in your workspace. 

from azureml.core import Model - Model.register will register a model from **local file system** where the model assets are located.

also Run class (run.register_model) will register the modle from run which located in outputs folder

![How it Works](https://amlworkshop.blob.core.windows.net/mlworkshop/10-Lab3b-model.PNG)

- **Parameterized Training Script** You can increase the flexibility of your training experiment by adding parameters to your script, enabling you to repeat the same training experiment with different settings.

argparse.ArgumentParser().add_argument('--reg_rate', type=float, dest='reg', default=0.01)

If the dest argument is provided, the value is saved using that name when the command-line arguments are parsed.

## Task 1: Use the Azure Machine Learning SDK to Train and Register Models

In this task, you'll use code in a notebook to run training scripts as Azure Machine Learning experiments.

1. In [Azure Machine Learning studio](https://ml.azure.com), view the **Compute** page for your workspace; and on the **Compute Instances** tab, start your compute instance.
2. When the compute instance is running, refresh the Azure Machine Learning studio web page in your browser to ensure your authenticated session has not expired. Then click the **Jupyter** link to open the Jupyter home page in a new browser tab.
3. In the Jupyter home page, in the **Users/AI-ML-Workshop-Azure/DataSienceSolutionAzure** folder, open the **03B - Training Models.ipynb** notebook. Then read the notes in the notebook, running each code cell in turn.
4. When you have finished running the code in the notebook, on the **File** menu, click **Close and Halt** to close it and shut down its Python kernel. Then close all Jupyter browser tabs.
5. In Azure Machine Learning studio, on the **Compute** page, select your compute instance and click **Stop** to shut it down.
