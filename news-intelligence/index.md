---

copyright:
  years: 2017
lastupdated: "2017-06-29"

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

# Getting Started with the Watson News Intelligence starter kit

The Watson News Intelligence starter kit for Node.js visualizes the results of [{{site.data.keyword.discoveryshort}}](http://www.ibm.com/watson/developercloud/discovery.html) queries. The app searches [Discovery News](https://www.ibm.com/watson/developercloud/discovery-news.html) data to get insights from the news, including related concepts, entities, and sentiment trends.
{: shortdesc}

## Before you begin
{: #before-you-begin}

- [Sign up](https://bluemix.net/registration/) for {{site.data.keyword.Bluemix_notm}}, or log into an existing account. Your account must have available space for at least one app and one service.
- To develop locally, install [Node.js](https://nodejs.org) (version 4 or later).
- To host the application on {{site.data.keyword.Bluemix_notm}}, install the [{{site.data.keyword.Bluemix_notm}} CLI](https://console.bluemix.net/docs/cli/reference/bluemix_cli/index.html#install_bluemix_cli).

## Generating and downloading the code
{: #generate-and-download}

1. Create or select your starter kit project:
    - If you haven't created a News Intelligence project in the {{site.data.keyword.watson}} {{site.data.keyword.dev_console}}, go to the [News Intelligence](https://console.{DomainName}/watson/create-project?starterKit=newsIntelligence&service=discovery) starter kit page and click **Create**.

    or

    - Select your News Intelligence project from the [Projects](https://console.bluemix.net/watson/projects) page of the {{site.data.keyword.dev_console}}.
1. Scroll down to the "Code" section and click **Get Code**, which generates configuration files for your application.
1. Click **Download Code** to download a .zip file of your generated app.
1. Extract the .zip file.

## Running the application locally
{: #run-locally}

1. At the command line, go to your application directory.
1. Install the dependencies:

    ```bash
    npm install
    ```
    {: pre}

1. Start the app:

    ```bash
    npm start
    ```
    {: pre}
    
1. Go to http://localhost:8080 in a web browser to view the application.

### Testing the application
{: #test-the-application}

Enter a company name in the search bar to query Watson Discovery News through the app. Each panel on the page contains a visual presentation of insights derived from the API response. Press **View Query** in each panel to view the parameters of the API request and the response in JSON form.

## Deploying to Bluemix
{: #deploy-to-bluemix}

Your application includes `manifest.yml` and `credentials.json` files with the host settings and service credentials already set, so you can quickly deploy to {{site.data.keyword.Bluemix_notm}}.

1. Open a terminal, go to your application folder, and log in to {{site.data.keyword.Bluemix_notm}} through the  {{site.data.keyword.Bluemix_notm}} CLI. For details about what to specify in the API field, go to the [How Bluemix Cloud Foundry works](https://console.{DomainName}/docs/overview/cf.html#ov_intro_reg) docs, and view the "Regions" section to locate the corresponding API endpoint for your region.

    ```bash
    bluemix login
    ```
    {: pre}

1. Push the app to {{site.data.keyword.Bluemix_notm}} with the settings in your `manifest.yml` file:

    ```bash
    bluemix app push
    ```
    {: pre}

1. Access your app at the URL specified in the command output.

    After your app is deployed, you can manage it from your [Bluemix dashboard](https://console.bluemix.net/dashboard/apps).

## Next Steps
{: #next-steps}

- Check out the {{site.data.keyword.discoveryshort}} [API reference ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/discovery/api/v1/){: new_window}
- Read the {{site.data.keyword.discoveryshort}} [docs ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/doc/discovery/index.html){: new_window}
