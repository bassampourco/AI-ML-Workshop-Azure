# Lab 5B: Working with Compute Targets

While you can run experiments on your local compute, in many cases you'll want to leverage cloud compute for increased scalability.

## Before You Start

Before you start this lab, ensure that you have completed [Lab 1A](Lab01A.md) and [Lab 1B](Lab01B.md), which include tasks to create the Azure Machine Learning workspace and other resources used in this lab.

### Types of Compute 

A compute target is a designated compute resource/environment where you run your training script or host your service deployment. This location may be your local machine or a cloud-based compute resource. Using compute targets make it easy for you to later change your compute environment without having to change your code.

 - Local Compute  
 
 - Training Clusters 
 
 - Inference Clusters
 
 - Attached Compute 
 
**ComputeTarget class** Abstract parent class for all compute targets managed by Azure Machine Learning.

**ComputeTargetException class** An exception related to failures when creating, interacting with, or configuring a compute target. This exception is commonly raised for failures attaching a compute target, missing headers, and unsupported configuration values.


**AmlCompute class** Manages an Azure Machine Learning compute in Azure Machine Learning. An Azure Machine Learning Compute (AmlCompute) is a managed-compute infrastructure that allows you to easily create a single or multi-node compute. The compute is created within your workspace region as a resource that can be shared with other users 

Also provisioning_configuration Create a configuration object for provisioning an AmlCompute target.


![How it Works](https://amlworkshop.blob.core.windows.net/mlworkshop/13-Lab5b.PNG)

## Task 1: Work with Compute Targets

In this task, you'll run a training experiment on a cloud-based compute target.

1. In [Azure Machine Learning studio](https://ml.azure.com), view the **Compute** page for your workspace; and on the **Compute Instances** tab, start your compute instance.
2. When the compute instance is running, refresh the Azure Machine Learning studio web page in your browser to ensure your authenticated session has not expired. Then click the **Jupyter** link to open the Jupyter home page in a new browser tab.
3. In the Jupyter home page, in the **Users/AI-ML-Workshop-Azure/DataSienceSolutionAzure** folder, open the **05B - Working with Compute Targets.ipynb** notebook. Then read the notes in the notebook, running each code cell in turn.
4. When you have finished running the code in the notebook, on the **File** menu, click **Close and Halt** to close it and shut down its Python kernel. Then close all Jupyter browser tabs.
5. In Azure Machine Learning studio, on the **Compute** page, select your compute instance and click **Stop** to shut it down.
