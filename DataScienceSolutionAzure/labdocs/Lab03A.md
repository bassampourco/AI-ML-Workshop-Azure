# Lab 3A: Running Experiments

Experiments are at the core of a data scientist's work. In Azure Machine Learning, an *experiment* is used to run a script or a pipeline, and usually generates outputs and records metrics.

## Before You Start

Before you start this lab, ensure that you have completed [Lab 1A](Lab01A.md) and [Lab 1B](Lab01B.md), which include tasks to create the Azure Machine Learning workspace and other resources used in this lab.

## Task 1: Run Experiments in a Compute Instance

An Azure Machine Learning Compute Instance provides a useful environment for running experiment code, right in your workspace.

- An Azure Machine Learning experiment represent the collection of trials used to validate a **user's hypothesis**.

- In Azure Machine Learning, an experiment is represented by the Experiment class and a trial is represented by the **Run class**.

![How it Works](https://amlworkshop.blob.core.windows.net/mlworkshop/9-lab3a-experiments-1.png)

- Data scientists and AI developers use the **Azure Machine Learning SDK for Python** to build and run machine learning workflows with the Azure Machine Learning service. You can interact with the service in any Python environment, including Jupyter Notebooks, Visual Studio Code, or your favorite Python IDE.

https://docs.microsoft.com/en-us/python/api/overview/azure/ml/?view=azure-ml-py

https://docs.microsoft.com/en-us/azure/machine-learning/how-to-track-experiments


azureml.core.Experiment : The **Experiment class** is used to submit new experiments and manage experiment history.

- **start_logging** creates an interactive run for use in scenarios such as Jupyter notebooks. Any metrics that are logged during the session are added to the run record in the experiment. If an output directory is specified, the contents of that directory is uploaded as run artifacts upon run completion. (Return type : Run Class )

**Run class (azureml.core.Run):**

- Log a numerical or string value to the run with the given name using log(name, value, description=''). Logging a metric to a run causes that metric to be stored in the run record in the experiment. You can log the same metric multiple times within a run, the result being considered a vector of that metric.Example: run.log("accuracy", 0.95)

- Log a list of values to the run with the given name using log_list(name, value, description='').Example: run.log_list("accuracies", [0.6, 0.7, 0.87])

- Log an image to the run record. Use log_image(name, path=None, plot=None, description='') to log an image file or a matplotlib plot to the run. These images will be visible and comparable in the run record. Example: run.log_image("ROC", plt)

- get_metrics: Retrieve the metrics logged to the run.Example:  metrics = run.get_metrics()

- upload_file: Upload a file to the run record.You can list all of the files that are associated with this run record by called run.get_file_names()

- get_context : Use this method to retrieve the current service context for logging metrics and uploading files.

**RunConfiguration class** (azureml.core.RunConfiguration) :Represents configuration for experiment runs targeting different compute targets in Azure Machine Learning .Create a Run Configuration that defines the Python code execution environment for the script - in this case, it will automatically create a Conda environment with some default Python packages installed

**ScriptRunConfig class**(azureml.core.ScriptRunConfig) :identifies the Python script file to be run in the experiment, and the environment in which to run it

1. In [Azure Machine Learning studio](https://ml.azure.com), view the **Compute** page for your workspace; and on the **Compute Instances** tab, start your compute instance.
2. When the compute instance is running, refresh the Azure Machine Learning studio web page in your browser to ensure your authenticated session has not expired. Then click the **Jupyter** link to open the Jupyter home page in a new browser tab.
3. In the Jupyter home page, in the **Users/AI-ML-Workshop-Azure/DataSienceSolutionAzure** folder, open the **03A - Running Experiments.ipynb** notebook. Then read the notes in the notebook, running each code cell in turn.
4. When you have finished running the code in the notebook, on the **File** menu, click **Close and Halt** to close it and shut down its Python kernel. Then close all Jupyter browser tabs.
5. In Azure Machine Learning studio, on the **Compute** page, select your compute instance and click **Stop** to shut it down.

![How it Works](https://amlworkshop.blob.core.windows.net/mlworkshop/9-lab3a-experiments-2.PNG)

Inside experiements: select **diabetes-experiment** and for both runs try:

select Metrics (chart and Table)

Select Images and look at Lable distrubution

select Output + logs 
