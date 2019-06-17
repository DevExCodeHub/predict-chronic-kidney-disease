# predict-chronic-kidney-disease
This repository explain how to predict chronic kidney disease using various attributes collected from hospitals. Chronic kidney disease (CKD) is a condition characterized by a gradual loss of kidney function over time, which may lead to kidney failure. 

# Data Source:
We are using the UCI Chronic Kidney Disease data set from the Watson Studio community.

## Pre-requisites

* **IBM Cloud account:**  An account must exist to use the platform.
* **Watson Studio service instance:** A service instance must exist to be able to use **IBM Data Refinery**.

## Steps
### Create an IBM cloud account
If you do not have an IBM Cloud account, create an account [here](https://ibm.biz/BdYpAy)
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

