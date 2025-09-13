<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# VPC Traffic Flow and Security

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-networks-security)

**Author:** Abegail Manalac  
**Email:** abby.manalac@gmail.com

---

## VPC Traffic Flow and Security

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-security_92b0b0b4)

---

## Introducing Today's Project!

### What is Amazon VPC?

Amazon VPC (Virtual Private Cloud) lets you create a private, isolated section of the AWS cloud where you can launch resources like EC2 instances. It’s useful because it gives you full control over your network setup, including IP ranges, subnets, route tables, and security settings.

### How I used Amazon VPC in this project

I used Amazon VPC in today’s project to set up a secure and organized network. I created a VPC, attached an internet gateway, added a subnet, configured a route table to allow internet access, and set up a security group to control inbound and outbound traffic to my resources.


### One thing I didn't expect in this project was...

One thing I didn't expect in this project was how many steps were involved just to make a subnet public. From attaching the internet gateway to updating the route table and adjusting security settings- it showed how precise you need to be when configuring network access.

### This project took me...

This project took me about 1 hour and 30 minutes including setting up the VPC components, verifying connectivity, and documenting each step. It was a good balance of hands-on practice and troubleshooting.


---

## Route tables

Route tables are a set of rules in a network that determine how data is directed between subnets and other networks. In Amazon VPC, route tables control the traffic flow by specifying which path network traffic should take, based on destination IP addresses.


Route tables are needed to make a subnet public because they define how traffic is routed outside the VPC. To make a subnet public, its route table must include a route that directs internet-bound traffic (0.0.0.0/0) to an internet gateway, allowing instances in that subnet to communicate with the internet.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-security_0a07b191)

---

## Route destination and target

Routes are defined by their destination and target, which mean the destination is the IP address range of the traffic (like 0.0.0.0/0 for all internet traffic), and the target is where that traffic should be sent- such as a local network, internet gateway, NAT gateway, or another VPC connection.

The route in my route table that directed internet-bound traffic to my internet gateway had a destination of 0.0.0.0/0 and a target of igw-059f80810f1cbf020, which is the ID of my internet gateway.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-security_0a07b191)

---

## Security groups

Security groups are virtual firewalls in Amazon VPC that control inbound and outbound traffic to resources like EC2 instances. They act at the instance level and define which traffic is allowed based on rules specifying protocols, ports, and IP ranges.

### Inbound vs Outbound rules

Inbound rules are settings in a security group that define what kind of incoming traffic is allowed to reach your resource. I configured an inbound rule that allows HTTP traffic on port 80 from any IP address (0.0.0.0/0) so that my web server can be accessed publicly from the internet.

Outbound rules are settings in a security group that define what kind of outgoing traffic is allowed from your resource to other destinations. By default, my security group's outbound rule allows all traffic (all protocols, all ports) to any destination (0.0.0.0/0), enabling instances to access the internet and other services freely.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-security_92b0b0b4)

---

## Network ACLs

Network ACLs are stateless firewalls that act like traffic cops at your subnet’s borders, checking each data packet against a set of rules before allowing it in or out. They control inbound and outbound traffic at the subnet level, using numbered rules to allow or deny specific IPs, ports, and protocols.


### Security groups vs. network ACLs

The difference between a security group and a network ACL is that security groups are stateful and control traffic at the resource level, while network ACLs are stateless and control traffic at the subnet level. Security groups allow only rules; network ACLs allow and deny rules.

---

## Default vs Custom Network ACLs

### Similar to security groups, network ACLs use inbound and outbound rules

By default, a network ACL's inbound and outbound rules will allow all traffic. This means all protocols, ports, and IP addresses are permitted until you modify the rules to restrict or deny specific traffic.

In contrast, a custom ACL’s inbound and outbound rules are automatically set to deny all traffic. This means no traffic is allowed in or out until you explicitly add rules to permit specific protocols, ports, or IP address ranges.


![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-security_4faeb056)

---

## Tracking VPC Resources

I created additional VPCs, subnets, and internet gateways. Instead of my usual region, I used Asia Pacific (Singapore) which is ap-southeast-1 to practice deploying in a different location. Teams would use multiple regions to improve availability, reduce latency, and meet compliance or data residency requirements.

EC2 Global View is a tool where you can find all your EC2 resources- like instances, VPCs, subnets, and security groups- across every AWS region in one place. I could even narrow down my search by region or resource type. Without EC2 Global View, you'd have to check each region manually.

Now that I've learnt about EC2 Global View, I'd use it again to quickly audit and manage resources across multiple regions, especially when troubleshooting, cleaning up unused infrastructure, or ensuring consistent setups during multi-region deployments.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-networks-security_b03ea6162)

---

---
