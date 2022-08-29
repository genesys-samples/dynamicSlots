---
title: "Creating the Inbound Message Flow"
chapter: false
weight: 30
---

## Creating the Inbound Message Flow

With our bot flow constructed, we will need to configure an inbound message flow to reference, or navigate to this bot.

Within architect, change the flow type to "Inbound Message"

![Select Message Flow](/images/messageflowselect.jpg)

Select Add, and provide your flow a name and description. You can also provide an Error Event Transfer queue which will allow for gracefully processing error events and allow interactions to continue to flow to a queue in the event of a logic failure.

![Create Message Flow](/images/messageflowcreate.jpg)

Within this message flow, you can process pre-bot logic, such as data action lookups. For the purpose of this workshop we will simply add a call bot flow logic block.

Within the toolbox, expand "Bot" and drag a "Call Bot Flow" box above the default disconnect block within the flow constructor.

![Call Bot Flow](/images/messageflowbot.jpg)

Within the Call Bot Flow options, we can select our Dynamic Slot bot flow. We are also able to define input and output parameters.

  * Inputs allow us to send information we've already gathered to a bot flow, for example, if we executed a data action in the Message Flow and found an open case, we could send this case to the bot as an already filled slot. We do not need inputs for this workshop

  * Outputs allow us to store data that the bot has gathered from the customer to make further routing or agent script decisions. Example; the customer uses the bot to select what they're contacting us about, we can use this information to route to different queues or provide different scripts to the agents.

![Call Bot Flow Options](/images/messageflowbotoptions.jpg)

The last item we will add is a transfer to ACD, this will not be a requirement for this workshop however it will allow for testing future enhancements.

Within the toolbox, find "Transfer to ACD", drag this underneath the "Call Bot Flow" block and select your queue. You can now publish this Inbound Message Flow.

![Transfer to ACD](/images/messageflowacd.jpg)