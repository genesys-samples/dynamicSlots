---
title: "Testing"
chapter: false
weight: 50
---

## Testing What We've Built
Now that we've created everything, now we can test to ensure there's nothing that needs fixed. Follow along to test: 

1. Navigate to the Genesys Cloud Developer Center Web Messaging Tools page https://developer.genesys.cloud/devapps/web-chat-messenger
2. Be sure to login to your account in the top right
3. Choose your web messenger deployment from the drop down, and then press Start Chat
4. Click on the web messenger icon that renders in the box
![Messenger Icon](/images/messengerIcon.jpg)
5. Upon clicking the icon and saying 'Hello', the dispute bot will kick into action and read off the transactions and then provide you the option on what store to dispute the transaction with
![Testing](/images/testing.jpg)
6. After selecting an option, our flow is configured to route to a queue. In a real world scenario, the bot could process everything behind the scenes without the need for human intervention. 
7. If you wish to view the agent leg of the transaction, be sure your user is a member of the queue that the Inbound Message flow is routing to. Then turn your user on queue to accept the interaction. For more information about queue setup and handling inbound message interactions, check out our Genesys Cloud CX™️ Channel Setup workshop: https://workshop.genesys.com/workshops/gride-demo/. 

Congrats! If this worked for you, you've successfully completed the workshop. 