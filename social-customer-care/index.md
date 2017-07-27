---

copyright:
  years: 2017
lastupdated: "2017-07-26"

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

# Getting started with the Watson Social Customer Care starter kit

The Watson Social Customer Care starter kit demonstrates how to use [Natural Language Classifier](https://www.ibm.com/watson/services/natural-language-classifier/) to route customer requests and queries to the appropriate agent or workflow. Additionally, it shows how to use [Natural Language Understanding](https://www.ibm.com/watson/services/natural-language-understanding/) and [Personality Insights](https://www.ibm.com/watson/services/personality-insights/) to provide an agent with customer insights.
{: shortdesc}

## Before you begin
{: #before-you-begin}

1. [Sign up for IBM Bluemix](https://console.bluemix.net/registration/).
1. Install local development prerequisites:
    - [Node.js](https://nodejs.org) (version 4 or later)
1. Install prerequisites for hosting your application on IBM Bluemix:
    - [Bluemix CLI](https://console.bluemix.net/docs/cli/reference/bluemix_cli/index.html#install_bluemix_cli)

## Generating and downloading the code
{: #generate-and-download}

1. Create or select your starter kit project:

    - If you haven't created a Social Customer Care project in the {{site.data.keyword.watson}} {{site.data.keyword.dev_console}}, go to the [Social Customer Care](https://console.{DomainName}/watson/create-project?starterKit=socialCustomerCare&service=naturalLanguageClassifier&service=personalityInsights&service=naturalLanguageUnderstanding) starter kit page and clck **Create**.

    or

    - Select your Social Customer Care project from the [Projects](https://console.bluemix.net/watson/projects) page of the {{site.data.keyword.dev_console}}.

1. Scroll down to the "Code" section and click **Get Code**, which generates configuration files for your application.

1. Click **Download Code** to download a .zip file of your generated app.

1. Extract the .zip file.

## Training your Natural Language Classifier instance
{: #train-natural-language-classifier}

Before you run locally or deploy to Bluemix, you need to train Natural Language Classifier with the training data in the *training/classifier-training-data.csv* file. The *train-classifier.js* script does this for you.

1. At the command line, go to your application directory.

1. Install the dependencies.

    ```bash
    npm install
    ```
    {: pre}

1. Run the training script.

    ```bash
    npm run train
    ```
    {: pre}

## Connecting the application to Twitter
{: #connect-to-twitter}

1. Go to [Twitter](http://apps.twitter.com) and sign up for application development credentials. Create a new application with the `Create new app` button and fill out the required form. Click on the **Keys and Access Tokens** tab to view your credentials.

1. Click on **Create my access token**.

1. Update the *env.properties* file with the credentials for your Twitter application.

    ```bash
    TWITTER_CONSUMER_KEY=REPLACE WITH YOUR CONSUMER KEY
    TWITTER_CONSUMER_SECRET=REPLACE WITH YOUR CONSUMER SECRET
    TWITTER_ACCESS_TOKEN_KEY=REPLACE WITH YOUR ACCESS TOKEN KEY
    TWITTER_ACCESS_TOKEN_SECRET=REPLACE WITH YOUR ACCESS TOKEN SECRET
    ```
    {: pre}

## Running the application locally
{: #run-locally}

After you train the application, you're ready to run it locally.

1. Start the app from your application directory.

    ```bash
    npm run build
    ```
    {: pre}

    ```bash
    npm start
    ```
    {: pre}

1. Go to http://localhost:8080 in a web browser to view the application.

## Testing the application
{: #test-the-application}

The application reports a live stream of tweets sent to Twitter's [@TwitterSupport account](https://twitter.com/twittersupport). The responses from the mock WatsonSupport bot are displayed next to each user tweet. Natural Language Classifier analyzes each tweet from the stream to determine the user's intent, and the application uses the corresponding message from the *data/default-responses.json* file to create the response.

### Filter interactions

On the left side of the application, you can filter interactions by customer sentiment and support topics that were identified by the WatsonSupport bot. The support topics correspond with the intents reported by Natural Language Classifier.

### Get user insights

Click on a user tweet to view details about their Twitter profile and personality information on the left side of the app. An emoticon in the top right corner of each user tweet indicates the sentiment of the tweet as determined by results from Natural Language Understanding's sentiment feature.

**Note**: For the purposes of this starter kit, random bodies of text are substituted for the customer's past tweets. This is done to avoid the issues involved with retrieving past tweets at scale. For your application, past tweets can be retrieved with the [IBM Insights for Twitter](https://console.ng.bluemix.net/docs/services/Twitter/index.html#twitter) service available on Bluemix.

## Deploying to Bluemix
{: #deploy-to-bluemix}

Your application includes *manifest.yml* and *credentials.json* files with the host settings and service credentials already set, so you can quickly deploy to {{site.data.keyword.Bluemix_notm}}.

1. Open a terminal, go to your application folder, and log in to {{site.data.keyword.Bluemix_notm}} through the {{site.data.keyword.Bluemix_notm}} CLI. For details about what to specify in the API field, go to the [How Bluemix Cloud Foundry works](https://console.{DomainName}/docs/overview/cf.html#ov_intro_reg) docs, and view the "Regions" section to locate the corresponding API endpoint for your region.

    ```bash
    bluemix login
    ```
    {: pre}

1. Push the app to {{site.data.keyword.Bluemix_notm}} with the settings in your *manifest.yml* file:

    ```bash
    bluemix app push
    ```
    {: pre}

1. Access your app at the URL specified in the command output.

After your app is deployed, you can manage it from your [Bluemix dashboard](https://console.bluemix.net/dashboard/apps).

## Adapting/extending the starter kit
{: #adapting-the-starter-kit}

This Starter Kit works off of Twitter data. However, the concepts used here are platform independent and can be applied wherever you do customer support. This includes email, SMS, Facebook, and chat/messaging apps.

The following are a basic set of instructions for how to adapt the Starter Kit to your own use case.

1. The Twitter feed can be changed by modifying the `TWITTER_TOPIC` variable in the *env.properties* file.
1. The Natural Language Classifier Service needs a new ground truth for your new feed. The best approach is to collect real user tweets. An easy solution is to use the [IBM Insights for Twitter](https://console.bluemix.net/docs/#services/Twitter/index.html) service available on Bluemix. Using this service, you can retrieve historical tweets from the Twitter Decahose (a 10% random sample of Tweets). Another alternative is to modify the starter kit to save incoming tweets and run the application locally. The number of tweets required will depend upon the complexity of the feed. In most cases, around 300 tweets is enough to receive respectable performance for a proof of concept, demo, or testing.
1. Create the ground truth for the Natural Language Classifier by classifying the tweets that you collected in the previous step.
    1. Edit the *training/classifier-training-data.csv* file so it includes new examples (column A) and intents (column B).
    1. Run the `npm run train` command to rerun the training script. This creates a new classifier, and changes the `CLASSIFIER_ID` variable in the *env.properties* file communicate with it. *Creating additional classifiers and running training events may increase your service bill. Check the [Natural Language Classifier page in Bluemix](https://console.bluemix.net/catalog/services/natural-language-classifier) for pricing details*.
1. Decide how the application will respond for each intent. The approach taken by the Starter Kit is to provide a FAQ style response or to delegate the customer to an appropriate agent. Responses can be customized by altering the *data/default-responses.json* file. Be sure to include an entry for each intent in your classifier ground truth.
1. Use the Personality Insights profile to drive your customer engagement strategy. The Starter Kit simply displays a few highlights from the customer's personality but much more is possible. Some examples of how to apply the service can be found in the Personality Insights [documentation](https://www.ibm.com/watson/developercloud/doc/personality-insights/basics.shtml#overviewApply).

## Next steps
{: #next-steps}

Learn more about the following Watson services that were used to create this starter kit.

### Natural Language Understanding
- [Demo](https://natural-language-understanding-demo.mybluemix.net/)
- [Documentation](https://www.ibm.com/watson/developercloud/doc/natural-language-understanding)
- [API Reference](https://www.ibm.com/watson/developercloud/natural-language-understanding/api/v1)

### Natural Language Classifier
- [Demo](https://natural-language-classifier-demo.mybluemix.net/)
- [Documentation](https://console.bluemix.net/docs/services/natural-language-classifier/natural-language-classifier-overview.html#about)
- [API Reference](https://www.ibm.com/watson/developercloud/natural-language-classifier/api/v1/)

### Personality Insights
- [Demo](https://personality-insights-livedemo.mybluemix.net/)
- [Documentation](https://www.ibm.com/watson/developercloud/doc/personality-insights)
- [API Reference](https://www.ibm.com/watson/developercloud/personality-insights/api/v2)


