---
title: "Use Cases for Dynamic List Slots"
chapter: true
weight: 10
---

## Use Cases

Dynamic slots truly open the doors to full automation within a bot. Historically, an administrator would have to modify what slots a bot captures when their organization's offerings or services change. Dynamic Slots allow the bot to construct its list of slots on a per interaction basis from an internal or external data source. This means that a customer can always be interacting with the most up to date data, and administrators aren't manually constructing it. Here are a few examples of use cases: 

**Use Case 1:** An insurance company expands their offerings to include additional insurance types and packages. Instead of an administrator adding these additional items into the slot list, the API that is pulling the current services will automatically see the new offerrings and capture those as accepted slots within the bot flow.

**Use Case 2:** A customer is using a self service menu to order a pizza however the pizza company has run out of a specific topping. Typically this would result in a call back to the customer to inform them that it's not available, however dynamic slots would allow the bot to no longer recognize that as an accepted slot and could recommend something else instead.

**Use Case 3:** A customer is reaching out to a bank to dispute a charge on their account. Dynamic slots allows the bot to pull down all recent transactions and recognize them as referenceable slots. The bot can read the various transactions back to the customer and allow them to say which transaction they believe is fraud. To create this without dynamic slots an administrator would have to build a complex flow to iterate through customer transactions and allow the customer to action off of them.

For this workshop, we are going to build out Use Case 3 in your own environment.