<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Secure Secrets with Secrets Manager

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-security-secretsmanager)

**Author:** Abegail Manalac  
**Email:** abby.manalac@gmail.com

---

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-security-secretsmanager_r7s8t9u0)

---

## Introducing Today's Project!

In this project, I will demonstrate how to secure AWS credentials in a web app using AWS Secrets Manager. I'm doing this project to learn how to safely store and retrieve sensitive information, avoid hardcoding secrets in code, and follow best practices for cloud security.

### Tools and concepts

The services I used were AWS IAM, AWS Secrets Manager, and Amazon S3. Key concepts I learnt include securely storing and retrieving credentials, preventing hardcoding sensitive information, resolving merge conflicts in Git, and running a web app with AWS integration.

### Project reflection

This project took me approximately a 2 hours. The most challenging part was debugging errors like invalid credentials and resolving Git conflicts. It was most rewarding to see the app successfully connect to AWS and list my S3 buckets securely.

I chose to do this project today because I wanted hands-on practice with securing AWS credentials in a real-world scenario.

---

## Hardcoding credentials

In this project, a sample web app is exposing AWS credentials in its code. It is unsafe to hardcode credentials because if the code is shared publicly, anyone can see and misuse them, leading to stolen data, deleted resources, or unauthorized charges on your AWS account.

I've set up the initial configuration with "AWS_ACCESS_KEY_ID", "AWS_SECRET_ACCESS_KEY", and "AWS_REGION" inside "config.py". These credentials are just examples because they let us practice setting up the app without exposing real AWS keys. They won’t actually connect to S3 but help us learn how the code works.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-security-secretsmanager_j2k3l4m5)

---

## Using my own AWS credentials

As an extension for this project, I also decided to set up my virtual environment. To set it up, I installed the packages listed in requirements.txt, including boto3 (to interact with AWS services like S3 and Secrets Manager), fastapi (to build the web API), and uvicorn (to run the FastAPI server). These packages are essential for connecting to AWS, running the application, and making the app accessible through a web server.

When I first ran the app, I ran into an error because the AWS Access Key ID was invalid. This means the app was running correctly, but it couldn’t access my AWS account since the placeholder credentials in config.py were not real AWS credentials.

To resolve the InvalidAccessKeyId error, I updated config.py by replacing the placeholder credentials with the real AWS Access Key ID, Secret Access Key, and the correct AWS Region from IAM. The file now contains my valid AWS credentials, which allow the app to connect securely to my AWS account and list my S3 buckets.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-security-secretsmanager_wghjteykut)

---

## Pushing Insecure Code to GitHub

Once I updated the web app code with credentials, I forked the repository because I wanted my own copy stored in my GitHub account that I could edit and share publicly without changing the original. A fork is different from a clone because a fork lives online in GitHub, while a clone is only a private local copy on my computer.

To connect my local repository to the forked repository, I used "git remote set-url origin <repo-url>" to point my code to my fork on GitHub. Then I used "git add" and "git commit" to stage and save my changes as a snapshot. Finally, "git push" uploads those commits from my local machine to the forked repository online.

GitHub blocked my push because it detected hardcoded AWS credentials in "config.py". This is a good security feature because it prevents sensitive information like access keys from being exposed in public repositories, protecting accounts from unauthorized access and potential misuse.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-security-secretsmanager_o2p3q4r5)

---

## Secrets Manager

Secrets Manager is an AWS service that securely stores, encrypts, and manages sensitive information like credentials, API keys, and tokens. I’m using it to store my AWS Access Key ID and Secret Access Key instead of hardcoding them in code. Other common use cases include storing database logins, API keys, and OAuth tokens.

Another feature in Secrets Manager is secret rotation, which means automatically changing credentials on a set schedule so they’re only valid for a limited time. It’s useful in situations where you manage high-risk credentials like database passwords, privileged API keys, or service accounts, since rotation reduces the damage window if a secret is ever compromised.

Secrets Manager provides sample code in various languages, like Python, Java, and JavaScript. This is helpful because it gives developers ready-made snippets to retrieve secrets securely, making integration with their applications faster, easier, and less error-prone compared to writing custom code from scratch.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-security-secretsmanager_h2i3j4k5)

---

## Updating the web app code

I updated the config.py file to retrieve credentials securely from Secrets Manager. The get_secret() function will connect to AWS Secrets Manager, fetch the secret "aws-access-key," and handle errors with boto3 and ClientError. Instead of hardcoding keys, I copied the Python sample code, replaced the old config.py with it, and removed the placeholder comment so the app can safely pull credentials at runtime.

I also added code to config.py to extract the values from the secret returned by get_secret(). This is important because our app.py needs the AWS_ACCESS_KEY_ID, AWS_SECRET_ACCESS_KEY, and AWS_REGION variables. The new lines parse the secret with json, pull out each credential, and assign them to these variables so the app can use them securely at runtime.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-security-secretsmanager_v0w1x2y3)

---

## Rebasing the repository

Git rebasing is a way to rewrite commit history by modifying, squashing, or dropping commits. I used it to remove the commit that contained hardcoded AWS credentials. This was necessary because leaving secrets in history poses a major security risk, even if the file is later deleted.

A merge conflict occurred during rebasing because the commit I dropped contained hardcoded credentials, while the next commit also modified config.py, leaving Git unsure which changes to keep. I resolved the conflict by removing the hardcoded credentials, deleting the conflict markers, and keeping only the secure Secrets Manager code.

Once the merge conflict was resolved, I verified that my hardcoded credentials were gone by checking both locally and on GitHub. Locally, I staged and committed the clean config.py, then continued the rebase and pushed the changes. Afterward, I opened my repository on GitHub, reviewed the commit history, and confirmed that the updated config.py only contains the secure get_secret() code from AWS Secrets Manager- no plaintext credentials in sight

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-security-secretsmanager_t5u6v7w8)

---

---
