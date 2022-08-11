---
title: "Introduction"
chapter: true
weight: 10
---

### Genesys Dialog Engine Bot Flows Terminology Refresher

Before we define Dynamic List slots, let's get a refresher on the terminology for Genesys Dialog Engine Bot Flows. Then we will be able to tie in how dynamic slots fits into the picture. 

Here are some of the key terms to know with Genesys Dialog Engine Bot Flows: 

- Intents - Intents describe a goal or task that the users wants to accomplish. For example, "Book a Room" or "Check Account Balance"
- Utterances - Utterances are phrases that users use to describe what they want to do. Utterances are mapped to intents so when an utterance is spoken, it fires off the corresponding itent. For example, if the intent is "Book a Room" an utterance might be "I'd like to reserve a room for tonight"
- Slots - Slots are pieces of information that can be used to help fulfill the intent. In the example of "I'd like to reserve a room for tonight", the word "tonight" is fulfilling a key piece of information; the date of the stay. The date of the stay is a slot. We might follow up asking for another slot; gathering the type of room they need for their stay. 
- Slot Types - A slot type defines how the bot processes the information available in the identified slot. Each slot must be mapped to a slot type. In the example above for gathering the date of the stay, a slot type can help define that we are only accepting values from the customer that are a date. So if the bot asked the customer which date they want to stay, the customer can't say "pizza" because the slot type won't accept anything other than a date.

Slots and slot types are ultimately the focus of todays workshop, so let's dive a bit deeper: 

### Slot & Slot Types
There are three different types of Slot Types that you can create:

- Regular Expression - Regular Expression is used for identifying patterns within utterances that match to a specific sequence of characters. Commonly known as REGEX, this is a widely used method. To give an example of using a REGEX slot type, think of account numbers. If you only want to accept a sequence of numbers that are 10-12 digits long, for example, you can have a REGEX expression that only allows that sequence of characters.
- List - This is the most easy to understand because it is exactly as it sounds. Think of our example above about the type of room that someone could book at a hotel. The hotel probably only offers around 4-8 types of rooms so this is a perfect example of using a List slot type. You also can include synonyms to the words in your list. 
- Dynamic List - While these are similar to lists, Dynamic Lists are helpful if your bot contains many values for a slot type and you don't want to manually add them and manually update them as your list changes. They are also helpful when the values of the list are not known at the time of designing the bot or if the list is specific to each individual customer. 

To give you some use cases of what we just described for Dynamic Lists slots, move on to the next section. 