<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Build a Virtual Private Cloud

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-vpc)

**Author:** Abegail Manalac  
**Email:** abby.manalac@gmail.com

---

## Build a Virtual Private Cloud (VPC)

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-vpc_2facf927)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC (Virtual Private Cloud) lets you create a private, secure network in the AWS cloud. It’s useful because it gives you full control over your IP addresses, subnets, routing, and security, allowing you to safely run and manage AWS resources in an isolated environment.

### How I used Amazon VPC in this project

In today’s project, I used Amazon VPC to set up a secure network environment by creating a VPC, subnet, and internet gateway. This allowed me to control IP ranges, enable internet access for instances, and understand how AWS networking works through the CLI in CloudShell.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was running into errors when deleting the VPC due to leftover resources. It taught me that every component- like CIDR, subnets, and  gateways- must be cleaned up first before a VPC can be deleted.

### This project took me...

This project took me about an hour to complete, including setting up the VPC, subnet, internet gateway, running commands in CloudShell, troubleshooting errors, and documenting the process.

---

## Virtual Private Clouds (VPCs)

A Virtual Private Cloud (VPC) is like your own private space on the internet where you can safely run apps, store data, and control who can access it—just like having your own secure office in a big shared building.


There was already a default VPC in my account ever since my AWS account was created. This is because AWS automatically provides a default VPC in each region to make it easier for users to quickly launch and connect resources without needing to set up networking from scratch.


To set up my VPC, I had to define an IPv4 CIDR block, which is a range of IP addresses written in a specific format (like 10.0.0.0/16). It tells AWS what IP addresses can be used within the VPC for resources like EC2 instances and subnets.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-vpc_2facf927)

---

## Subnets

Subnets are smaller sections of a VPC that divide the IP address range into manageable parts. There are already subnets existing in my account, one for every Availability Zone in the region, allowing resources to be distributed across zones for high availability.

Once I created my subnet, I enabled auto-assign public IPv4 addresses. This setting makes sure that any EC2 instance launched in the subnet automatically gets a public IP, so that it can connect to the internet or be accessed from outside the VPC without extra steps.

The difference between public and private subnets are based on internet access. For a subnet to be considered public, it has to be associated with a route table that routes traffic to an internet gateway. Without this, the subnet remains private.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-vpc_157c4219)

---

## Internet gateways

Internet gateways are AWS components that allow resources in a VPC, like EC2 instances, to connect to the internet. They act as a bridge between the VPC and the internet, enabling both inbound and outbound traffic for public subnets.

Attaching an internet gateway to a VPC means the VPC can send and receive traffic from the internet. If I missed this step, even with a public IP, my resources wouldn't be able to access the internet or be reached from outside the VPC.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-vpc_4ae90410)

---

## Using the AWS CLI

VPC resources could also be created with CloudShell, which is a browser-based command-line tool in AWS that lets you run scripts and commands without installing anything. CLI is the AWS Command Line Interface used to manage AWS services using typed commands.


To set up a VPC or subnet, use the `aws ec2 create-subnet` command. Make sure to include required parameters like `--cidr-block` to avoid errors. The error means the CLI is missing the `--cidr-block`, so it doesn’t know what IP range to assign to the subnet, and cannot proceed.

Compared to using the AWS Console, an advantage of using commands is that it’s faster and more efficient, especially for repeated setups. An advantage of using the Console is that it’s more visual and beginner-friendly. Overall, I preferred using CLI because it saves time and feels more powerful.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-vpc_9b2465411)

---

---
