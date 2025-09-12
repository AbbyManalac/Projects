<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Testing VPC Connectivity

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-connectivity)

**Author:** Abegail Manalac  
**Email:** abby.manalac@gmail.com

---

## Testing VPC Connectivity

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-connectivity_8ee57662)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC (Virtual Private Cloud) is a service that lets you create a private, isolated section of the AWS cloud where you can launch and control your resources. It’s useful because it gives you full control over your network settings- like IP ranges, subnets, route tables, and security- so you can design a secure and customized environment for your applications.


### How I used Amazon VPC in this project

I used Amazon VPC in today’s project to create a secure, isolated network with public and private subnets, set up route tables, and configure security rules. I tested connectivity between the public and private servers and ensured the public server could access the internet using EC2 Connect commands.

### One thing I didn't expect in this project was...

One thing I didn’t expect in this project was that even after allowing ICMP in the private server’s security group, I still couldn’t ping it from the public server until I also updated the private subnet’s network ACL to allow ICMP traffic in both inbound and outbound directions.

### This project took me...

This project took me about 2 hours to set up the VPC, configure subnets, security groups, and network ACLs, then test connectivity between the public and private servers using EC2 Connect and troubleshooting until successful communication was established.

---

## Connecting to an EC2 Instance

Connectivity means how well devices in a network can communicate with each other and the internet. It’s important because it allows data to flow smoothly, ensuring that communication, sharing, and operations happen reliably and efficiently.

My first connectivity test was whether I could connect to my public EC2 instance using EC2 Instance Connect, which gives secure, temporary SSH access directly from the AWS Console without manually creating or managing key pairs.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-connectivity_88727bef)

---

## EC2 Instance Connect

I connected to my EC2 instance using EC2 Instance Connect, which is a secure, browser-based way to SSH into your instance directly from the AWS Management Console without manually creating or managing SSH key pairs.

My first attempt at getting direct access to my public server resulted in an error, because the security group settings didn’t allow inbound SSH traffic from my IP address, blocking the connection.

I fixed this error by updating the security group settings to allow inbound SSH traffic from my IP address, ensuring EC2 Instance Connect could establish a secure connection to the server.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-connectivity_1cbb1b88)

---

## Connectivity Between Servers

Ping is a network tool that sends a small message to another device to check if it’s reachable and how long it takes to respond. I used ping to test the connectivity between my NextWork Public Server and my NextWork Private Server.

The ping command I ran was "ping <Private EC2’s private IP address>", which sent small ICMP packets from my NextWork Public Server to my NextWork Private Server to check if they could communicate.


The first ping returned no replies. This meant my Public Server sent out a ping message to the Private Server, but didn’t get any response back. That indicated a connection problem, likely because ICMP traffic was being blocked by the Private Server’s network settings.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-connectivity_defghijk)

---

## Troubleshooting Connectivity

I troubleshooted this by checking the security group and network ACL rules for both servers, then updating the Private Server’s ACL inbound and outbound rules and its security group inbound and outbound rules to allow ICMPv4 traffic so ping messages could pass through and get a response.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-connectivity_4a9e8014)

---

## Connectivity to the Internet

Curl is a command-line tool used to transfer data to or from a server. Unlike ping, which only checks if another computer is reachable, curl can actually send requests and retrieve or upload data, such as downloading a webpage’s HTML content directly to your terminal.

I used curl to test the connectivity between my NextWork Public Server and an external server by sending an HTTP request and checking if I could receive the webpage’s HTML content as a response.

### Ping vs Curl

Ping and curl are different because ping simply checks if one computer can reach another and measures the response time, while curl not only checks connectivity but can also send requests and transfer actual data, such as downloading a webpage’s HTML.

---

## Connectivity to the Internet

I ran the curl command `curl example.com`, which returned the raw HTML content of the Example website, confirming that my server could connect to the site and retrieve data successfully.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-connectivity_8ee57662)

---

---
