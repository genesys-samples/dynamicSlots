---
title: "Creating the Data Action"
chapter: false
weight: 10
---

## Creating the Data Action

For the workshop, we can't expect everyone to have access to the same third party system for pulling back our dynamic list, so we've created a mock API for this workshop. This API will pull back a list of transaction history for a fictitious person. You will not specify any inputs, the data action will simply hit the API endpoint and return the same transaction history for each query. 

We will need to import this data action into your instance of Genesys Cloud CX so you can query the transaction history in your instance. Follow the steps below to import the data action: 

1. Navigate to your Genesys Cloud CX Admin console and locate integrations
2. Create a new integration of Web Services Data Actions type
![Web Services Data Actions](/images/webServicesDataActions.jpg)
3. Give the integration a descriptive name. You do not need to worry about configuring credentials for this integration because we are just using a MOCK API that doesn't require credentials
4. Click on the Actions button under Integrations in Genesys Cloud CX Admin
5. Download this JSON file that contains the data action
***Need to figure out how to make a downloadable link to the JSON file***
6. Click Import on the Actions page choose the JSON file you just downloaded. Under integration category, choose the Web Services Data Action integration that we just set up
![Import Data Action](/images/importDataAction.jpg)
7. After importing the data action, navigate to the test tool and click Run Action. You should get this response.
![Data Action Test](/images/dataActionTest.jpg)

You are now ready to call this data action in a Genesys bot flow.