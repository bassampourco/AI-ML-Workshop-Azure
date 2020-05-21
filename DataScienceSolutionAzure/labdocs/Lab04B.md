# Lab 4B: Working with Datasets

Datasets provide a way to encapsulate data for experiments and training. You can use tabular and file datasets to define versioned sources of data that can easily be consumed in experiments.

## Before You Start

Before you start this lab, ensure that you have completed [Lab 1A](Lab01A.md) and [Lab 1B](Lab01B.md), which include tasks to create the Azure Machine Learning workspace and other resources used in this lab.

## Datasets

Azure Machine Learning datasets are references that point to the data in your storage service. They aren't copies of your data, so no extra storage cost is incurred. To interact with your data in storage, create a dataset to package your data into a consumable object for machine learning tasks. Register the dataset to your workspace to share and reuse it across different experiments without data ingestion complexities.

We support 2 types of datasets:

 - A TabularDataset represents data in a tabular format by parsing the provided file or list of files. You can load a TabularDataset into a Pandas or Spark DataFrame for further manipulation and cleansing. For a complete list of data formats you can create TabularDatasets from, see the TabularDatasetFactory class.

 - A FileDataset references single or multiple files in your datastores or public URLs. You can download or mount files referenced by FileDatasets to your compute target.(like unstructured data ,images,documents,etc.)

In **Datasets class**:

 - Dataset.Tabular.from_delimited_files() : Returns a TabularDataset object
 
 - Dataset.File.from_files()
 
we can register and retrive rigistered dataset
 
 - register(workspace, name, description=None, tags=None, create_new_version=False) : Register the dataset to the provided workspace.
 
 - get_by_id(workspace, id) : Get a Dataset which is saved to the workspace.
 
 - get_by_name(workspace, name, version='latest') : Get a registered Dataset from workspace by its registration name.
 
 - as_named_input(name) : Provide a name for this dataset which will be used to retrieve the materialized dataset in the run.
 
When you need to access a dataset in an experiment script, you can pass the dataset as an input to a ScriptRunConfig or an Estimator.  

## Task 1: Work with Datasets

In this task, you'll use code in a notebook to work with tabular and file datasets.

1. In [Azure Machine Learning studio](https://ml.azure.com), view the **Compute** page for your workspace; and on the **Compute Instances** tab, start your compute instance.
2. When the compute instance is running, refresh the Azure Machine Learning studio web page in your browser to ensure your authenticated session has not expired. Then click the **Jupyter** link to open the Jupyter home page in a new browser tab.
3. In the Jupyter home page, in the **Users/AI-ML-Workshop-Azure/DataSienceSolutionAzure** folder, open the **04B - Working with Datasets.ipynb** notebook. Then read the notes in the notebook, running each code cell in turn.
4. When you have finished running the code in the notebook, on the **File** menu, click **Close and Halt** to close it and shut down its Python kernel. Then close all Jupyter browser tabs.
5. In Azure Machine Learning studio, on the **Compute** page, select your compute instance and click **Stop** to shut it down.

![How it Works](https://amlworkshop.blob.core.windows.net/mlworkshop/12-Lab4b.PNG)
