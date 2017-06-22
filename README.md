[![Build Status](https://travis-ci.org/IBM/watson-discovery-news.svg?branch=master)](https://travis-ci.org/IBM/watson-discovery-news)
![Bluemix Deployments](https://deployment-tracker.mybluemix.net/stats/3999122db8b59f04eecad8d229814d83/badge.svg)

# Query Watson Discovery News using the Watson Discovery Service
In this developer journey, we will build a Node.js web application that will use the Watson Discovery Service to access Watson Discovery News. 

Watson Discovery News is a defaullt data collection that is associated with the Watson Discovery Service. It is a dataset of primarily English language news sources that is updated continuously, with approximately 300,000 new articles and blogs added daily.

This journey will demonstrate two use cases for accessing Watson Discovery News:

* **Trending Topics in the News** - Identify popular topics over the past 24 hours. Topics can be general, or for a specific industry or category.

* **Search** - Query for the most relevant new articles about a specific topic or subject. Resullts will include enrichment data, such as article summary text and sentiment analysis.

Optionally included in this journey are examples of how to:

* Build a **RSS News Feed** generator to push Trending Topic news to your favorite RSS reader.

* Build a **SlackBot** to access the Search feature from Slack. 

ARCHITURE PICTURE HERE

* Flow

ADD FLOW STEPS BASED ON ARCHITURE PICTURE

## With Watson

Want to take your Watson app to the next level? Looking to leverage Watson Brand assets? Join the [With Watson](https://www.ibm.com/watson/with-watson) program which provides exclusive brand, marketing, and tech resources to amplify and accelerate your Watson embedded commercial solution.

# Included components

* [Watson Discovery](https://www.ibm.com/watson/developercloud/discovery.html): A cognitive search and content analytics engine for applications to identify patterns, trens, and actionable insights.

# Featured technologies

* [Node.js](https://nodejs.org/en/) - An asynchronous event driven JavaScript runtime, designed to build scalable applications
* [React](https://facebook.github.io/react/) - Javascript library for building User Interfaces
* [Express](https://expressjs.com) - A popular and minimalistic web framework for creating API and Web server
* [Yarn](https://yarnpkg.com) - Fast, reliable and secure dependency manager for node.js
* [RSS](https://en.wikipedia.org/wiki/RSS) - RSS (Rich Site Summary) is a format for delivering regularly changing web content in our case it will be trending topics
* [Slack](https://slack.com) - Slack is a cloud-based set of team collaboration tools and services with chat bot integration
* [Botkit](https://www.botkit.ai) - Framework for creating and managing chat bots

# Watch the Video

* coming soon

# Steps

Use the ``Deploy to Bluemix`` button **OR** create the services and run locally.

## Deploy to Bluemix
[![Deploy to Bluemix](https://deployment-tracker.mybluemix.net/stats/3999122db8b59f04eecad8d229814d83/button.svg)](https://bluemix.net/deploy?repository=https://github.com/IBM/watson-discovery-news.git)

1. Press the above ``Deploy to Bluemix`` button and then click on ``Deploy``.

2. In Toolchains, click on Delivery Pipeline to watch while the app is deployed. Once deployed, the app can be viewed by clicking 'View app'.
![](doc/source/images/toolchain-pipeline.png)

3. To see the app and services created and configured for this journey, use the Bluemix dashboard. The app is named `watson-discovery-news` with a unique suffix. The following services are created:
    * discovery-news-service

## Run locally
> NOTE: These steps are only needed when running locally instead of using the ``Deploy to Bluemix`` button.

1. [Clone the repo](#1-clone-the-repo)
2. [Create Bluemix services](#2-create-bluemix-services)
3. [Configure Watson Discovery](#3-configure-watson-discovery)
4. [Configure Slack](#4-configure-slack)
5. [Run the application](#5-run-the-application)

## 1. Clone the repo

Clone the `watson-discovery-news` locally. In a terminal, run:
```
$ git clone https://github.com/ibm/watson-discovery-news
```

## 2. Create Watson Services with IBM Bluemix

Create the following service:

  * [**Watson Discovery**](https://console.ng.bluemix.net/catalog/services/discovery)

## 3. Configure Watson Discovery

Fill in name you want to give to your service and click *Create*.

![Create Discovery Service Service](https://raw.githubusercontent.com/IBM/watson-discovery-news-trending-topics/master/docs/discovery-1.png)

After the service is created, click on *Service credentials* and then click on *View Credentials*. Save these credentials as they will be needed when configuring the app.

![Discovery Service Credentials](https://raw.githubusercontent.com/IBM/watson-discovery-news-trending-topics/master/docs/discovery-2.png)

## 4. Configure Slack

To integrate a new Slack Bot into your existing Slack team, navigate to https://my.slack.com/services/new/bot. Enter a username for the bot and click **Add bot integration**.

![Create Slackbot](https://raw.githubusercontent.com/IBM/watson-discovery-news-search/master/docs/slack-1.png)

Once created, save the **API Token** that is generated.

![Slackbot Token](https://raw.githubusercontent.com/IBM/watson-discovery-news-search/master/docs/slack-2.png)

## 5. Run the application

### If you used the Deploy to Bluemix button...

If you used ``Deploy to Bluemix``, most of the setup is automatic, but not
quite all of it. We have to update a few environment variables.

In the Bluemix dashboard find the App that was created. Click on ``Runtime`` on the menu and navigate to the ``Environment variables`` tab.

![](doc/source/images/env_vars.png)

Update the following environment variable:

  * Set ``SLACK_BOT_TOKEN`` to the token you saved in Step 4

Save the new value and restart the application, watch the logs for errors.

### If you decided to run the app locally...

1. Install [Node.js](https://nodejs.org/en/) and [Yarn](https://yarnpkg.com)
2. Install all of the dependencies by running `yarn`. This will install of the node modules specified in [`package.json`](package.json)
```
$ yarn
```
3. Run `yarn bootstrap` to copy the `.env.sample` to `.env`
```
$ yarn bootstrap
```
4. Edit the `.env` file and enter the Watson Discovery credentials saved in Step 3, and the Slack Bot Token saved in Step 4.
5. Start the app by running `yarn start`. If you are developing and making changes to the app and would like the server to restart every time then run `yarn start:watch`
```
$ yarn start
```
6. Open a browser and go to `http://localhost:{PORT}`, where PORT is the value specified in `.env` (default is 3000)


# Sample output


Go to the URL that is printed at the end after deployment is done and you can view the app in the browser and copy the RSS link to your favorite RSS Reader. If your RSS Feed Reader supports push notifications you can get alerted when trending topics change along with a news article for that topic.

![RSS feed notification](https://raw.githubusercontent.com/IBM/watson-discovery-news/master/docs/rss-2.png)

![RSS feed notifications](https://raw.githubusercontent.com/IBM/watson-discovery-news/master/docs/rss-1.png)

## RSS Feed Usage

Since RSS feed is a standard way to consume constantly changing data such as news, we can use the RSS feeds we generated to also post news articles to your organizations [slack channel](https://get.slack.help/hc/en-us/articles/218688467-Add-RSS-feeds-to-Slack) to track trends in your industry, or consume the feed to generate a dialy digest of news and email in the morning. Other uses may include automaticaly posting tweets to a twitter account on news articles on trending topics using a service called [IFTTT](https://ifttt.com/connect/feed/twitter).

# Troubleshooting

* Help! I'm seeing errors in my log

This is expected during the first run. The app tries to start before the Discovery
service is fully created. Allow a minute or two to pass, the following message
should appear:

``Watson XXXXXXXXXXX is connected and running!``

* Setting environment variables for a local run

> NOTE: This only needs to be set if the application is running locally.

The credentials for Bluemix services (Discovery), can
be found in the ``Services`` menu in Bluemix, and selecting the ``Service Credentials``
option.

```
# Watson Discovery
DISCOVERY_USERNAME=<add_discovery_username>
DISCOVERY_PASSWORD=<add_discovery_password>

# Slack
SLACK_BOT_TOKEN=<add_slack_bot_token>
```

# License

[Apache 2.0](LICENSE)

# Privacy Notice

If using the Deploy to Bluemix button some metrics are tracked, the following
information is sent to a [Deployment Tracker](https://github.com/IBM-Bluemix/cf-deployment-tracker-service) service
on each deployment:

* Node.js package version
* Node.js repository URL
* Application Name (application_name)
* Application GUID (application_id)
* Application instance index number (instance_index)
* Space ID (space_id)
* Application Version (application_version)
* Application URIs (application_uris)
* Labels of bound services
* Number of instances for each bound service and associated plan information

This data is collected from the setup.py file in the sample application and the ``VCAP_APPLICATION``
and ``VCAP_SERVICES`` environment variables in IBM Bluemix and other Cloud Foundry platforms. This
data is used by IBM to track metrics around deployments of sample applications to IBM Bluemix to
measure the usefulness of our examples, so that we can continuously improve the content we offer
to you. Only deployments of sample applications that include code to ping the Deployment Tracker
service will be tracked.

## Disabling Deployment Tracking

To disable tracking, simply remove ``cf_deployment_tracker.track()`` from the
``index.js`` file in the top level directory.