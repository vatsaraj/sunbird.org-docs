---
type: landing
directory: developer-docs/installation
title: Developer Installation
page_title: Developer Installation
description: Installing the Sunbird portal or web application
published: true
allowSearch: true
---

## Overview

This page provides information for you to install and run a Sunbird instance on your laptop or desktop. The intent is to give you a look and feel of some of the features of Sunbird, be able to tweak around with the front-end code. This developer installation of Sunbird application and the cloud APIs used therein, are not intended for production purposes.

> The Sunbird developer installation can be best viewed via the Google Chrome browser. Although, other browsers may be used, but some pages might not render correctly.

> Sunbird developer installation is intended for the web. It cannot be used on mobile devices and Single Sign On (SSO).  

## Intended Audience

The intended audience of this document is a person who is familiar with installing, configuring, and deploying nodejs based open-source software.

## Prerequisites

## Prerequisites

1. **Software**: Install the following software: 
   * [node](https://nodejs.org/dist/v8.11.2/) - Install the latest release version 8.11.2 LTS series
   * [nodemon](https://www.npmjs.com/package/nodemon) - Latest version  
   * [git](https://git-scm.com/downloads) - Latest version. WINDOWS users ensure that you select the Git Bash option in the installation wizard.
   * [gulp](https://gulpjs.com/) - Install **gulp** via npm, which gets installed when **nodejs** is installed
   * (For WINDOWS installation only)
   		* [ng](https://cli.angular.io/) - Install Angular CLI

1. **API Keys**
The Sunbird developer instance is powered by cloud hosted Sunbird APIs, which require an API key. To get an API key, submit an [API Key Request](https://goo.gl/forms/2tRDfLlbJ2IgjWgA2). In the form, provide information about your team and what brings you to Sunbird. 

> It may take up to a couple of business days (IST) to send you the API key. We regret the inconvenience caused due to such delays. 

## System Requirements

To install Sunbird, ensure that your laptop or desktop has the following minimum system requirements:

- Operating System: Ubuntu Linux 16.04 or later, Mac OS X 10.0 and above, or Windows 7 and above
- RAM: > 1.5GB
- CPU: 2 cores (> 2 GHz/core)

## Components Installed

The Sunbird installation has two primary software components:
- Portal or web application
- Services stack or the backend API interface

This version installs the portal web application and uses the cloud-hosted services stack


## Set up the Application

These instructions install Sunbird version 1.9. The code examples provided here are Linux based. For installation on WINDOWS<sup>(R)</sup> it is suggested that you use a Linux like command line terminal emulator like Git Bash.

1. Launch a command-line terminal

2. Ensure that the system **PATH** variable contains the paths where **git**, **node**, **nodemon**, **gulp** and **ng** are located. 
> If you are unable to find an executable with the name **node**, check for **nodejs**

3. Change the directory into the folder that you have designated as the top level folder of the Sunbird application

4. Clone the Sunbird portal github repository using the following command:

    ```
    git clone https://github.com/project-sunbird/sunbird-portal.git
    ```
    
5. Checkout the files tagged with version 1.9 using the following commands:

    ```
    cd sunbird-portal
    git checkout tags/v1.9 -b 1.9
    ```
    
6. Build the nodejs packages that are required by the Sunbird application using the following commands:

    ```
    cd src/app
    npm install
    gulp download:editors
    cd client
    npm install
    ```
    The both the install commands will take a while to complete.

## Configuring the Environment & Services Stack

1. Configure the following system environment variables in the terminal which you have opened

| Environment Variable      |  Value  | Data Type |
|---------------------------|---------|-----------|
|  sunbird_environment      | local   |   string  |
|  sunbird_instance         | sunbird |   string  |
|  sunbird_default_channel  | sunbird |   string  |
|  sunbird_default_tenant   | sunbird |   string  |

> In Linux, the initialization of these environmental variables can take place in a common place like in your **.bashrc** or **.bash_profile**

2. Edit the file **sunbird-portal/src/app/helpers/environmentVariablesHelper.js** and ensure that the following tokens are set to the values indicated. Enclose all string values within double quotation marks.

|            Token            |                   Value                              | Data Type |
|-----------------------------|------------------------------------------------------|-----------|
| CONTENT_CHANNEL_FILTER_TYPE | all                                                  |  string   |
| CONTENT_PROXY_URL           | https://staging.open-sunbird.org                     |  string   |
| CONTENT_URL                 | https://staging.open-sunbird.org/api/                |  string   |
| DEFAULT_CHANNEL             | sunbird                                              |  string   |
| LEARNER_URL                 | https://staging.open-sunbird.org/api/                |  string   |
| PORTAL_API_AUTH_TOKEN       | (The API key you received from your API key request) |  string   |
| PORTAL_AUTH_SERVER_URL      | https://staging.open-sunbird.org/auth                |  string   |
| PORTAL_AUTH_SERVER_CLIENT   | portal                                               |  string   |
| PORTAL_ECHO_API_URL         | (empty string)                                       |  string   |
| PORTAL_PORT                 | 3000                                                 |  number   |
| PORTAL_REALM                | sunbird                                              |  string   |
| TELEMETRY_SERVICE_LOCAL_URL | https://staging.open-sunbird.org/api/data/           |  string   |
| ANDROID_APP_URL             | http://www.sunbird.org                               |  string   |


## Run the Application

1. Update the Sunbird application with the modified configuration file values. Run the following command in the **sunbird-portal/src/app/client** folder:

    ```
    nodemon
    ```
    
2. Wait for the following message before proceeding to the next step 

    ```
    [nodemon] clean exit - waiting for changes before restart
    ```
    
3. Open a new commmand-line window and and populate the following system environment variables once again

  | Environment Variable Name |  Value  | Data Type |
  |---------------------------|---------|-----------|
  |  sunbird_environment      | local   |   string  |
  |  sunbird_instance         | sunbird |   string  |
  |  sunbird_default_channel  | sunbird |   string  |
  |  sunbird_default_tenant   | sunbird |   string  |

4. Run the following commands to change to the application directory and start the server
    
    ```
    cd sunbird-portal/src/app
    node server.js
    ```
   Wait till you see something like this
   
   ```
   Telemetry is initialized.
   app running on port 3000
   ```
    
5. Launch the Google Chrome browser and navigate to

    ```
    http://localhost:3000
    ```

## Login into the Sunbird portal

After successfully installing Sunbird use any of the following user IDs, the password to which you should have recieved along with the API key, to explore Sunbird's workflows. Each user ID corresponds to a specific role.

| User ID                     | Role              |  
|-----------------------------|-------------------|
| adopterorgadmin@adopter     | Org administrator | 
| adoptercreator@adopter      | Content creator   |  
| adopterreviewer@adopter     | Content reviewer  |  
| adopterbookcreator@adopter  | Boook creator     |  
| adopterbookreviewer@adopter | Book reviewer     |  
| adopterflagreviewer@adopter | Flag reviewer     |  
| adoptercoursementor@adopter | Course mentor     |  

* For information on user roles, refer to [Types of Users](features-documentation/user_type)
