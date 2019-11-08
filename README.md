In this Digital Developer Conference challenge, you'll learn how to deploy your first Cloud Foundry application to IBM Cloud using an automated deployment through an IBM Cloud DevOps Toolchain. The toolchain will then build and deploy your application to IBM Cloud when you click a **Deploy to IBM Cloud** button in a later step.

The toolchain that will be created for you looks like this:

![IBM Cloud toolchain](images/toolchain.png)

This toolchain has four components:

1. Issue management through a hosted GitLab instance on IBM Cloud.
2. A git repo hosted on IBM Cloud.
3. The Eclipse Orion web IDE.
4. A delivery pipeline to build and deploy your application to IBM Cloud.

The pipeline that will build and deploy your application looks like this:

![Build and Deploy Pipeline](images/pipeline.png)

This pipeline has the following two steps:

1. Build: Your application code will be pulled from your repo and the dependencies will be built.
2. Deploy: Your application's build artifacts will then be deployed to IBM Cloud.

## Application and Toolchain Files
This simple application utilizes the vue.js framework to display a simple single page application. Webpack is then utilized to bundle the frontend files into static assets. Node.js and Express are then used to serve the application

The vue.js application files can be found in the **/src** directory of this repository. 

Those files are then bundled into the **/dist** folder by webpack.

Then **/bin/www** and **app.js** are the Node.js files that utilize express to serve the frontend application while **/routes** contains the file to route requests to the homepage.

As for the toolchain, we are utilizing the default toolchain template to build our toolchain for us. The template can be seen [here](https://github.com/open-toolchain/default-toolchain).

In that repo, the **/.bluemix** directory contains the toolchain and pipeline files.

- **toolchain.yml** contains the structure of the toolchain including the cloned repo, the pipeline, and the web IDE integration.

- **pipeline.yml** contains the definition of the pipeline which in this case only has two stages: build and deploy.

## Prerequisites

You must register for an IBM Cloud account before you can complete this challenge.

## Estimated time

This challenge should take you approximately 10 minutes to complete.

## Steps

1. Click the **Deploy to IBM Cloud** image below:

   [![Deploy to IBM Cloud](https://cloud.ibm.com/devops/setup/deploy/button.svg)](https://cloud.ibm.com/devops/setup/deploy?repository=https://github.com/omidmeh/ddc-challenge-1.git&branch=master)

2. You will be prompted to sign into IBM Cloud. Enter your account information if you have not already signed in.
3. The toolchain creation page opens. Enter a new name for your toolchain. Make a note of the region that displays under **Select Region** -- you will need to use this region name in a later section. The region might not be *Dallas* as shown in the image below because the toolchain attempts to select the region closest to you.

   ![new name](images/newName.png)

4. Click on **Delivery Pipeline** in the Tool Integrations section. You will need to update your pipeline configuration settings.

   ![Tool integrations](images/toolIntegrations.png)

5. Click the **Create** button next to **IBM Cloud API Key** field. A pop-up window opens.

   ![pipeline configurations](images/pipelineConfigurations.png)

6. The window asks if you want to create a new API key for this pipeline. Click **Create**.

   ![API popup](images/APICreate.png)

7. You will see information such as **Region**, **Space**, and **Organization** displayed. If no organization or space displays, update the **Region** field. In particular, if *Washington DC* is selected, switch to the *Dallas* region.

    ![Change Delivery Pipeline Region](images/setDeliveryPipelineRegion.png)

8. Click **Create** at the top right of the page. Your new toolchain is displayed.
9. You can click on the pipeline to view your application being built or you can remain on the toolchain page until the pipeline finishes building.
10. From the toolchain page, go to the application console by clicking on **View Console** on the Deploy pipeline tile.

    ![View App Console](images/viewAppConsole.png)

11. Open the application from the App Console by clicking on **Visit App URL**.

     **Note**: Due to Internet Explorer and Microsoft Edge limitations, the application will not display in those browsers. We recommended that you open your application using Firefox, Chrome, or Safari instead.

   ![View app URL](images/viewAppURL.png)

If you have completed all the steps correctly, you will see the following image displayed on the home page of your new application:

![IBM Cloud deployment success!](images/thumbsUp.png)

## Summary
In this challenge, you deployed your first application using IBM Cloud DevOps Toolchains, which enabled you to automatically build and push the application to IBM Cloud. Be sure to explore your newly deployed app, and remember to complete the other challenges.
