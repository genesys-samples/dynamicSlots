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

### Setting up the Dynamic List Slot Variable
1. 
