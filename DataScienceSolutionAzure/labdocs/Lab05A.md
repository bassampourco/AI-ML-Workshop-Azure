# Lab 5A: Working with Environments

All Python code runs in the context of an environment, which determines the Python packages available. When you run a script as an experiment in Azure Machine Learning, you can configure the environment in which it runs.

## Before You Start

Before you start this lab, ensure that you have completed [Lab 1A](Lab01A.md) and [Lab 1B](Lab01B.md), which include tasks to create the Azure Machine Learning workspace and other resources used in this lab.

## Environments

Azure Machine Learning environments specify the Python packages, environment variables, and software settings around your training and scoring scripts. They also specify run times (Python, Spark, or Docker). The environments are managed and versioned entities within your Machine Learning workspace that enable reproducible, auditable, and portable machine learning workflows across a variety of compute targets.

Azure Machine Learning provides a default environment that includes many common packages; including the azureml-defaults package that contains the libraries necessary for working with an experiment run, as well as popular packages like pandas and numpy.You can also define your own environment and add packages by using conda or pip, to ensure your experiment has access to all the libraries it requires.

Environments can broadly be divided into three categories: curated, user-managed, and system-managed.

 - Curated environments are provided by Azure Machine Learning and are available in your workspace by default. They contain collections of Python packages and settings to help you get started with various machine learning frameworks.
 
 - In user-managed environments, you're responsible for setting up your environment and installing every package that your training script needs on the compute target. Conda doesn't check your environment or install anything for you. If you're defining your own environment, you must list azureml-defaults with version >= 1.0.45 as a pip dependency. This package contains the functionality that's needed to host the model as a web service.

 - You use system-managed environments when you want Conda to manage the Python environment and the script dependencies for you. The service assumes this type of environment by default, because of its usefulness on remote compute targets that are not manually configurable
 
 https://docs.microsoft.com/en-us/azure/machine-learning/how-to-use-environments
 
 
#### Environment class

Configures a reproducible Python environment for machine learning experiments.

#### The DockerSection class 

is used in the Environment class to customize and control the final resulting Docker image that contains the specified environment.When you enable Docker, the service builds a Docker image. It also creates a Python environment that uses your specifications within that Docker container. This functionality provides additional isolation and reproducibility for your training runs.By default, the newly built Docker image appears in the container registry that's associated with the workspace.

#### PythonSection class

Defines the Python environment and interpreter to use on a target compute for a run.

#### CondaDependencies class 

Manages application dependencies in an Azure Machine Learning environment.If no parameters are specified, azureml-defaults is added as the only pip dependency.


## Task 1: Work with Environments

In this task, you'll use code in a notebook to work with environments for Azure Machine Learning experiments.

1. In [Azure Machine Learning studio](https://ml.azure.com), view the **Compute** page for your workspace; and on the **Compute Instances** tab, start your compute instance.
2. When the compute instance is running, refresh the Azure Machine Learning studio web page in your browser to ensure your authenticated session has not expired. Then click the **Jupyter** link to open the Jupyter home page in a new browser tab.
3. In the Jupyter home page, in the **Users/AI-ML-Workshop-Azure/DataSienceSolutionAzure** folder, open the **05A - Working with Environments.ipynb** notebook. Then read the notes in the notebook, running each code cell in turn.
4. When you have finished running the code in the notebook, on the **File** menu, click **Close and Halt** to close it and shut down its Python kernel. Then close all Jupyter browser tabs.
5. In Azure Machine Learning studio, on the **Compute** page, select your compute instance and click **Stop** to shut it down.
