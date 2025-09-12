<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Creating a Private Subnet

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-private)

**Author:** Abegail Manalac  
**Email:** abby.manalac@gmail.com

---

## Creating a Private Subnet

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-private_afe1fdbd)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC (Virtual Private Cloud) is a service that lets you create a secure, isolated network within AWS. It’s useful because it gives you full control over your network setup—including IP ranges, subnets, route tables, and gateways—so you can safely run and protect your resources like EC2, RDS, and more.

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to create a secure network environment by setting up a public subnet for a web server and a private subnet for a database. I also configured route tables, a custom network ACL, and a security group to control and restrict traffic between resources.


### One thing I didn't expect in this project was...

One thing I didn't expect in this project was that even without a route to the internet, the default network ACL still allowed all traffic. I realized that for better security, I needed to create a custom ACL to block unnecessary access- even within the VPC.

### This project took me...

This project took me about almost 2 hours, including the time to plan the VPC structure, set up the subnets, configure route tables and network ACLs, and test connectivity between the resources.


---

## Private vs Public Subnets

The difference between public and private subnets is that public subnets can connect to the internet, while private subnets cannot. For example, a web server goes in a public subnet so users can access it, but a database stays in a private subnet to keep it safe from public access.

Having private subnets are useful because they keep sensitive resources, like databases and internal servers, hidden from the internet. This adds a layer of security by allowing only specific traffic from trusted sources, reducing the risk of attacks or unauthorized access.

My private and public subnets cannot have the same IP address range (CIDR block) within the same VPC. Each subnet must have a unique range so that the network can route traffic correctly between them without confusion or conflict.


![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-private_afe1fdbd)

---

## A dedicated route table

By default, my private subnet is associated with the NextWork route table, which is the default route table for the VPC. Since this table has a route to the internet gateway, keeping my private subnet on it would make it public- so I need to create a new route table for privacy.


I had to set up a new route table because the default NextWork route table has a route to the internet gateway, which would make my private subnet public. To keep the subnet truly private and block direct internet access, it needs its own route table without that internet route.

My private subnet's dedicated route table only has one inbound and one outbound rule that allows traffic within the VPC. This means resources in the private subnet can communicate with other subnets in the same VPC but not with the internet directly.


![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-private_b4b904b5)

---

## A new network ACL

By default, my private subnet is associated with NextWork NextWork ACL, since I haven’t explicitly assigned another one. This default ACL allows all traffic, which isn’t secure- so I need to create a new ACL with stricter rules to better protect my private subnet.


I set up a dedicated network ACL for my private subnet because the default ACL allows all traffic, which could expose sensitive resources to risks. Even without internet access, a compromised public subnet could still reach the private subnet if the ACL isn’t restrictive.

My new network ACL has two simple rules- one inbound and one outbound- that allow traffic only within the VPC. This means my private subnet can communicate with other subnets in the VPC, but blocks any unwanted access from outside sources.


![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-private_1ed2cb07)

---

---
