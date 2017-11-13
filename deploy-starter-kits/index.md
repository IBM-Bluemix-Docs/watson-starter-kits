---

copyright:
  years: 2017
lastupdated: "2017-11-13"

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


## Before you begin
{: #before-you-begin}

- [Sign up](https://bluemix.net/registration/) for {{site.data.keyword.Bluemix_notm}}, or log into an existing account. Your account must have available space for at least one app and one service.
- To host the application on {{site.data.keyword.Bluemix_notm}}, install the [{{site.data.keyword.Bluemix_notm}} CLI](https://console.bluemix.net/docs/cli/reference/bluemix_cli/index.html#install_bluemix_cli).


## Deploying your Watson app locally
{: #run-locally}


### Node App
{: #run-node-apps}
The following steps are for running locally with Node.js.

1. To develop locally, first install [Node.js](https://nodejs.org) ([LTS](https://github.com/nodejs/Release) supported versions).

1. At the command line, go to your project directory.

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

### Python App
{: #run-python-apps}
The following instructions are for running locally with Python.

1. Install the prerequisites:
    - [Python](https://www.python.org/) version 2.7 or 3.6
    - [Node.js](https://nodejs.org/en/) ([LTS](https://github.com/nodejs/Release#nodejs-release-working-group) versions)

1. At the command line, go to your application directory.

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
