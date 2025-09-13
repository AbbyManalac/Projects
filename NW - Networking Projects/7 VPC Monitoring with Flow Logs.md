<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# VPC Monitoring with Flow Logs

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-monitoring)

**Author:** Abegail Manalac  
**Email:** abby.manalac@gmail.com

---

## VPC Monitoring with Flow Logs

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-monitoring_3e1e79a1)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC is a virtual network in AWS that allows you to launch resources in a secure, isolated environment. It is useful because it gives full control over network configuration, security, and traffic routing for cloud resources.

### How I used Amazon VPC in this project

In today's project, I used Amazon VPC to monitor and analyze network traffic, ensuring resources communicated securely. I configured subnets, routing, and security settings to control traffic flow and observe interactions between cloud instances.

### One thing I didn't expect in this project was...

One thing I didn't expect in this project was how quickly traffic patterns could be visualized and analyzed within the VPC. Seeing real-time insights on data transfer between instances was more detailed and interactive than I anticipated.

### This project took me...

This project took me approximately 2–3 hours, including setup, configuring the VPC, running traffic monitoring queries, and reviewing the results. The hands-on approach made the process smooth yet insightful.

---

## In the first part of my project...

### Step 1 - Set up VPCs

In this step, I will set up two VPCs using the VPC wizard because it allows me to quickly create isolated networks and prepare them for monitoring and peering in the next stages of the project.


### Step 2 - Launch EC2 instances

In this step, I will launch an EC2 instance in each VPC because we need them to generate network activity and test the VPC peering connection later in the project.


### Step 3 - Set up Logs

In this step, I will set up VPC Flow Logs because they let us track all inbound and outbound network traffic and store the records for analysis, helping us monitor connectivity and security across our VPCs.

### Step 4 - Set IAM permissions for Logs

In this step, I will set up an IAM policy and role for VPC Flow Logs because they need permission to write log data and send it to CloudWatch, which allows us to finish configuring our subnet’s flow log.

---

## Multi-VPC Architecture

I started my project by launching two VPCs (NextWork-1 and NextWork-2) using the VPC wizard. Each VPC was set up with one public subnet, no private subnets, and a unique CIDR block to avoid overlap.


The CIDR blocks for VPCs 1 and 2 are 10.1.0.0/16 and 10.2.0.0/16. They have to be unique because overlapping IP ranges would cause routing conflicts, making it impossible for resources in different VPCs to communicate reliably.


### I also launched EC2 instances in each subnet

My EC2 instances’ security groups allow ICMP (ping) traffic from all IP addresses (0.0.0.0/0). This is because we need to run ping tests later, and allowing ICMP from everywhere ensures the instances can respond to connectivity checks.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-monitoring_e7fa8775)

---

## Logs

Logs are records of events in a system, like logins, errors, or activity. They act as a diary that helps monitor performance, troubleshoot problems, and track security to understand what’s happening within your network or applications.

Log groups are containers in AWS that organize related logs from the same source or application. They’re region-specific, but you can use CloudWatch dashboards to bring logs from different regions together for easier monitoring and analysis.

### I also set up a flow log for VPC 1

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-monitoring_e8398869)

---

## IAM Policy and Roles

I created an IAM policy because VPC Flow Logs don’t have permission by default to record logs and send them to CloudWatch. This policy grants the necessary actions—like creating log groups, streams, and putting log events—so Flow Logs can store and manage traffic data properly.

I also created an IAM role because roles bundle policies together and let us assign those permissions to AWS services. While the IAM policy defines what actions Flow Logs can take, the IAM role is how we give Flow Logs those permissions so they can actually send data to CloudWatch.

A custom trust policy is a special type of policy that defines who can assume a role. Unlike IAM policies, which define what actions are allowed, trust policies act like a VIP list—only the specified services or users (in this case, VPC Flow Logs) are allowed to use the role.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-monitoring_4334d777)

---

## In the second part of my project...

### Step 5 - Ping testing and troubleshooting

In this step, I will send test messages from Instance 1 in VPC 1 to Instance 2 in VPC 2 because this generates network traffic for our flow logs to capture and also verifies that our VPC peering connection is working correctly.


### Step 6 - Set up a peering connection

In this step, I will create a peering connection between VPC 1 and VPC 2 because without it, the instances can only communicate over the public internet. The peering connection will allow secure, private communication using their private IPs.

### Step 7 - Analyze flow logs

In this step, I will analyze the VPC Flow Logs because they capture all network traffic in my VPC. Reviewing them helps me understand how my instances are communicating, verify connectivity, and spot any issues or unusual activity in the network.

---

## Connectivity troubleshooting

My first ping test had no replies, meaning the EC2 instances can’t reach each other. This isn’t a good response- it shows a network issue. Since ICMP is allowed in security groups, the problem is likely missing or incorrect routes between the VPCs.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-monitoring_99d4ba42)

I could receive ping replies if I ran the ping test using the other instance's public IP address, which means the instances can talk to each other over the public internet and that their security groups, routing, and ICMP rules are correctly allowing traffic through.

---

## Connectivity troubleshooting

Looking at VPC 1's route table, I identified that the ping test with Instance 2's private address failed because there’s no direct route to VPC 2. Without a VPC peering connection route, traffic only goes out via the internet gateway, not privately between the two VPCs.

### To solve this, I set up a peering connection between my VPCs

I also updated both VPCs' route tables so that traffic meant for the other VPC knows to travel through the peering connection. Without these routes, the instances wouldn’t be able to communicate privately using their private IP addresses.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-monitoring_7316a13d)

---

## Connectivity troubleshooting

I received ping replies from Instance 2's private IP address! This means the VPC peering connection and route tables are correctly configured, allowing private communication between the two instances without needing to go over the public internet.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-monitoring_4ec7821f)

---

## Analyzing flow logs

Flow logs tell us about the details of network traffic, such as source and destination IPs, ports, protocol, traffic type, action (ACCEPT or REJECT), and byte/packet counts. Each part helps us see who is talking to who, how, and whether the traffic was allowed or blocked.

For example, the flow log I’ve captured tells us that instance 10.2.6.246 in VPC 2 successfully sent ICMP traffic (ping) to instance 10.0.9.56 in VPC 1. It shows 58 packets (4872 bytes) were sent, and the action ACCEPT with status OK confirms the traffic was allowed. This means the VPC peering and security group settings are working correctly, enabling private communication between the two instances.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-monitoring_d116818e)

---

## Logs Insights

Logs Insights is a CloudWatch feature that lets you query and analyze logs. By running queries, you can filter, process, and combine log data to troubleshoot issues, track patterns, and gain insights into your network or application activity.

I ran the query "Top 10 byte transfers by source and destination IP addresses". This query analyzes network traffic to identify which source and destination IP pairs are transferring the most data, revealing the busiest traffic paths in the VPC.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-monitoring_3e1e79a1)

---

---
