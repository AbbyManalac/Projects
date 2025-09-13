<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a Chatbot with Amazon Lex

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-ai-lex1)

**Author:** Abegail Manalac  
**Email:** abby.manalac@gmail.com

---

## Build a Chatbot with Amazon Lex

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-ai-lex1_505be5b8)

---

## Introducing Today's Project!

### What is Amazon Lex?

Amazon Lex is an AWS service that makes it easy to build chatbots by providing built-in natural language understanding, speech recognition, and seamless integration with other AWS services.

### How I used Amazon Lex in this project

The service I used was Amazon Lex. Key concepts I learned include intents, utterances, FallbackIntent, and the confidence score threshold, which helps the bot decide how sure it needs to be before responding.

### One thing I didn't expect was...

One thing I didn't expect in this project was how easy it is to create a chatbot using Amazon Lex, even without any coding experience.

### This project took me...

This project took me approximately 1 hour to complete. The most challenging part was choosing a voice, as they were all fun to explore. The most rewarding part was seeing my bot in action and responding exactly how I intended.

---

## Setting up a Lex chatbot

I created my chatbot from scratch with Amazon Lex. Setting it up took me 5 minutes.

While creating my chatbot, I also set up a role with basic permissions. This is necessary because Amazon Lex needs access to interact with other AWS services like Lambda for processing user requests.

I kept the default intent classification confidence score at 0.40, which means my chatbot must be at least 40% confident in understanding the user's input before responding.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-ai-lex1_97dc2351)

---

## Intents

Intents represent the goal a user wants to accomplish during their conversation with the chatbot.

I created my first intent, WelcomeIntent, to greet users when they say hello or request help, providing a friendly starting point for the conversation.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-ai-lex1_505be5b8)

---

## FallbackIntent

I launched and tested my chatbot, which could respond successfully if I entered "Hiya", and "Hello", and "Help me".

My chatbot returned the message "Intent FallbackIntent is fulfilled" when I entered "How are you" and "Good morning." This happened because the bot couldn't match these inputs to any of the defined intents.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-ai-lex1_505be5b8)

---

## Configuring FallbackIntent

FallbackIntent is a default intent included in every chatbot. It is triggered when the chatbot doesn't recognize or match the user's input to any defined intent.

I configured the FallbackIntent because I want my BankerBot to respond to users in a friendly and helpful manner, even when it doesn’t understand their input or encounters an error.

---

## Variations

To configure the FallbackIntent, I customized the closing response message and added variations to make the chatbot’s replies sound more natural and conversational.

I also added variations to the FallbackIntent. This means end users will see slightly different responses each time the bot doesn’t understand, making the conversation feel more natural and less repetitive.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-ai-lex1_c4fc89af)

---

## Initial Responses

---

---
