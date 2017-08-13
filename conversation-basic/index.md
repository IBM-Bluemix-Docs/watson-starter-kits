---

copyright:
  years: 2017
lastupdated: "2017-08-11"

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

# Getting Started with the Conversation Basic starter kit

The Conversation Basic starter kit for Node.js visualizes the results of [{{site.data.keyword.conversationshort}}](http://www.ibm.com/watson/developercloud/conversation.html) queries. 
{: shortdesc}

## Before you begin
{: #before-you-begin}

- [Sign up](https://bluemix.net/registration/) for {{site.data.keyword.Bluemix_notm}}, or log into an existing account. Your account must have available space for at least one app and one service.
- To develop locally, install [Node.js](https://nodejs.org) (version 4 or later).
- To host the application on {{site.data.keyword.Bluemix_notm}}, install the [{{site.data.keyword.Bluemix_notm}} CLI](https://console.bluemix.net/docs/cli/reference/bluemix_cli/index.html#install_bluemix_cli).

## Generating and downloading the code
{: #generate-and-download}

1. Create or select your starter kit project:
    - If you haven't created a Conversation Basic project in the {{site.data.keyword.watson}} {{site.data.keyword.dev_console}}, go to the [Conversation Basic](https://console.{DomainName}/developer/watson/create-project?starterKit=45fe1f9a-5d31-36c6-9ad1-3affa9b49d49&service=conversation) starter kit page and click **Create**.

    or

    - Select your Conversation Basic project from the [Projects](https://console.bluemix.net/developer/watson/projects) page of the {{site.data.keyword.dev_console}}.
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

After your app is installed and running, experiment with it to see how it responds.

The chat interface is on the left, and the JSON that the JavaScript code receives from the Conversation service is on the right. Your questions and commands are interpreted using a small set of sample data trained with the following intents:

    turn_on
    turn_off
    turn_up
    turn_down
    traffic_update
    locate_amenity
    weather
    phone
    capabilities
    greetings
    goodbyes

Type a request, such as `music on` or `I want to turn on the windshield wipers`. The system understands your intent and responds. You can see the details of how your input was understood by examining the JSON data in the `Watson understands` section on the right side.

For example, if you type `Turn on some music`, the JSON data shows that the system understood the `turn_on` intent with a high level of confidence, along with the `appliance` entity with a value of `music`.

For more information about intents, see the [Conversation service documentation](http://www.ibm.com/watson/developercloud/conversation.html).

To see details of how these intents are defined, including sample input for each intent, launch the Conversation tool.

## Deploying to Bluemix
{: #deploy-to-bluemix}

Your application includes `manifest.yml` and `./server/localdev-config.json` files with the host settings and service credentials already set, so you can quickly deploy to {{site.data.keyword.Bluemix_notm}}.

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

- Check out the {{site.data.keyword.conversationshort}} [API reference ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/conversation/api/v1/){: new_window}
- Read the {{site.data.keyword.conversationshort}} [docs ![External link icon](../../icons/launch-glyph.svg "External link icon")](https://www.ibm.com/watson/developercloud/doc/conversation/index.html){: new_window}