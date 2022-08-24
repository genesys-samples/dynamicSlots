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
4. In the Bot Flow Settings, under Dynamic Slot Types, add the variable that you created for the stores under the values column.
    - In theory, you could also choose the transaction amount as the variable. In a real world scenario, you'd probably want each transaction to have a unique ID in case of duplicate transactions.
    - We won't have any synonyms in our example
    ![Dynamic Slot Type](/images/dynamicSlotType.jpg)
5. Now navigate to the Slots button under Natural Language Understanding. Click to add a new slot. Give it a descriptive name and choose Existing as the Associated Slot Type. Choose the dynamic list slot type that we just created.
![Create Slot](/images/createSlot.jpg)

### Building the Rest of the Bot Flow
Now we need to make this transaction dispute conversational. We have the data that we need already from our data action and our slot's are all set up. Let's use that to guide our conversation.
1. First, we need to read off the transactions to the customer. To do this, drag a Communicate block under the Success path of the data action. Once you've added this click to configure communication on the right.
![Configure Communication](/images/configureCommunication.jpg)
2. In the Communication Sequence Builder, add some text that says "We are sorry that you feel there has been fraudulent activity on your account. We will read off your most recent transactions and you can tell us which one is fraudulent."
![Add Text](/images/addText.jpg)
3. Now we need to loop through the array of transaction stores and amounts and read them off. To do this, add a Loop Block under that Communicate block. Be sure to give the loop index a variable name and set the Max Loop Count to a variable that counts the number of items in your Transactions.store variable array. This expression will mean the loop will only happen for the amount of stores we have pulled back in that array.
![Loop](/images/loop.jpg)
4. Now drag another Communicate block inside of the loop and click to configure Communication.
![loop Communicate](/images/loopCommunicate.jpg)
5. Now we need to have an expression that uses our loop to the transaction stores and amounts in the array and read them off in sequential order. In the Communication Sequence Builder, toggle to Expression and paste in this expression: 
    - MakeCommunication(
  "$", 
  ToCommunication(GetAt(Flow.transactionValues, Flow.loopIndex)), 
  "at ", 
  ToCommunication(GetAt(Flow.transactionStores, Flow.loopIndex)))

  ![Expression](/images/expression.jpg)
6. Now we can ask the customer to tell us which store they'd like to dispute the transaction with. To do this drag a Ask for Slot block under the Communicate block, but out of the loop. On the right, select the slot that we created earlier. For the question say, "Which store do you want to dispute the transaction with?"
![Ask for Slot](/images/askForSlot.jpg)



