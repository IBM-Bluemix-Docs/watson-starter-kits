---

copyright:
  years: 2017
lastupdated: "2017-11-15"

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

The following instructions describe how to run [Watson starter kits](https://console.bluemix.net/developer/watson/starter-kits) locally and deploy them to {{site.data.keyword.Bluemix_notm}}. 
{: shortdesc}

There might be additional steps required to start your application. View the `README.md` file in your downloaded starter kit directory for more information.
{: tip}

## Running locally with Docker
{: #run-locally-with-docker}

1. Install and run [Docker](https://www.docker.com).

1. Install the [IBM Cloud Developer Tools CLI](https://console.bluemix.net/docs/cloudnative/dev_cli.html#add-cli).

1. At the command line, go to your starter kit directory and run the following commands:

    ```sh
    bx dev build
    ```
    {: pre}
    
    ```sh
    bx dev run
    ```
    {:pre}

1. Go to http://localhost:3000 in a web browser to view the application.

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

1. Install the [Bluemix CLI](https://console.bluemix.net/docs/cli/reference/bluemix_cli/get_started.html#getting-started). Open a terminal and run the command that corresponds with your operating system:

    - MacOS

        ```sh
        sh <(curl -fsSL https://clis.ng.bluemix.net/install/osx)
        ```
        {: pre}

    - Linux

        ```sh
        sh <(curl -fsSL https://clis.ng.bluemix.net/install/linux)
        ```
        {: pre}

    - Windows Powershell

        Copy and paste the following command into a Windows PowerShell terminal console and execute it.
        ```sh
        iex(New-Object Net.WebClient).DownloadString('https://clis.ng.bluemix.net/install/powershell')
        ```
        {: pre}

1. Set your API endpoint. In the menu bar on the top of your [IBM Cloud dashboard](https://console.bluemix.net/dashboard), find the IBM Cloud region that you are using, then run the corresponding command to set your API endpoint.

    - US South:

        ```sh
        bx api https://api.ng.bluemix.net
        ```
        {: pre}

    - Germany:

        ```sh
        bx api https://api.eu-de.bluemix.net
        ```
        {: pre}

    - Sydney:

        ```sh
        bx api https://api.au-syd.bluemix.net
        ```
        {: pre}

    - United Kingdom:

        ```sh
        bx api https://api.eu-gb.bluemix.net
        ```
        {: pre}

1. At the command line, go to your starter kit directory and run the following command to log in to your IBM Cloud account with your IBMid.

    ```bash
    bx login
    ```
    {: pre}

1. Push the app to IBM Cloud:

    ```bash
    bx app push
    ```
    {: pre}
    
    The app will be deployed using the settings in your project's `manifest.yml` file.

1. Access your app at the URL specified in the command output.

    After your app is deployed, you can manage it from your [IBM Cloud dashboard](https://console.bluemix.net/dashboard/apps).
