<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# VPC Endpoints

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-endpoints)

**Author:** Abegail Manalac  
**Email:** abby.manalac@gmail.com

---

## VPC Endpoints

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-endpoints_09bcaa8a)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC is a private virtual network in AWS where you can launch and manage resources securely. It is useful because it gives you full control over networking, routing, and access, ensuring your resources stay isolated and protected.

### How I used Amazon VPC in this project

In today’s project, I used Amazon VPC to launch an EC2 instance, connect it to an S3 bucket, and set up a VPC endpoint so the instance could securely access S3 without using the public internet.

### One thing I didn't expect in this project was...

One thing I didn’t expect in this project was that after applying the bucket policy, I could no longer access the S3 bucket through the console, since the policy only allowed traffic from the VPC endpoint.

### This project took me...

This project took me around 2 hours, including setting up the VPC, configuring the EC2 instance, testing access with credentials, and troubleshooting the VPC endpoint and route table.

---

## In the first part of my project...

### Step 1 - Architecture set up

In this step, I will create a new VPC, launch an EC2 instance, and set up an S3 bucket because these resources form the core architecture needed to test secure communication using VPC endpoints.

### Step 2 - Connect to EC2 instance

In this step, I will connect directly to my EC2 instance using EC2 Instance Connect because I need to test accessing S3 through the public internet first, before setting up a secure VPC endpoint connection.

### Step 3 - Set up access keys

In this step, I will create and configure access keys because my EC2 instance needs credentials to securely connect to and interact with AWS services like S3.

### Step 4 - Interact with S3 bucket

In this step, I will connect my EC2 instance to the S3 bucket using the access keys because this allows me to securely list, view, and manage the objects in the bucket from the instance using the AWS CLI.

---

## Architecture set up

I started my project by launching a new VPC with one public subnet and default settings, and an EC2 instance inside that VPC using Amazon Linux 2023. I also created a new security group to enable SSH access for EC2 Instance Connect.

I also set up an S3 bucket named nextwork-vpc-project-abby in the same region as my VPC. After creating the bucket, I uploaded two files from my local computer, which I’ll later access and manage from my EC2 instance using the AWS CLI.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-endpoints_4334d777)

---

## Access keys

### Credentials

To set up my EC2 instance to interact with my AWS environment, I configured the Access Key ID, Secret Access Key, Default region name, and Default output format. These settings allow the AWS CLI on my instance to securely access and manage AWS services like S3.

Access keys are credentials made up of an Access Key ID (like a username) and a Secret Access Key (like a password). They allow applications, servers, or EC2 instances to securely interact with AWS services without using the AWS Management Console.

Secret access keys are the private part of your AWS credentials, used together with the Access Key ID to authenticate. They act like a password, granting access to AWS services, and must be kept secure and never shared.

### Best practice

Although I'm using access keys in this project, a best practice alternative is to use IAM roles. Roles allow EC2 instances (and other AWS resources) to securely inherit permissions without needing long-term credentials, improving security and manageability.

---

## Connecting to my S3 bucket

The command I ran was "aws s3 ls". This command is used to list all the S3 buckets in my AWS account, allowing me to quickly check which buckets I have access to from my EC2 instance.

The terminal responded with a list of all S3 buckets in my account, including "vpc-project-abby". This indicated that the access keys I set up were correctly configured and my EC2 instance could successfully authenticate and interact with AWS services.


![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-endpoints_4334d778)

---

## Connecting to my S3 bucket

I also tested the command "aws s3 ls s3://nextwork-vpc-project-abby", which returned a list of all objects inside my S3 bucket. This showed the files I uploaded earlier and confirmed that my EC2 instance could access the bucket’s contents.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-endpoints_4334d779)

---

## Uploading objects to S3

To upload a new file to my bucket, I first ran "sudo touch /tmp/nextwork.txt". This command creates an empty file named nextwork.txt in the /tmp/ directory on my EC2 instance.

The second command I ran was "aws s3 cp /tmp/nextwork.txt s3://nextwork-vpc-project-abby". This command copies the file from my EC2 instance into my S3 bucket.

The third command I ran was "aws s3 ls s3://nextwork-vpc-project-abby", which validated that nextwork.txt was successfully uploaded by listing all objects in the bucket.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-endpoints_3e1e79a2)

---

## In the second part of my project...

### Step 5 - Set up a Gateway

In this step, I will create a VPC endpoint because it allows my VPC to communicate directly with my S3 bucket without going through the public internet, improving security and keeping traffic within the AWS network.

### Step 6 - Bucket policies

In this step, I will create a super secure S3 bucket policy that blocks all traffic except requests coming from my VPC endpoint. This will validate that the endpoint is working correctly and ensure my EC2 instance can access the bucket securely without using the public internet.

### Step 7 - Update route tables

In this step, I will test whether my EC2 instance can still access my S3 bucket now that the bucket policy only allows traffic from the VPC endpoint. I’m doing this to confirm that the endpoint is correctly set up and providing secure, private access to S3.

### Step 8 - Validate endpoint conection

In this step, I will access my S3 bucket from my EC2 instance one last time to confirm that the VPC endpoint is working correctly. I'm doing this to ensure that all traffic to S3 is now routed privately through the endpoint, making my setup secure and removing dependency on the public internet.

---

## Setting up a Gateway

I set up an S3 Gateway, which is a type of endpoint that adds a route to my VPC’s route table, directing traffic bound for S3 straight to the Gateway instead of the internet. This allows my VPC to access S3 privately and securely.

### What are endpoints?

An endpoint is a service that enables private connections between my VPC and other AWS services, like S3, without sending traffic over the public internet. This keeps data secure and ensures communication stays within the AWS network.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-endpoints_09bcaa8a)

---

## Bucket policies

A bucket policy is a type of IAM policy specifically designed to manage access to an S3 bucket. It lets you define who can access the bucket and what actions they can perform, giving you fine-grained control over permissions for that bucket and its objects.

My bucket policy will deny all actions on my S3 bucket and its contents to everyone except requests coming from my VPC endpoint. This ensures that only traffic routed through the endpoint can access the bucket, keeping all other internet traffic blocked.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-endpoints_7316a13d)

---

## Bucket policies

Right after saving my bucket policy, my S3 bucket page showed 'denied access' warnings. This was because the policy blocks all access to the bucket unless the request comes through my VPC endpoint, so any attempt to access it from the AWS Management Console or other sources is automatically denied.

I also had to update my route table because without a route to the VPC endpoint, traffic from my EC2 instance would try to reach the S3 bucket via the public internet instead of through the private endpoint.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-endpoints_4ec7821f)

---

## Route table updates

To update my route table, I selected the VPC endpoint I created, chose Manage route tables, and added my public subnet’s route table so that traffic destined for S3 is routed through the VPC endpoint.

After updating my public subnet's route table, my terminal returned a list of the objects in my S3 bucket, including the files I uploaded earlier. This indicated that my EC2 instance could now access S3 privately through the VPC endpoint, confirming that the endpoint was set up correctly.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-endpoints_d116818e)

---

## Endpoint policies

An endpoint policy is a JSON-based policy document that controls which AWS services and resources can be accessed through a specific VPC endpoint. It works like an extra layer of permissions, letting you allow or deny certain actions for traffic going through the endpoint.

I updated my endpoint's policy by changing "Effect": "Allow" to "Effect": "Deny". I could see the effect of this right away because my EC2 instance could no longer access the S3 bucket, proving that the endpoint policy successfully blocked the connection.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-endpoints_3e1e79a3)

---

---
