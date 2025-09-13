<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Set Up Multiple Slots in a Lex Chatbot

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-ai-lex5)

**Author:** Abegail Manalac  
**Email:** abby.manalac@gmail.com

---

## Build a Chatbot with Multiple Slots

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-ai-lex5_67890123)

---

## Introducing Today's Project!

### What is Amazon Lex?

Amazon Lex is a service that helps you build chatbots using voice and text. It’s useful because it understands natural language, making it easy to create conversational interfaces that improve user experience and automate common tasks.

### How I used Amazon Lex in this project

In today's project, I used Amazon Lex to create BankerBot, a chatbot that acts like a virtual banker-helping users transfer funds, check balances, and interact through natural language conversations.


### One thing I didn't expect in this project was...

One thing I didn't expect in this project was running into permission issues with the Lambda function after deployment- it was a bit tricky to troubleshoot, but it helped me understand how important IAM settings are in chatbot integrations.

### This project took me...

This project took me around two hours to complete, including setup, troubleshooting errors, and testing the chatbot. It was a great hands-on experience that helped me understand how different AWS services work together.

---

## TransferFunds

An intent I created for my chatbot was TransferFunds, which allow users to transfer their preferred amount from one account to another. 

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-ai-lex5_67890123)

---

## Using multiple slots

For this intent, I had to use the same slot type twice because the user needs to specify both the source and destination accounts, and both use the same slot type-accountType- to identify the type of account involved in the transfer.


I also learnt how to create confirmation prompts, which are messages that seek the user's consent before an intent is fulfilled, which in this case is the transfer of money from one account to the other.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-ai-lex5_97dc2351)

---

## Exploring Lex features

Lex also has a special conversation flow feature that visually maps out how a conversation progresses between the user and the bot, making it easier to design, understand, and troubleshoot the chatbot’s logic and interactions.

You could also set up your intent using a visual builder! A visual builder simplifies chatbot development by letting you drag and drop elements, configure prompts, and manage slots in a visual interface—no coding required.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-ai-lex5_12345678)

---

## AWS CloudFormation

AWS CloudFormation is a service that lets you define and provision AWS resources using code. It allows you to create, update, or delete a full set of resources from a single template, making deployment faster, more consistent, and easier to manage.

I used CloudFormation to quickly deploy all the necessary resources for BankerBot using a single template, saving time and ensuring everything was set up consistently without manual configuration.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-ai-lex5_c4fc89af)

---

## The final result!

Re-building my bot with CloudFormation took me just a few minutes, thanks to the automated setup provided by the template- it was much faster and more efficient than doing it manually.

There was an error after deployment- the Lambda function didn’t return values to the bot due to permission issues. I fixed it by creating a new function, adding the correct code, and updating the alias to connect to the new Lambda.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-ai-lex5_505be5b8)

---

## Using the visual builder

---

---
