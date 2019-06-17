# Predict Chronic Kidney Disease
This repository explain how to predict chronic kidney disease using various attributes collected from hospitals. Chronic kidney disease (CKD) is a condition characterized by a gradual loss of kidney function over time, which may lead to kidney failure. 

# Data Source:
We are using the UCI Chronic Kidney Disease data set from the Watson Studio community.

## Pre-requisites

* **IBM Cloud account:**  An account must exist to use the platform.
* **Watson Studio service instance:** A service instance must exist to be able to use **IBM Data Refinery**.

## Steps
### Create an IBM cloud account
If you do not have an IBM Cloud account, create an account [here](https://ibm.biz/BdzztD)
- A Lite account, which is a free of charge. Make sure to set the region to US South.

### Create a Watson Studio service instance
If you don't have a **watson Studio** instance, do the following:

1. Select Catalog found at the top right of the page.
2. Click on Watson from the menu on the left, which you can find under Platform services.
3. Select Browse Services under **Watson Services**.
4. Choose **watson Studio** instance
<p align="center"><img width="947" alt="untitled" src="https://user-images.githubusercontent.com/20974667/48708706-50914980-ec14-11e8-8768-23092ab0b330.png"> 
 
* Once the main page of the service appears, click on Get Started. This will redirect your browser to the Watson Studio platform. It might ask to confirm IBM Cloud organization and space information.

### Create a Standard Project in Watson Studio
From the Get Started page, select **Creat a Project**

![](https://user-images.githubusercontent.com/20974667/48708691-4a9b6880-ec14-11e8-8936-64d0ec4f6b8b.png)

Then Choose a **Standard plan**

![](https://user-images.githubusercontent.com/20974667/48708692-4a9b6880-ec14-11e8-88a6-928cc5646f13.png)

* Make sure a cloud storage instance exists, or add a new **IBM Cloud Object Storage** instance by clicking on Add under Select storage service.

![](https://user-images.githubusercontent.com/20974667/48709557-da421680-ec16-11e8-8c07-c90b29db12e2.png)

### Add the dataset to the project from Community

### Create SPSS Modeler Flow:
Give a name and description to the flow and select the IBM SPSS Modeler runtime.

## Nodes In IBM SPSS Modeler Flow:

Before starting with the analysis, let’s have a look at different node options available in SPSS Modeler Flow.

On left side panel (Nodes Palette) you can see different types of nodes available for you to use while working on your data. There are six types of node categories:

1. Record Operations: As the name suggests, you can use them to perform operations such as selecting, appending, sorting on the record (row) level.
2.Field Operations: These nodes are helpful in the data preparation phase. You can filter data, rename features, and choose the type of your attributes.
3. Graphs: Nodes in this section will help you with basic data exploration and understanding distribution or relationship between features.
4. Modeling: These nodes provide different modeling algorithms for different types of problems.
5. Outputs: These nodes are helpful in understanding your data and model. You can display results in table format or get a report on evaluation parameters of your model.
6. Export: After processing and modeling, this node will help you export data from the flow editor to your Watson Studio project.



