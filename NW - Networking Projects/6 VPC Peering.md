<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# VPC Peering

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-peering)

**Author:** Abegail Manalac  
**Email:** abby.manalac@gmail.com

---

## VPC Peering

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-peering_88727bef)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC (Virtual Private Cloud) is a service that lets you create your own isolated virtual network within the AWS cloud. It’s useful because it gives you full control over your network environment- like choosing IP address ranges, setting up subnets, and configuring security settings- so you can securely run and connect your AWS resources.

### How I used Amazon VPC in this project

Today, I used Amazon VPC to create two isolated virtual networks and set up VPC peering between them. This allowed instances in each VPC to communicate securely and privately, enabling test messages to be sent between the two instances across different VPCs.

### One thing I didn't expect in this project was...

One thing I didn’t expect in this project was that even though the setup involved two internal VPCs, an Elastic Public IP address was still needed to connect using EC2 Instance Connect. Without a public IP, remote access isn’t possible, so assigning an Elastic IP ensured I could reliably connect to the instances as it still connect to the Internet. 

### This project took me...

This project took me about two hours to complete, including setting up the VPCs, configuring VPC peering, updating security groups, and troubleshooting connection issues to ensure successful communication between the instances.

---

## In the first part of my project...

### Step 1 - Set up my VPC

In this step, I’m setting up two brand-new VPCs from scratch. I’ll use the VPC wizard and the visual resource map to quickly create each VPC along with its basic components, making the setup process fast and efficient.

### Step 2 - Create a Peering Connection

In this step, I’m creating a peering connection to link my two VPCs. This connection will let resources in one VPC communicate with resources in the other as if they were part of the same network.

### Step 3 - Update Route Tables

In this step, I’m updating the route tables in both VPCs so they know how to send traffic to each other through the peering connection. This ensures that resources in VPC 1 can reach VPC 2, and vice versa.

### Step 4 - Launch EC2 Instances

In this step, I’m launching one EC2 instance in each VPC so I can later use them to test the VPC peering connection and confirm that resources in both VPCs can communicate with each other.

---

## Multi-VPC Architecture

I started my project by launching two new VPCs using the VPC wizard and created a total of two subnets—one public subnet in each VPC to serve as the starting network setup for the project.

The CIDR blocks for VPCs 1 and 2 are unique. They have to be unique because overlapping IP address ranges would cause routing conflicts, making it impossible for the VPCs to communicate properly when we set up VPC peering.

### I also launched 2 EC2 instances

I didn't set up key pairs for these EC2 instances as I’m using EC2 Instance Connect, which lets AWS manage the key pairs for me. 


![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-peering_11111111)

---

## VPC Peering

A VPC peering connection is a networking link between two VPCs that allows them to communicate privately using their IPv4 or IPv6 addresses, without needing to go over the public internet.

VPCs would use peering connections to securely share resources and communicate with each other over a private network, avoiding the need for public internet routes and reducing security risks.

The difference between a Requester and an Accepter in a peering connection is that the Requester is the VPC that initiates the peering request, while the Accepter is the VPC that receives the request and must approve it for the connection to be established.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-peering_1cbb1b88)

---

## Updating route tables

After accepting a peering connection, my VPCs' route tables need to be updated because traffic in VPC 1 won’t know how to reach resources in VPC 2 without a route. Adding a route directs traffic bound for the other VPC to use the peering connection.

My VPCs' new routes have a destination of 10.2.0.0/16 in VPC 1’s route table and 10.1.0.0/16 in VPC 2’s route table. The routes’ target was the peering connection linking VPC 1 and VPC 2.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-peering_4a9e8014)

---

## In the second part of my project...

### Step 5 - Use EC2 Instance Connect

In this step, I’m going to connect to my first EC2 instance using EC2 Instance Connect, then troubleshoot and fix any connection errors so it can successfully communicate with the other instance.

### Step 6 - Connect to EC2 Instance 1

In this step, I’m going to use EC2 Instance Connect to connect to Instance 1 again. If I encounter any connection errors, I’ll troubleshoot and fix them so that I can successfully access the instance remotely.

### Step 7 - Test VPC Peering

In this step, I’m going to set up Instance 1 to send test messages to Instance 2. I’ll troubleshoot and fix any connection errors that come up until Instance 2 can successfully receive and send messages back to Instance 1.


---

## Troubleshooting Instance Connect

Next, I used EC2 Instance Connect to securely access my EC2 instance directly from the AWS Management Console without manually creating or managing SSH key pairs, making the connection process quicker and easier.

I was stopped from using EC2 Instance Connect as my instance had no public IPv4 address assigned. This happened because I kept the Auto-assign IP address option disabled in the network settings, but EC2 Instance Connect needs a public IP in a public subnet to work.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-peering_7685490c)

---

## Elastic IP addresses

To resolve this error, I set up Elastic IP addresses. Elastic IPs are static IPv4 addresses that stay fixed for your AWS account. They keep your EC2 instance reachable with a constant public IP, avoiding downtime caused by IP changes after restarts or launches.

Associating an Elastic IP address resolved the error because it provided the EC2 instance with a fixed public IPv4 address. Without a public IP, the instance couldn’t be reached via EC2 Instance Connect, so the Elastic IP made remote connection possible.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-peering_45663498)

---

## Troubleshooting ping issues

To test VPC peering, I ran the command `ping` from Instance 1 to the private IP address of Instance 2. This sent a small message asking if Instance 2 was reachable, helping verify that the two VPCs were properly connected.

A successful ping test would validate my VPC peering connection because it shows that network traffic can pass between the two VPCs. Receiving a reply means the instances can communicate across the peered networks, confirming the peering is correctly set up.

I had to update my second EC2 instance's security group because it wasn’t allowing ping requests from Instance 1. I added a new rule that allowed All ICMP - IPv4 traffic, enabling all types of ICMP messages, including ping requests and responses, which are essential for testing network connectivity.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-peering_7a29d352)

---

---
