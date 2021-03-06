# ITRY SCDF IBM Challenge 2020
This repository contains the files neccessary for the description and submission of the project as well as a step-by-step installation guides.

## Contents

1.[Short Description](#Short-Description)

2.[Pitch Video](#Ptich-Video)

3.[Architecture of project](#Architecture-of-project)

4.[Detailed Description](#Detailed-description)

5.[Prerequisites](#Prerequisites)

6.[Getting started](#Getting-started)

7.[Software required](#Software-required)

8.[Data Services](#Data-services)

9.[Authors](#Authors)

10.[Acknowledgements](#Acknowledgements)

## Short Description
### 1.1 What's the problem ? 
With an increasingly ageing population and a growing segment of vulnerable populations specifically the increasing trend of elderly with no next of kin, Community First Responders (CFRs) must be alerted at the onset of incidents which require emergency response (e.g. cardiac arrests, falls, unattended cooking fires etc.) and mobilised for effective early intervention.

For the general population, alerting CFRs about the situation is seen as a rather simple step to accomplish,the same cannot be said for the elderly. This problem is further compounded by fact that we see more elderly living alone with no next of kin to look out for them. Often, cases involving elderly go unreported until it is too late. The lingering smell of decomposed bodies and an individuals prolonged absence or a full-on-fire are the only tell-tale signs of an emergency that has occured sometime back.

### 1.2 How does technology help?

Advancements in statistics and technology has blessed us with data analytics, sensors and data storage solutions like the cloud. This has allowed us to collect , store and analyse information about the environment around us automatically. All these can be pivoted towards emergency response as  ameans of detecting emergencies which could have been unseen when no one is available to report or witness them. The availability of such information allows CFRs to kick into gear for effective early intervention before it escalates to anything more.


### 1.3 Idea of project
Our team has decided to make use of Internet of Things (IOT) devices to collect data via sensor from andriod devices, transmit data to the cloud and make use of IBM Watson Studio and Jupyter Notebook (R Studio) to analyse and visualise the data for comparison. In case of abnormal activites or reading from daily routines, the CFRs will be activated to investigate the situation. This can improve SCDF sense-making to be alerted at the onset of incidents which require emergency response and mobilise the CFRs for effective early intervention for the elderly population. Ultimately, this framework will be integrated with myResponder appUltimately, this framework will be integrated with myResponder app

## Pitch video

[![Watch Video](https://github.com/Bet365619/ITRY_Pompeii_SCDFXIBM/blob/master/Video-IMG/Video-Pitch.png)](https://youtu.be/La1nkP_5otk)

## Architecture of project
![Architecture of project](https://github.com/Bet365619/ITRY/blob/master/TIMELINE/Architecture-of-Project-ITRY.png)

1.	User’s and his/her surrounding environment’s variables (e.g. Movement of user, Temperature) are detected by the IoT device and sent as data packets from smartphone periodically.
2.	The data from the IoT device are streamed to the IoT platform via node red.
3.	Node red also gives the instruction for the sensor data to be sent to cloudant app.
4.	Data from the IoT device can be retrieved and visualised for live movement tracking.
5.	Sensor data is also stored in db2 for future use.
6.	Sensor data is imported to  Watson studios .
7.	Data is refined with Data Refinery app.
8.	Refined data is imported to Jupyter Notebook where further data wrangling and statistical analysis is conducted to detect any changes is   user’s behaviour.
9.	Visualisation of data can also be generated look for behavioural changes visually.
10.	Statistical results from analysis is passed to Firebase through Push Notification.
11.	In the event a drastic change, which renders an emergency event (i.e. Condition in Firebase Met), CFRs and SCDF will be notified via push notification.


## Detailed description
[More detail is available here](DESCRIPTION.md)
## Prerequisites
1. An IBM Cloud account; if you do not have an existing IBM Cloud account, [start your free trial](https://cloud.ibm.com/registration?cm_sp=ibmdev-_-developer-tutorials-_-cloudreg). Learn more about IBM Cloud by reviewing the [Getting Started documentation](https://cloud.ibm.com/docs).
2. Download and install the [IBM Cloud CLI and Developer Tools](https://cloud.ibm.com/docs/cli?topic=cli-getting-started).
3. A smartphone (an Android or iOS device)
4. Jupyter notebook install [here](https://jupyter.org/install.html).
## Getting started
### Step by step guide to build the analytical device
### Step 1 Creating an IOT app in IBM cloud
Work through the steps in this tutorial to create a [Node-RED and Watson IoT Platform starter app in IBM Cloud](https://developer.ibm.com/tutorials/how-to-create-an-internet-of-things-platform-starter-application/).

As a result, you will have a Node-RED Starter Kit application connected to the IBM IoT platform.As a result, you will have a Node-RED Starter Kit application connected to the IBM IoT platform.

### Step 2 Add a device that will send MQTT messages to the IBM Watson IoT Platform
1. After completing the setup in step 1, the  IBM Watson IoT Platform console is opened.
![IOT Platform](https://github.com/Bet365619/ITRY/blob/master/Setup_IMG/IOT/IOT-Platform.jpg)
An organisation id is being assigned to your app, as shown in the picture labelled as 1.
![IOT-Label1](https://github.com/Bet365619/ITRY/blob/master/Setup_IMG/IOT/IOT-1.png)

In this case, the organisation id is pu3272 which is located at the top right corner of the dashboard. 

2. Click Add Device Type. In your organization, you can have multiple device types each with multiple devices. A device type is a group of devices that share characteristics; for example, they might provide the same sensor data. In our case, the device type name must be “Android” (this device type name is required by the app that you will use later).

3. Click Next. A page is displayed where you can enter metadata about the device type, such as a serial number or model. You don’t need to specify this information for this tutorial. Just click Finish.
![IOT-label2](https://github.com/Bet365619/ITRY/blob/master/Setup_IMG/IOT/IOT-2.png)

4. Click Register Devices. Enter the device ID. The device ID can be, for example, the MAC address of your smartphone. However, it must be unique within your organization only. For example in this instance, the device ID is "androidchris".
![IOT-label3](https://github.com/Bet365619/ITRY/blob/master/Setup_IMG/IOT/IOT-3.png)
5. Click Next. A page is displayed where you could enter metadata about the device. Leave it blank, and click Next.

6. On the security page, enter any value for the authentication token(Password). Remember this value for later. Then, click Next.

7. Messages are now ready to be sent from registered device to IOT platform.

### Step 3 Downloading and installing App on mobile device

You will use the IoT Starter for Android app to read and send sensor data on your smartphone. The source code and documentation of the app are in the [iot-starter-for-android GitHub project](https://github.com/ibm-watson-iot/iot-starter-for-android). The [Apk installation file](https://github.com/deveops/iot-starter-for-android/releases) for android devices can be found here.

### Step 4 Allow permission of IOT starter on mobile device
1. Go to Settings on mobile phone.

2. Go to Application Management. ![Setting-1](https://github.com/Bet365619/ITRY/blob/master/Setup_IMG/Settings/Settings-1.png)

3. Search for application called IOT Starter. ![Setting-2](https://github.com/Bet365619/ITRY/blob/master/Setup_IMG/Settings/Settings-2.png)

4. Go to Permissions. ![Setting-3](https://github.com/Bet365619/ITRY/blob/master/Setup_IMG/Settings/Settings-3.png)

5. CLick on allow "location" to allow data to flow. ![Setting-4](https://github.com/Bet365619/ITRY/blob/master/Setup_IMG/Settings/Settings-4.png)

6. Turn on share "location" before starting application. ![Setting-5](https://github.com/Bet365619/ITRY/blob/master/Setup_IMG/Settings/Settings-5.png)

### Step 5 Configuring the mobile device
1. Start the IoT Starter app.
2. Click Skip tutorial.
3. Enter the following parameters:
Organization: The organization ID that was displayed on the IBM IoT server at the top right corner of dashboard. For example, pu3272 in this tutorial.
Device ID: The device ID that you configured above. For example, “andriodchris” in this tutorial.
Auth Token: The authorization token that you specified earlier.
Make sure that USE SSL is checked.
![Login](https://github.com/Bet365619/ITRY/blob/master/Setup_IMG/Settings/Login.png)
Upon clicking on Activate Sensor, the app collects data from the acceleration sensor in your smartphone and sends the data to the IBM IoT server. The app displays the accelerometer data and the number of messages that were published or received. The data is being sent back into the IBM IOT server to be compiled into a json file for further analysis.
![Sensor-data](https://github.com/Bet365619/ITRY/blob/master/Setup_IMG/Settings/Sensor-Data.png)

### Step 6 Data visualization using IOT platform 
The following graph is obtained from the IOT platform where the data is recorded and visualized. The sharp increase in acceleration is due to a simulated fall of the android device together with the elderly.
![Visualization of Sensor Data](https://github.com/Bet365619/ITRY/blob/master/Setup_IMG/IOT/Data-visualization-of-accelerator.png)

### Step 7 Using of saved data to be analysed using R in Jupyter Notebook
Other than accelerometer data of the user, temperature data of the user's residence is also an important metric that can potentially indicate signs of an emergency.

Data stored in the database can be extracted and be analysed. 
The following are library to be used and packages to be installed when using Jupyter Notebook:
```bash
#If required
# install.packages("ggplot2")
# install.packages("jsonlite", repos="http://cran.r-project.org")
# install.packages("readr")
library(readr)
library(ggplot2)
library(sqldf)
library(httr)
library(RCurl)
library(bitops)
library(jsonlite)
library(stringr)
```

1. Import the [code](https://github.com/Bet365619/ITRY/blob/master/Code/Anomaly-Detection.R) to Jupyter Notebook.

2. Read the [json file](https://github.com/Bet365619/ITRY/blob/master/Setup_IMG/Parameter%20Config/Config.json) to obtain the configuration for the various parameters (Time and Date etc). This will be useful to harmonise similar data with different format in order to make analysis and evaluation possible later in this step.

![json-1](https://github.com/Bet365619/ITRY/blob/master/Code/Config%20data.png)

3. Read the [csv file](https://github.com/Bet365619/ITRY/blob/master/Sample_Data/sample_sensordata.csv) to obtain the sample time series data used for the analysis.
![Import](https://github.com/Bet365619/ITRY/blob/master/Code/Import.png)

4. From the time series data, subset 2 time series data of 2 different days with some time periods. (E.g. Day1 12am to 12pm, Day2 12am to 12pm. The photo below shows the splitting into two subset of time series data
![Compare](https://github.com/Bet365619/ITRY/blob/master/Code/Split.png)
5. Construct plots (Boxplots and trendline)
![Plots](https://github.com/Bet365619/ITRY/blob/master/Code/Plotting.png)
The below shows the plots of the two subset time series data obtained in line and boxplot format.
![Sensor-Reading](https://github.com/Bet365619/ITRY/blob/master/Code/Sensor-reading.png)
![Box-plot](https://github.com/Bet365619/ITRY/blob/master/Code/Box-plot.png)

6. Statistical matrix.
![statistic](https://github.com/Bet365619/ITRY/blob/master/Code/statistic.png)

7. Comparing differences.
![Comparing](https://github.com/Bet365619/ITRY/blob/master/Code/comparing-differences.png)

### Step 8 Push Notification
Push Notifications is available as an IBM Cloud catalog service in the Web and Mobile category and enables you to send and manage mobile and web push notifications. A push notification is an alert to indicate a change or update on a mobile device or browser.

Push Notifications are a universally accepted communication channel across enterprises or for a wide spectrum of audience. You can deliver these notifications as an onscreen banner alert or to a device's locked screen, thus providing information updates that are quickly and easily accessible.

The basic steps that get you started:
1. [Create an IBM Cloud Push Notifications service instance](https://cloud.ibm.com/docs/mobilepush?topic=mobilepush-push_step_1a)
2. [Obtain your notification provider credentials](https://cloud.ibm.com/docs/mobilepush?topic=mobilepush-push_step_1)
3. [Configure the service instance](https://cloud.ibm.com/docs/mobilepush?topic=mobilepush-push_step_2)
4. [Setup Push notifications service client SDKs](https://cloud.ibm.com/docs/mobilepush?topic=mobilepush-push_step_3)
5. [Send a notification](https://cloud.ibm.com/docs/mobilepush?topic=mobilepush-push_step_4)
![Push Notifications service lifecycle](https://github.com/Bet365619/ITRY/blob/master/Push-notification/Push.png)


## Software required
* Jupyter Notebook

* IBM Node-Red

* IBM Firebase


## Data services
* [IBM Cloudant](https://cloud.ibm.com/catalog?search=cloudant#search_results) - The NoSQL database used
* [IBM Cloud Functions](https://cloud.ibm.com/catalog?search=cloud%20functions#search_results) - The computing platform for handling logic
* [IBM IOT platform](https://cloud.ibm.com/catalog/services/internet-of-things-platform) -  The hub for IBM Watson IoT and lets you communicate with and consume data from connected devices and gateways
* [IBM Watson Studio](https://cloud.ibm.com/catalog/services/watson-studio) -  Watson Studio provides a suite of tools and a collaborative environment for data scientists, developers and domain experts.
* [IBM DB2](https://cloud.ibm.com/catalog/services/db2v) - A fully-managed cloud database
* [IBM Push Notifications](https://cloud.ibm.com/catalog/services/push-notifications) - The Push Notifications service provides a unified push service to send real-time notifications to mobile and web applications. The service provides the ability to personalize and send notifications to a segment of users, single user or broadcast to all users.

## Authors 
* **Rui Jie** 
* **Ismail** 
* **Yu Da** 
* **Zhi Hao** 

## Acknowledgements
We would like to take this opportunity to thank and acknowledge IBM and SCDF for organising the Call for Code 2020.

