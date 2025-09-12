<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Add Custom Slots to a Lex Chatbot

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-ai-lex2)

**Author:** Abegail Manalac  
**Email:** abby.manalac@gmail.com

---

## Add Custom Slots to a Lex Chatbot

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-ai-lex2_c4fc89af)

---

## Introducing Today's Project!

In today's project, I used Amazon Lex to create a chatbot called BankerBot that collects user details to handle banking-related intents, such as checking account balances.

### What is Amazon Lex?

Amazon Lex is a chatbot service that uses natural human language to help users interact with the bot. It’s useful for creating friendly, conversational experiences and automating support flows efficiently.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was how creative and fun it can be to design the different ways a chatbot interacts with users, making the experience more engaging and personalized.

### This project took me...

This project took me about 1 hour to complete, including creating the chatbot from scratch and finishing the documentation for all the steps involved.

---

## Slots

A slot is a piece of information that a chatbot needs to complete a user's request—like filling in blanks on a form. For example, booking a table might require the date, time, and number of people. Amazon Lex offers built-in and custom slot types.

By adding custom slots in utterances, my chatbot's users can provide inputs like "savings," "checking," or "credit"—responses that I customized to match the account types supported by the bot.

In this project, I created a custom slot type to ensure Amazon Lex accepts only the account types supported by BankerNet, allowing the chatbot to respond accurately to user requests.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-ai-lex2_97dc2351)

---

## Connecting slots with intents

The restricted slot values means Lex will only accept the specific values I defined and reject any inputs that don’t match, ensuring more accurate and controlled user interactions.

I associated my custom slot with the CheckBalance intent, which collects user data—like account type and birthday—to help them check their balance accurately.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-ai-lex2_c4fc89af)

---

## Slot values in utterances

I included slot values in some of the utterances by using curly braces { }. For example, “What’s the balance in my {accountType} account?” allows Lex to capture the user’s account type directly from their input.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-ai-lex2_505be5b8)

---

## Handling failures in slot values

---

---
