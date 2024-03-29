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

From the Left menu in Watson Studio, choose Community

![Screenshot (34)](https://user-images.githubusercontent.com/37486654/59593500-c00fde80-90fa-11e9-8a1f-e192d41d8ad1.png)
Search for 'Chronic kidney disease'

![Screenshot (35)](https://user-images.githubusercontent.com/37486654/59593505-c1410b80-90fa-11e9-93b3-4b78ec7830f9.png)

Choose the correct search result and add it to your project from the **plus** icon. Select your project from drop down menu and press add.

![Screenshot (37)](https://user-images.githubusercontent.com/37486654/59593507-c1d9a200-90fa-11e9-8e46-29cbb9d75ad6.png)



Navigate back to your project

![Screenshot (38)](https://user-images.githubusercontent.com/37486654/59593508-c1d9a200-90fa-11e9-9e32-d59f986fd441.png)


### Create SPSS Modeler Flow
Give a name and description to the flow and select the IBM SPSS Modeler runtime.

![Screenshot (14)](https://user-images.githubusercontent.com/37486654/59591315-7b824400-90f6-11e9-9b0d-c9d373c7db09.png)

## Nodes In IBM SPSS Modeler Flow:

Before starting with the analysis, let’s have a look at different node options available in SPSS Modeler Flow.

On left side panel (Nodes Palette) you can see different types of nodes available for you to use while working on your data. There are six types of node categories:

1. Record Operations: As the name suggests, you can use them to perform operations such as selecting, appending, sorting on the record (row) level.
2.Field Operations: These nodes are helpful in the data preparation phase. You can filter data, rename features, and choose the type of your attributes.
3. Graphs: Nodes in this section will help you with basic data exploration and understanding distribution or relationship between features.
4. Modeling: These nodes provide different modeling algorithms for different types of problems.
5. Outputs: These nodes are helpful in understanding your data and model. You can display results in table format or get a report on evaluation parameters of your model.
6. Export: After processing and modeling, this node will help you export data from the flow editor to your Watson Studio project.

### Import the dataset to the flow

From **Import** drag and drop (data assset) node, navigate through to add the chronic kidney disease dataset from the project in the canvas.
Click **Save** when you have changed the data source successfully.

![Screenshot (17)](https://user-images.githubusercontent.com/37486654/59591316-7b824400-90f6-11e9-95b2-5662535bf661.png)
![Screenshot (18)](https://user-images.githubusercontent.com/37486654/59591318-7c1ada80-90f6-11e9-816a-43f130a5587b.png)
![Screenshot (19)](https://user-images.githubusercontent.com/37486654/59591293-77562680-90f6-11e9-8eba-dbd2c0734955.png)

## Data Cleaning

There are two issues to deal with in the dataset, few columns have missing value (?) as mode. We can drop those features using the Filter node, and then we will drop rows with missing values using the Select node. In this way, we can retain the maximum number of records.

### Drop Columns

1. To drop columns drag and drop Filter node on the canvas and connect it with data node.
2. Right click and open the node. Select below columns under filter section [bgr,sod,pot,hemo,pcv,wbcc & rbcc] 
**make sure to check box** — Filter selected fields and hit save button.

![Screenshot (20)](https://user-images.githubusercontent.com/37486654/59591294-77eebd00-90f6-11e9-95ed-a4951901809d.png)

### Drop Rows

1. Drag and drop Select node on the canvas, connect it with Filter node, right click and open the node.
2. Select **discard mode** and provide **below condition** to remove rows with missing values.
```
sg = '?' or al= '?' or su= '?' or rbc= '?' or pc= '?' or pcc= '?' or ba= '?' or bu= '?' or appet= '?' or pe= '?' or ane= '?'
```

![Screenshot (23)](https://user-images.githubusercontent.com/37486654/59591299-78875380-90f6-11e9-876a-1337c16846ed.png)

The data is clean now, we can set our class variable as the target variable using the **Type** node. It will help our model to distinguish between input and target features.

![Screenshot (25)](https://user-images.githubusercontent.com/37486654/59591302-791fea00-90f6-11e9-9825-c653f4fdb587.png)

1. Drag and drop the Type node on the canvas, connect it with Select node, right click and open the node.
2. Click on configure types. Select column name class, change role to target hit ok and then save.

### Partition the dataset

We will partition the dataset to percentage of 70% for training and 30% for testing.

![Screenshot (30)](https://user-images.githubusercontent.com/37486654/59591309-7ae9ad80-90f6-11e9-8dfd-9dfd1d25c2d0.png)

### Fit the classification model. 

We will be using a C5.0 algorithm to build a decision tree. A C5.0 model works by splitting the data based on the field that provides the maximum information gain.You can see **node C5.0** under the Modeling section of the nodes palette.

Select the target of the model (class) from the drop down menu, select the input as all fields except partition. Finally, choose partition for partiotion option.

![Screenshot (28)](https://user-images.githubusercontent.com/37486654/59596365-3a8f2d00-9100-11e9-9654-9b73159b7b2d.png)

In the Build Option, check (use partitioned data)

![Screenshot (29)](https://user-images.githubusercontent.com/37486654/59596366-3a8f2d00-9100-11e9-9872-119ec42230e2.png)



Right-click on the **orange color node** and view the model. You can see predictor importance, tree digram, and other model information here.

![Screenshot (31)](https://user-images.githubusercontent.com/37486654/59591310-7ae9ad80-90f6-11e9-92f0-3b772c7cb946.png)
![Screenshot (32)](https://user-images.githubusercontent.com/37486654/59591312-7ae9ad80-90f6-11e9-8500-884ff6440a8f.png)

### Evaluate model performance
Select the Analysis node from the Output section of the node palette and connect it with the model. Similarly, use the Table node to view data in a table format with predicted labels and confidence.

![Screenshot (33) - Copy](https://user-images.githubusercontent.com/37486654/59591313-7b824400-90f6-11e9-9306-cd0677f028c2.png)

## Reference
Snehal Gawas, [Predict Chronic Kidney Disease Using SPSS Modeler Flows](
https://medium.com/ibm-data-science-experience/predict-chronic-kidney-disease-using-spss-modeler-flows-cf82a16835a8)

