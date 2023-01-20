---
title: "Build Transaction Dispute Use Case"
chapter: true
weight: 30
---

## Build Transaction Dispute Use Case

Now the time has come to build a bot flow using a dynamic list slot. Because we can't expect everyone to have access to the same external platform to pull an array of data, we've created a mock API that will help accomplish our use case. 

The use case that we will build out today is going to be for disputing a transaction at a bank. Think back to the 3 slots types we covered in the introduction: list, dynamic list, and regular expression. Your most recent transactions are certainly a list, but they are dynamic because they are different for each person and frequently you are adding new transactions to the list (some people more than others). So this is an opportunity to use a Dynamic List Slot type that pulls the most recent transactions through an API call and use that dynamic list as the list for the slot type. 

We'll break this down into 5 steps: 

1. Creating the data action
2. Building the Genesys Bot Flow - *this is the focus of our workshop* 
3. Creating the inbound message flow
4. Creating the Web Messenger Configuration and Deployment for Testing
5. Testing