# Lab 7A: Creating a Real-time Inferencing Service

There's no point in training and registering models if you don't plan to make them available for applications to use. In this lab, you'll deploy a model as a web service for real-time inferencing.

## Before You Start

Before you start this lab, ensure that you have completed [Lab 1A](Lab01A.md) and [Lab 1B](Lab01B.md), which include tasks to create the Azure Machine Learning workspace and other resources used in this lab.

## Prepare to deploy
 
To deploy the model as a service, you need the following components:

 - #### Define inference environment.
   This environment encapsulates the dependencies required to run your model for inference.An inference configuration describes how to set up the web-service containing your model. It's used later, when you deploy the model.
Inference configuration uses Azure Machine Learning environments to define the software dependencies needed for your deployment. Environments allow you to create, manage, and reuse the software dependencies required for training and deployment. You can create an environment from custom dependency files or use one of the curated Azure Machine Learning environments.
   
 - #### Define scoring code. 
   This script accepts requests, scores the requests by using the model, and returns the results.The entry script receives data submitted to a deployed web service and passes it to the model. It then takes the response returned by the model and returns that to the client. The script is specific to your model. It must understand the data that the model expects and returns.The script contains two functions that load and run the model:
   
   - init(): Typically, this function loads the model into a global object. This function is run only once, when the Docker container for your web service is started.
   - run(input_data): This function uses the model to predict a value based on the input data. Inputs and outputs of the run typically use JSON for serialization and deserialization. You can also work with raw binary data. You can transform the data before sending it to the model or before returning it to the client.
   
 - #### Define inference configuration. 
   The inference configuration specifies the environment configuration, entry script, and other components needed to run the model as a service.
   
Once you have the necessary components, you can profile the service that will be created as a result of deploying your model to understand its CPU and memory requirements.

## Deploy to target

Deployment uses the inference configuration deployment configuration to deploy the models. The deployment process is similar regardless of the compute target. Deploying to AKS is slightly different because you must provide a reference to the AKS cluster.

You can deploy a model as a real-time web service to several kinds of compute target, including local compute, an Azure Machine Learning compute instance,  an Azure Container Instance (ACI), an Azure Kubernetes Service (AKS) cluster, an Azure Function, or an Internet of Things (IoT) module. Azure Machine Learning uses containers as a deployment mechanism, packaging the model and the code to use it as an image that can be deployed to a container in your chosen compute target. 

### AciWebservice class

Represents a machine learning model deployed as a web service endpoint on Azure Container Instances.
A deployed service is created from a model, script, and associated files. The resulting web service is a load-balanced, HTTP endpoint with a REST API. You can send data to this API and receive the prediction returned by the model.

### InferenceConfig class

Represents configuration settings for a custom environment used for deployment.Inference configuration is an input parameter for Model deployment-related actions


 more info: https://docs.microsoft.com/en-us/azure/machine-learning/how-to-deploy-and-where
 
## Task 1: Create a Real-time Inferencing Service

In this task, you'll create a real-time inferencing service as an Azure Container Instance (ACI).

1. In [Azure Machine Learning studio](https://ml.azure.com), view the **Compute** page for your workspace; and on the **Compute Instances** tab, start your compute instance.
2. When the compute instance is running, refresh the Azure Machine Learning studio web page in your browser to ensure your authenticated session has not expired. Then click the **Jupyter** link to open the Jupyter home page in a new browser tab.
3. In the Jupyter home page, in the **Users/AI-ML-Workshop-Azure/DataSienceSolutionAzure** folder, open the **07A - Creating a Real-time Inferencing Service.ipynb** notebook. Then read the notes in the notebook, running each code cell in turn.
4. When you have finished running the code in the notebook, on the **File** menu, click **Close and Halt** to close it and shut down its Python kernel. Then close all Jupyter browser tabs.
5. In Azure Machine Learning studio, on the **Compute** page, select your compute instance and click **Stop** to shut it down.

![How it Works](https://amlworkshop.blob.core.windows.net/mlworkshop/16-Lab7a.PNG)
