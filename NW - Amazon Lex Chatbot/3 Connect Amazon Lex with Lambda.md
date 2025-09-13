<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Connect Amazon Lex with Lambda

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-ai-lex3)

**Author:** Abegail Manalac  
**Email:** abby.manalac@gmail.com

---

## Connect Amazon Lex with Lambda

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-ai-lex3_505be5b8)

---

## Introducing Today's Project!

### What is Amazon Lex?

Amazon Lex is a service for building chatbots that understand natural language. It’s useful because it provides built-in NLP and speech recognition, making it easy to create smart, conversational bots without needing advanced AI skills.

### How I used Amazon Lex in this project

In today’s project, I used Amazon Lex to build a chatbot called BankerBot that collects user details, understands banking intents like checking account balances, and connects with AWS Lambda to return dynamic responses.

### One thing I didn't expect in this project was...

One thing I didn’t expect in this project was how creative and personalized I could make the chatbot responses, especially by customizing messages through Lambda to make the user experience more fun and engaging.

### This project took me...

This project took me about 1 hour to complete, including building the chatbot, connecting it to Lambda, customizing responses, and testing the full interaction flow.

---

## AWS Lambda Functions

AWS Lambda is a service that lets you run code in the cloud without managing any servers—Lambda handles that for you. It runs your code only when needed and automatically scales, whether it’s a few requests a day or thousands per second.

In this project, I created a Lambda function to generate and return a random bank balance when a user asks, allowing my chatbot to simulate a real banking response.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-ai-lex3_97dc2351)

---

## Chatbot Alias

An alias in Amazon Lex points to a specific bot version. It lets apps connect through the alias, so when you update the bot, you just update the alias—no need to change the apps. This saves time and reduces the risk of errors.

TestBotAlias is the default version of your bot used for testing and development. It’s a safe space to try out changes and make sure everything works before going live.

I connected my bot with Lambda using TestBotAlias by selecting my Lambda function, BankingBotEnglish, in the Lambda function panel that appeared. I left the version/alias field set to the default $LATEST to use the most recent code.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-ai-lex3_c4fc89af)

---

## Code Hooks

A code hook connects your chatbot to a custom Lambda function to handle tasks the basic bot can’t do—like checking a database or making decisions. It makes the chatbot smarter by running custom logic during the conversation.

Even though I connected my Lambda function to my chatbot's alias, I used code hooks so the bot could run custom logic, like verifying inputs or generating a bank balance—tasks that go beyond what the basic bot setup can handle.

I could find code hooks in the CheckBalance intent settings. Under the Fulfillment section, I enabled the Lambda function code hook so the bot could trigger my Lambda function when all required slot values are collected.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-ai-lex3_505be5b9)

---

## The final result!

My chatbot will return a bank balance figure once the user provides their account type and date of birth for verification. At that point, it triggers the Lambda function to generate and return a random balance.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-ai-lex3_505be5b8)

---

## Customizing the Lambda function

---

---
