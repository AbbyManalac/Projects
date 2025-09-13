<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Access S3 from a VPC

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-s3)

**Author:** Abegail Manalac  
**Email:** abby.manalac@gmail.com

---

## Access S3 from a VPC

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-s3_3e1e79a2)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC is a private virtual network in AWS where you can launch resources securely. It is useful because it gives full control over networking, including IP ranges, subnets, routing, and security.

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to host my EC2 instance and configure it so it could securely interact with AWS services like S3.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was how detailed the setup for IAM access keys would be, and how important roles are as a more secure alternative.

### This project took me...

This project took me about 2 hours, including setting up the VPC, configuring the EC2 instance, and connecting it with my S3 bucket.

---

## In the first part of my project...

### Step 1 - Architecture set up

In this step, I will create a new VPC and launch an EC2 instance inside it because these form the foundation of the project. Setting up the VPC establishes the network environment, while the EC2 instance will serve as the compute resource to connect with and access Amazon S3.

### Step 2 - Connect to my EC2 instance

In this step, I will connect directly to my EC2 instance because it allows me to access and control the server inside my VPC. This connection is essential to test, configure, and interact with AWS services like S3 from within the instance.

### Step 3 - Set up access keys

In this step, I will create access keys and configure them on my EC2 instance because the AWS CLI requires credentials to authenticate. Without access keys, the instance cannot securely interact with AWS services like S3 or perform other commands.


---

## Architecture set up

I started my project by launching a new VPC and an EC2 instance. The VPC provides the custom network environment, while the EC2 instance acts as the compute resource inside it. These two resources form the foundation needed to access and interact with Amazon S3.

I also set up an S3 bucket named "nextwork-vpc-project-abby" and uploaded two files into it. This gives my EC2 instance a target S3 resource to interact with and lets me practice listing and accessing objects from the bucket using the AWS CLI.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-s3_4334d777)

---

## Running CLI commands

AWS CLI is the Command Line Interface tool that lets me interact with AWS services from a terminal. I have access to AWS CLI because it comes pre-installed on EC2 instances, allowing me to run commands directly without needing the console.

The first command I ran was "aws s3 ls". This command is used to list all the S3 buckets in my account. It supposed to give a quick view of the available storage resources I have.

The second command I ran was "aws configure". This command is used to set up credentials, such as the Access Key ID and Secret Access Key, so that the AWS CLI can securely authenticate and access AWS services.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-s3_e7fa8776)

---

## Access keys

### Credentials

To set up my EC2 instance to interact with my AWS environment, I configured it using the "aws configure" command. This allowed me to provide my access key ID, secret access key, region, and output format so the AWS CLI can authenticate and run commands like accessing S3.

Access keys are security credentials made up of an Access Key ID and a Secret Access Key. They act like a username and password that applications or servers (like an EC2 instance) can use to securely interact with AWS services.

Secret access keys are the private part of your AWS credentials, used together with the access key ID to authenticate. They act like a password for your AWS account and should always be kept secure.

### Best practice

Although I'm using access keys in this project, a best practice alternative is to use IAM roles. By attaching a role with the right permissions to an EC2 instance, it automatically inherits credentials securely without needing to store or rotate access keys.

---

## In the second part of my project...

### Step 4 - Set up an S3 bucket

In this step, I will create a new S3 bucket and upload two files because my EC2 instance needs an S3 resource to interact with. This setup lets me practice accessing and managing objects in S3 using the AWS CLI from within my EC2 environment.


### Step 5 - Connecting to my S3 bucket

In this step, I will connect from my EC2 instance to the S3 bucket because this allows me to practice using the AWS CLI to interact with S3. By running commands from the instance, I can list and manage the objects stored in my bucket.


---

## Connecting to my S3 bucket

The first command I ran was "aws s3 ls". This command is used to list all the S3 buckets in my account. It supposed to give a quick view of the available storage resources I have.

When I ran the command "aws s3 ls" again, the terminal responded with a list of my S3 buckets. This indicated that my EC2 instance is now successfully authenticated with AWS and can interact with my S3 environment.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-s3_4334d778)

---

## Connecting to my S3 bucket

Another CLI command I ran was "aws s3 ls s3://nextwork-vpc-project-abby" which returned the list of objects stored inside my S3 bucket. This showed me the files I had uploaded earlier and confirmed that my EC2 instance could access the bucket’s contents.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-s3_4334d779)

---

## Uploading objects to S3

To upload a new file to my bucket, I first ran the command "sudo touch /tmp/test.txt". This command creates an empty text file called test.txt in the /tmp/ directory of my EC2 instance.

The second command I ran was "aws s3 cp /tmp/test.txt s3://nextwork-vpc-project-abby". This command will copy the test.txt file from my EC2 instance into my S3 bucket.

The third command I ran was "aws s3 ls s3://nextwork-vpc-project-abby", which validated that my test.txt file was successfully uploaded to the bucket by listing it alongside the other objects already stored there.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-s3_3e1e79a2)

---

---
