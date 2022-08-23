---
title: "Building the Genesys Bot Flow"
chapter: false
weight: 20
---

## Building the Genesys Bot Flow
A Genesys Bot Flow is necessary to accomplish our use case of disputing a transaction. The reason that we need a bot flow is so we can communicate back and forth with the customer via an NLU engine about which transaction they believe is fraudulent. Follow these steps to create your bot flow. There is also a video that you can watch of these steps at the end of this section if you prefer that. 

### Creating a Bot Flow

1. Navigate to Genesys Cloud CX Architect and choose Bot Flows from the flows drop down
![Bot Flow](/images/botFlow.jpg)
    - note: if you don't see this, be sure that Genesys Bot Flows are enabled in your org and that you have permissions to view and edit them.
2. Click to create a new bot flow. Give it a descriptive name, and under Template choose Blank Bot Flow
![Create Bot Flow](/images/createBotFlow.jpg)

### Calling the Data Action
1. The first thing we need to do in the bot flow is to drag a Call Data Action block as the start of our flow. 
2. For Category, choose the Web Services Data Actions integration that you set up earlier
3. Under Data Action, choose the data action that we imported earlier 
4. Create variables for both the Success Outputs of transactions.Store and transactions.Value

Now your flow should look like this:
![Data Action Config](/images/dataActionConfig.jpg)

### Setting up the Dynamic List Slot Variable
1. Inside of the bot flow, on the left side, navigate to Slot Types. Click to add a new slot type
2. Give it a descriptive name, such as Transaction List, and then choose Dynamic List as the slot type
![Dynamic List](/images/dynamicList.jpg)
3. Now navigate to Bot Flow Settings
![Bot Flow Settings](/images/botFlowSettings.jpg)

