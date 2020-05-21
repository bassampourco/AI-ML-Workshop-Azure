# Lab 6A: Creating a Pipeline

You can use the Azure Machine Learning SDK to perform all of the tasks required to create and operate a machine learning solution in Azure. Rather than perform these tasks individually, you can use *pipelines* to orchestrate the steps required to prepare data, run training scripts, register models, and other tasks.

## Before You Start

Before you start this lab, ensure that you have completed [Lab 1A](Lab01A.md) and [Lab 1B](Lab01B.md), which include tasks to create the Azure Machine Learning workspace and other resources used in this lab.

## Azure ML pipelines

An Azure Machine Learning pipeline is an independently executable workflow of a complete machine learning task. Subtasks are encapsulated as a series of steps within the pipeline. An Azure Machine Learning pipeline can be as simple as one that calls a Python script, so may do just about anything. Pipelines should focus on machine learning tasks such as:

 - Data preparation including importing, validating and cleaning, munging and transformation, normalization, and staging
 - Training configuration including parameterizing arguments, filepaths, and logging / reporting configurations
 - Training and validating efficiently and repeatedly. Efficiency might come from specifying specific data subsets, different hardware compute resources, distributed processing, and progress monitoring
 - Deployment, including versioning, scaling, provisioning, and access control

Independent steps allow multiple data scientists to work on the same pipeline at the same time without over-taxing compute resources. Separate steps also make it easy to use different compute types/sizes for each step.

## Why build pipelines?

With pipelines, you can optimize your workflow with simplicity, speed, portability, and reuse. When building pipelines with Azure Machine Learning, you can focus on what you know best — machine learning — rather than infrastructure.

Using distinct steps makes it possible to rerun only the steps you need as you tweak and test your workflow. Once the pipeline is designed, there is often more fine-tuning around the training loop of the pipeline. When you rerun a pipeline, the execution jumps to the steps that need to be rerun, such as an updated training script, and skips what hasn't changed. The same paradigm applies to unchanged scripts and metadata.

With Azure Machine Learning, you can use distinct toolkits and frameworks for each step in your pipeline. Azure coordinates between the various compute targets you use so that your intermediate data can be shared with the downstream compute targets easily

![](https://github.com/Azure/MachineLearningNotebooks/blob/master/how-to-use-azureml/machine-learning-pipelines/aml-pipelines-concept.png)

#### azureml-pipeline-steps package

Contains pre-built steps that can be executed in an Azure Machine Learning Pipeline.

Azure ML Pipeline steps can be configured together to construct a Pipeline, which represents a shareable and reusable Azure Machine Learning workflow. Each step of a pipeline can be configured to allow reuse of its previous run results if the step contents (scripts and dependencies) as well as inputs and parameters remain unchanged

Common kinds of step in an Azure Machine Learning pipeline include: 

● PythonScriptStep: Runs a specified Python script.

● EstimatorStep:  Runs an estimator. 

● DataTransferStep: Uses Azure Data Factory to copy data between data stores. 

● DatabricksStep: Runs a notebook, script, or compiled JAR on a databricks cluster. 

● AdlaStep: Runs a U-SQL job in Azure Data Lake Analytics. 

https://docs.microsoft.com/en-us/python/api/azureml-pipeline-steps/azureml.pipeline.steps?view=azure-ml-py

#### PipelineData class

Represents intermediate data in an Azure Machine Learning pipeline.

Data used in pipeline can be produced by one step and consumed in another step by providing a PipelineData object as an output of one step and an input of one or more subsequent steps.




## Task 1: Create a Pipeline

In this task, you'll create a pipeline to train and register a model.

1. In [Azure Machine Learning studio](https://ml.azure.com), view the **Compute** page for your workspace; and on the **Compute Instances** tab, start your compute instance.
2. When the compute instance is running, refresh the Azure Machine Learning studio web page in your browser to ensure your authenticated session has not expired. Then click the **Jupyter** link to open the Jupyter home page in a new browser tab.
3. In the Jupyter home page, in the **Users/AI-ML-Workshop-Azure/DataSienceSolutionAzure** folder, open the **06A - Creating a Pipeline.ipynb** notebook. Then read the notes in the notebook, running each code cell in turn.
4. When you have finished running the code in the notebook, on the **File** menu, click **Close and Halt** to close it and shut down its Python kernel. Then close all Jupyter browser tabs.
5. In Azure Machine Learning studio, on the **Compute** page, select your compute instance and click **Stop** to shut it down.

![How it Works](https://amlworkshop.blob.core.windows.net/mlworkshop/14-Lab6a.png)
