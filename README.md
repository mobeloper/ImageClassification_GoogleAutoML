# ImageClassification_GoogleAutoML
Here I use Google VertexAI, the newest AI product offering available on Google Cloud, to create a dataset to train an image classification model and deploy it to a production end-point for cloud inferences.

# Overview
1. Create an image classification dataset and import images.
2. Train an AutoML image classification model.
3. Deploy a model to an endpoint and send a prediction.

# Setup and requirements
Sign in to Google Console.
Enable the APIs.
In the Google Cloud Console, on the Navigation menu, click Vertex AI > Dashboard.
Click Enable all recommended APIs.

# Introduction to Vertex AI 
Vertex AI integrates the ML offerings across Google Cloud into a seamless development experience. Previously, models trained with AutoML and custom models were accessible via separate services. The new offering combines both into a single API, along with other new products. You can also migrate existing projects to Vertex AI. If you have any feedback, please see the Get support page.

Vertex AI includes many different products to support end-to-end ML workflows. This lab focuses on the products highlighted below: Training/HP-Tuning and Notebooks.

A diagram displaying the Vertex AI products, with the Training and Notebooks products highlighted.

PART 1. Create an image classification dataset and import images
Image data input file
The image files you use in this tutorial are from the flower dataset used in this Tensorflow blog post. These input images are stored in a public Cloud Storage bucket. This publicly accessible bucket also contains a CSV file you use for data import. This file has two columns: the first column lists an image's URI in Cloud Storage, and the second column contains the image's label. Following are some sample rows.

gs://cloud-training/mlongcp/v3.0_MLonGC/toy_data/flowers_toy.csv:

gs://cloud-samples-data/ai-platform/flowers/daisy/10559679065_50d2b16f6d.jpg,daisy
gs://cloud-samples-data/ai-platform/flowers/dandelion/10828951106_c3cd47983f.jpg,dandelion
gs://cloud-samples-data/ai-platform/flowers/roses/14312910041_b747240d56_n.jpg,roses
gs://cloud-samples-data/ai-platform/flowers/sunflowers/127192624_afa3d9cb84.jpg,sunflowers
gs://cloud-samples-data/ai-platform/flowers/tulips/13979098645_50b9eebc02_n.jpg,tulips
Copied!
Create an image classification dataset and import data
To begin the process of creating your dataset and training your image classification model, on the Vertex AI page, in the navigation pane, click Dashboard.

In the central pane, click Create dataset.

Optional: Specify a name for this dataset.

For Select a data type and objective, on the Image tab, select Image classification (Single-label).

For Region, select REGION.

To create the empty dataset, click Create.
The Data import page opens.

Select Select import files from Cloud Storage, and specify the Cloud Storage URI of the CSV file with the image location and label data.

The CSV file is at: gs://cloud-training/mlongcp/v3.0_MLonGC/toy_data/flowers_toy.csv.

For Import file path, type cloud-training/mlongcp/v3.0_MLonGC/toy_data/flowers_toy.csv

To begin image import, click Continue.

The import process takes about 15 minutes. When it is complete, the next page shows all of the images, both labeled and unlabeled, identified for your dataset.

PART 2. Train an AutoML image classification model
Use the Google Cloud Console to train an AutoML image classification model. After your dataset is created and data is imported, use the Cloud Console to review the training images and begin model training.

Review imported images
After the dataset is imported, the Browse tab opens. You can also access this tab by selecting Datasets from the side menu, and then selecting the annotation set (set of single-label image annotations) associated with your new dataset.

Begin AutoML model training
On the Browse tab, you can choose Train new model to begin training. You can also start training by selecting Models from the side menu, then selecting Create.

On the Vertex AI page, in the navigation pane, click Model Registry.
To open the Train new model page, click Create.
Under Training method, select the target Dataset and Annotation set if they are not automatically selected.
Select AutoML, and then click Continue.
Optional: Under Model details, type a Model name.
Click Continue.
Leave the Explainability section as default and click Continue.
Under Compute and pricing, for Budget, enter 8 maximum node hours.
Click Start training.
Training takes about 2 hours. When the model finishes training, it is displayed with a green checkmark status icon.

PART 3. Deploy a model to an endpoint and send a prediction
After your AutoML image classification model training is complete, use the Google Cloud Console to create an endpoint and deploy your model to the endpoint. After your model is deployed to this new endpoint, send an image to the model for label prediction.

Deploy your model to an endpoint
Access your trained model to deploy it to a new or existing endpoint from the Models page.

On the Vertex AI page, in the navigation pane, click Model Registry.

Select your trained AutoML model and then click on Version ID.

The Evaluate tab opens, where you can view model performance metrics.

On the Deploy & Test tab, click Deploy to endpoint.
The Endpoint options page opens.

Under Define your endpoint, select Create new endpoint, and for Endpoint name, type hello_automl_image.

Click Continue.

Under Model settings, accept the Traffic split of 100%, and set the Number of compute nodes to 1.

Click Deploy.

It takes about 20 minutes to create the endpoint and deploy the AutoML model to the new endpoint.

Send a prediction to your model
After the endpoint creation process finishes, you can send a single image annotation (prediction) request in the Cloud Console.

In the Test your model section of the same Deploy & test tab you used to create an endpoint in the previous subtask, click Upload image, choose a local image for prediction, and view its predicted label.
The Test your model page, which includes an image and the Filter labels panel with several filters listed.


