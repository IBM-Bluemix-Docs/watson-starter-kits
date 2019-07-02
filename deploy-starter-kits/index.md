---

copyright:
  years: 2017, 2019
lastupdated: "2019-03-06"

---

{:shortdesc: .shortdesc}
{:new_window: target="_blank"}
{:tip: .tip}
{:pre: .pre}
{:codeblock: .codeblock}
{:screen: .screen}
{:javascript: .ph data-hd-programlang='javascript'}
{:java: .ph data-hd-programlang='java'}
{:python: .ph data-hd-programlang='python'}
{:swift: .ph data-hd-programlang='swift'}

# Deploying Watson starter kits

The following instructions describe how to run [Watson starter kits](https://cloud.ibm.com/developer/watson/starter-kits) locally and deploy them to {{site.data.keyword.cloud_notm}}. 
{: shortdesc}

There might be additional steps required to start your application. View the _README.md_ file in your downloaded starter kit directory for more information.
{: tip}

## Running locally with Docker
{: #run-locally-with-docker}

1. Install the [IBM Cloud developer tools](https://cloud.ibm.com/docs/cli). Docker is included with the installation.

2. Run the Docker application.

3. At the command line, go to your starter kit directory and run the following commands:

    ```sh
    ibmcloud dev build
    ```
    {: pre}
    
    ```sh
    ibmcloud dev run
    ```
    {:pre}

4. Go to http://localhost:3000 in a web browser to view the application.

## Running Node starter kits locally
{: #run-locally-with-node}

1. Install [Node.js](https://nodejs.org) ([LTS](https://github.com/nodejs/Release) supported versions).

1. At the command line, go to your starter kit directory.

1. Install the dependencies:

    ```sh
    npm install
    ```
    {: pre}

1. Start the app:

    ```sh
    npm start
    ```
    {: pre}
    
1. Go to http://localhost:3000 in a web browser to view the application.

## Running Python starter kits locally
{: #run-locally-with-python}

1. Install the prerequisites:
    - [Python](https://www.python.org/) version 2.7 or 3.6
    - [Node.js](https://nodejs.org/en/) ([LTS](https://github.com/nodejs/Release#nodejs-release-working-group) versions)

1. At the command line, go to your starter kit directory.

1. Install the Python dependencies:

    ```sh
    pip install -r requirements.txt
    ```
    {: pre}

1. Install the Node dependencies:

    ```sh
    npm install
    ```
    {: pre}

1. Start the app:

    ```sh
    gunicorn -b localhost:3000 server:app
    ```
    {: pre}
    
1. Go to http://localhost:3000 in a web browser to view the application.


## Deploying to IBM Cloud as a CloudFoundry application
{: #deploy-to-cloud}

1. Install and configure the [IBM Cloud developer tools](https://cloud.ibm.com/docs/cli?topic=cloud-cli-ibmcloud-cli#overview).

2. At the command line, go to your starter kit directory and run the following command to log in to your IBM Cloud account with your IBM Cloud email and password.

    ```bash
    ibmcloud login
    ```
    {: pre}

3. Target a Cloud Foundry organization and space.

    ```
    ibmcloud target --cf
    ```
    {: pre}

4. Push the app to IBM Cloud.

    ```bash
    ibmcloud dev deploy
    ```
    {: pre}
    
    The app will be deployed using the settings in your project's `manifest.yml` file.

5. Access your app at the URL specified in the command output.

    After your app is deployed, you can manage it from your [IBM Cloud resources](https://cloud.ibm.com/resources).
