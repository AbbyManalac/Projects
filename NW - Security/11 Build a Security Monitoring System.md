<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a Security Monitoring System

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-security-monitoring)

**Author:** Abegail Manalac  
**Email:** abby.manalac@gmail.com

---

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-security-monitoring_reghtjy)

---

## Introducing Today's Project!

In this project, I will demonstrate how to securely store secrets using AWS Secrets Manager, track account activity with CloudTrail, and set up monitoring and alerts with CloudWatch and SNS. I’m doing this project to learn how to protect sensitive data, detect suspicious activity, and respond quickly through automated notifications.

### Tools and concepts

ervices I used were CloudTrail, CloudWatch, Secrets Manager, and SNS. Key concepts I learnt include event monitoring, alarms, and notification systems for tracking secret access.

### Project reflection

This project took me approximately 2 hours. The most challenging part was troubleshooting why the alarm didn’t trigger. It was most rewarding to finally see the alarm go In alarm and receive the email alert.

---

## Create a Secret

Secrets Manager is an AWS service that securely stores, manages, and rotates sensitive information such as passwords, API keys, and database credentials. You could use Secrets Manager to keep credentials out of your code and control access, reducing the risk of accidental exposure or leaks.

To set up for my project, I created a secret called "TopSecretInfo" under the secret type Other type of secret. It contains a key-value pair where the key is “The Secret is” and the value is a random phrase I entered. This dummy secret will act as the sensitive information we’ll monitor for access events.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-security-monitoring_o5p6q7r8)

---

## Set Up CloudTrail

CloudTrail is an AWS monitoring service that records account activity such as who performed an action, when it happened, and where it came from. I set up a trail to capture these events and store them in an S3 bucket so I can track and review any access to my secret for security and auditing purposes.

CloudTrail events include types like Management events (admin actions such as creating resources or accessing secrets), Data events (operations performed on resources like uploading to S3), Insights events (detecting unusual activity patterns), and Network activity events (changes to VPC and traffic flows). API activities are classified as Read (viewing information without changes) and Write (creating, modifying, deleting, or retrieving sensitive values).

### Read vs Write Activity

Read API activity involves viewing resources without making changes, such as listing S3 buckets or describing a secret. Write API activity involves creating, modifying, deleting, or retrieving sensitive values, like getting a secret’s value. For this project, we need both because secret retrieval is logged as a Write event, while viewing secret metadata is logged as a Read event.

---

## Verifying CloudTrail

I retrieved the secret in two ways: First, through the AWS Management Console by selecting Retrieve secret value on the secret details page. Second, using the AWS CLI in CloudShell with the get-secret-value command, which returned the secret in JSON format.

To analyze my CloudTrail events, I visited the Event history in the CloudTrail console and filtered by the event source secretsmanager.amazonaws.com. I found GetSecretValue events, which showed when my secret was accessed. This tells me CloudTrail is correctly logging secret retrievals, giving me visibility into who accessed the secret and when.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-security-monitoring_s8t9u0v1)

---

## CloudWatch Metrics

CloudWatch Logs is an AWS service that centralizes log data from CloudTrail and other sources so you can search, filter, and analyze activity across your account. It’s important for monitoring because it allows you to detect suspicious patterns, create metrics and alarms, and respond quickly to security or operational issues.

CloudTrail’s Event History is useful for quickly reviewing recent management events within the last 90 days. CloudWatch Logs are better for long-term storage, advanced filtering, and setting up alerts or automated responses when specific events occur.

A CloudWatch metric is a number you track over time. The metric value is what gets recorded when a filter finds a match (like 1 for each secret access). The default value is what gets recorded when no match is found (like 0), so your chart shows both activity and inactivity.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-security-monitoring_a9b0c1d2)

---

## CloudWatch Alarm

A CloudWatch alarm is a monitor that watches a metric and triggers when conditions are met. I set my CloudWatch alarm threshold to greater than or equal to 1 so the alarm will trigger whenever the secret is accessed within a 5-minute period

I created an SNS topic along the way. An SNS topic is a channel that lets AWS send notifications to multiple subscribers. My SNS topic is set up to send me an email alert whenever the CloudWatch alarm detects that my secret was accessed.

AWS requires email confirmation because it ensures the subscriber really wants to receive notifications. This helps prevent spam or accidental subscriptions, making sure alerts only go to verified and authorized recipients.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-security-monitoring_fsdghstt)

---

## Troubleshooting Notification Errors

o test my monitoring system, I retrieved the secret value to trigger the CloudWatch alarm. The results were that no email arrived immediately, which showed me the system needed troubleshooting. 

When troubleshooting the notification issues I checked CloudTrail for GetSecretValue events, verified CloudTrail delivered logs to CloudWatch, tested metric filters, confirmed CloudWatch alarms triggered actions, and ensured SNS delivered emails.

I initially didn’t receive an email because SNS delivery wasn’t properly configured or confirmed. The key solution was verifying my subscription, ensuring permissions, and checking CloudWatch alarms linked correctly to the SNS topic.

---

## Success!

To validate my monitoring system, I accessed my secret again and checked CloudWatch to see my alarm move into the In alarm state. I then confirmed success by receiving an email notification from SNS, proving alerts work as expected.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-security-monitoring_ageraergearge)

---

## Comparing CloudWatch with CloudTrail Notifications

In a project extension, I updated my CloudTrail configurations to enable direct SNS notifications because I wanted to compare how CloudTrail notifications work versus CloudWatch alarms. This helps me understand different monitoring approaches and their impact on system design.

After enabling CloudTrail SNS notifications, my inbox quickly filled up with many emails since CloudTrail sends alerts for every log file delivered. In terms of usefulness, I thought these emails were overwhelming, while CloudWatch alarms are more focused and actionable.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-security-monitoring_d7e8f9g0)

---

---
