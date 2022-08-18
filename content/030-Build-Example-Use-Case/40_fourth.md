---
title: "Creating the Web Messenger Configuration and Deployment for Testing"
chapter: false
weight: 40
---

## Creating the Web Messenger Configuration and Deployment for Testing

With the Bot and Message flow created, we're ready to create a messenger configuration and deployment.

### Web Messenger Configuration
The web messenger configuration is where we will define visibility, appearance and other various configuration elements for how the messenger will behave.

Within the main Genesys Cloud application, navigate to Admin > Messenger Configurations and create new.

While there are many configuration elements, for this workshop we will only provide a name and select our default language (by scrolling to the bottom of the appearance tab), as seen below - 

![Call Bot Flow](/images/Messageconfigname.jpg)

![Call Bot Flow](/images/Messageconfiglanguage.jpg)

For an explanation of the additional configuration options, you can review this resource center article - https://help.mypurecloud.com/articles/configure-messenger/

You can now Save new version.

### Web Messenger Deployment

Within the main Genesys Cloud application, navigate to Admin > Messenger Deployments and create new.

The deployment is where we will tie together our messenger configuration to our message flow (and ultimately, our bot flow).

1. Name your Configuration
2. Enable the messenger status
3. Select your configuration (you will search for the web messenger configuration we just created)
4. Allow on all domains (this will simplify testing)
5. Select your inbound message architect flow

After configuring these options your deployment should look as such - 

![Message Deployment](/images/messagedeployment.jpg)