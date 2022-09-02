---
title: "Creating the Inbound Message Flow"
chapter: false
weight: 30
---

## Creating the Inbound Message Flow

With our bot flow constructed, we will need to configure an inbound message flow that routes customers to this bot flow.

Within architect, change the flow type to "Inbound Message"

![image](/images/messageflowselect.PNG)

Select Add, and provide your flow a name and description. You can also provide an Error Event Transfer queue which will allow for gracefully processing error events and allow interactions to continue to flow to a queue in the event of a logic failure.

![Create Message Flow](/images/messageflowcreate.PNG)

Within this message flow, you can process pre-bot logic, such as data action lookups. For the purpose of this workshop we will simply add a call bot flow logic block.

Within the toolbox, expand "Bot" and drag a "Call Bot Flow" box above the default disconnect block within the flow constructor.

![Call Bot Flow](/images/messageflowbot.PNG)

Within the Call Bot Flow options that open on the right hand side, we can select our Dynamic Slot bot flow that we just constructed. We are also able to define input and output slots.

  * Inputs allow us to send information we've already gathered to a bot flow, for example, if we executed a data action in the Message Flow and found an open case, we could send this case to the bot as an already filled slot. We do not need inputs for this workshop.

  * Outputs allow us to store data that the bot has gathered from the customer to make further routing or agent script decisions. Example; the customer uses the bot to select what they're contacting us about, we can use this information to route to different queues or provide different scripts to the agents. We won't be needing outputs for this example either.

![Call Bot Flow Options](/images/messageflowbotoptions.PNG)

The last item we will add is a transfer to ACD block. This will not be a requirement for this workshop; however, it will allow for testing future enhancements.

Within the toolbox, find "Transfer to ACD" and then drag this underneath the "Call Bot Flow" block and select your queue. You can now publish this Inbound Message Flow.

If you are experienced with Architect, feel free to add any other logic you'd like.

![Transfer to ACD](/images/messageflowacd.PNG)