<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Launching VPC Resources

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-ec2)

**Author:** Abegail Manalac  
**Email:** abby.manalac@gmail.com

---

## Launching VPC Resources

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-ec2_8ee57662)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC (Virtual Private Cloud) is a service that lets you create a private, isolated network within AWS. It’s useful because it gives you full control over your network setup- like IP ranges, subnets, route tables, and gateways- so you can securely run and manage your cloud resources.

### How I used Amazon VPC in this project

In today’s project, I used Amazon VPC to build a secure network environment by creating a custom VPC with public and private subnets. I set up route tables, a security group, and a network ACL to control traffic, and launched EC2 instances in both subnets to manage access and communication.

### One thing I didn't expect in this project was...

One thing I didn’t expect was how helpful the “VPC and more” setup option was. The visual resource map clearly showed how subnets, route tables, and gateways connect, making it much easier to understand and correctly configure the VPC architecture from the start.

### This project took me...

This project took me about 3 hours. It included setting up the VPC using the “VPC and more” option, configuring public and private subnets, route tables, security groups, a network ACL, and launching EC2 instances to test connectivity and access.

---

## Setting Up Direct VM Access

Directly accessing a virtual machine means logging into and controlling its operating system through the terminal, like installing software or running commands- as if you're using the machine in person, but remotely over the internet using a secure connection like SSH.

### SSH is a key method for directly accessing a VM

SSH traffic means Secure Shell traffic, used to securely access your EC2 instance’s terminal. It verifies your private key matches the instance’s public key, ensuring only authorized access. All data sent is encrypted, making it safe for managing and troubleshooting servers.

### To enable direct access, I set up key pairs

Key pairs are two cryptographic keys (public and private) used to securely access EC2 instances. The public key is on the server, and the private key stays with you. It lets you directly log in to the instance’s terminal to run scripts or manage the OS, like you're using it in person.

A private key's file format means the type of file used to store the private key, which determines how it can be used or imported. My private key's file format was ".pem", which is commonly used for SSH access to EC2 instances in AWS.

---

## Launching a public server

I had to change my EC2 instance's networking settings by switching from the default VPC to the NextWork VPC and selecting the NextWork Public Subnet. This tells AWS to launch the instance in the custom network setup we created instead of the default one.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-ec2_88727bef)

---

## Launching a private server

My private server has its own dedicated security group because it needs stricter access controls. Unlike the public server, it shouldn't be open to the internet. This security group only allows trusted traffic, like connections from my public server, to keep the private server protected.

My private server's security group's source is NextWork Public Security Group, which means only resources in that group can access the private server. This is much safer than using "Anywhere" (0.0.0.0/0), because it limits access to trusted instances instead of the whole internet.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-ec2_4a9e8014)

---

## Speeding up VPC creation

I used an alternative way to set up an Amazon VPC! This time, I selected "VPC and more” instead of just creating a VPC. It showed a visual flow called the VPC resource map, which helped me create the VPC along with subnets, route tables, and other resources all at once.

A VPC resource map is a visual diagram in the AWS VPC setup wizard that shows how different network components- like subnets, route tables, and gateways- are connected. It helps you understand and create all the necessary VPC resources in one clear, guided view.

My new VPC has a CIDR block of 10.0.0.0/16. It is possible for my new VPC to have the same IPv4 CIDR block as my existing VPC because VPCs are isolated from each other by default, even within the same region and account. There’s no IP conflict unless you connect them using VPC peering.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-ec2_1cbb1b88)

---

## Speeding up VPC creation

### Tips for using the VPC resource map

When determining the number of public subnets in my VPC, I only had two options: 1 or 2. This was because AWS enforces best practices by encouraging high availability through redundancy- putting one public subnet in each of two Availability Zones. The setup wizard limits it to two to keep things simple, but I can add more manually later if needed.

The set up page also offered to create NAT gateways, which are used to let instances in private subnets access the internet for things like updates or patches, while blocking any inbound traffic. Unlike internet gateways, which allow two-way communication, NAT gateways only allow outbound traffic, keeping private instances secure.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-ec2_8ee57662)

---

---
