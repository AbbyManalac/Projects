<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Save User Info with a Lex Chatbot

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-ai-lex4)

**Author:** Abegail Manalac  
**Email:** abby.manalac@gmail.com

---

## Save User Info with a Lex Chatbot

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-ai-lex4_505be5b8)

---

## Introducing Today's Project!

### What is Amazon Lex?

Amazon Lex is a service that lets you build chatbots that understand natural language. It’s useful because it allows you to create smart, conversational bots without coding, using built-in tools like speech recognition and language understanding.

### How I used Amazon Lex in this project

In today’s project, I built a chatbot from scratch using Amazon Lex that greets users, handles errors with friendly responses, returns a random bank balance using account type and date of birth, and remembers the birthdate for quick follow-up checks.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was how smoothly Amazon Lex could remember and reuse user information across intents, making the chatbot feel much more intelligent and conversational with very minimal setup.

### This project took me...

This project took me less than 2 hours to complete, including building the chatbot, setting up context tags, connecting it to Lambda, and testing the follow-up intent behavior.

---

## Context Tags

Context tags in Amazon Lex store and check specific information during a conversation. They help the chatbot remember details, so users don’t have to repeat the same info, making the interaction smoother and more efficient.

Amazon Lex has two context tag types: Output context tags save info after an intent (like a birthday), while Input context tags check if info already exists before an intent runs, so the bot can skip asking again. This makes chats smoother.

I created a context tag called contextCheckBalance. This context tag was created in the CheckBalance intent. It stores information about the user’s birthday so the bot can reuse it in future intents without asking again.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-ai-lex4_97dc2351)

---

## FollowUpCheckBalance

I created a new intent called FollowupCheckBalance. The purpose of this intent is to handle follow-up questions about account balances without asking for the user’s birthday again, using previously saved information for a smoother experience.

This intent is connected to the previous intent I made, CheckBalance, because it reuses the user's saved birthday through context tags, allowing the chatbot to answer follow-up balance questions without asking for the same information again.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-ai-lex4_12345678)

---

## Input Context Tag

I created an input context, contextCheckBalance, that allows the FollowupCheckBalance intent to recognize when the user has already provided their birthday in the CheckBalance intent, so it doesn’t ask for it again.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-ai-lex4_c4fc89af)

---

## The final result!

To see the context tags and followup intent in action, I first triggered the CheckBalance intent by saying "check my balance," then followed up with "what about checking" to trigger FollowupCheckBalance and reuse my saved birthday info.

If I had triggered FollowupCheckBalance without setting up context, BankerBot would’ve asked for my date of birth again. But with context set, it remembered the info from CheckBalance and didn’t ask for it again during the follow-up.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-ai-lex4_505be5b8)

---

## Managing context expiry

---

---
