<img src="https://cdn.prod.website-files.com/677c400686e724409a5a7409/6790ad949cf622dc8dcd9fe4_nextwork-logo-leather.svg" alt="NextWork" width="300" />

# Cloud Security with AWS IAM

**Project Link:** [View Project](http://learn.nextwork.org/projects/aws-security-iam)

**Author:** Abegail Manalac  
**Email:** abby.manalac@gmail.com

---

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-security-iam_1c864649)

---

## Introducing Today's Project!

In this project, I will demonstrate how to use AWS IAM to manage access and permissions in an AWS account. I'm doing this to build a strong foundation in cloud security, as access control is essential for every organization's cloud strategy.

### Tools and concepts

Today, we used Amazon EC2 and AWS IAM. Key concepts learned include IAM users, groups, policies, account aliases, and the Policy Simulator. We also learned how to write JSON policies, launch an instance, and log in as another IAM user.

### Project reflection

This project took about 1.5 hours including demo time. The hardest part was writing the JSON IAM policy with multiple statements.The most rewarding part was seeing the intern denied access to delete the production instance, proving the policy worked.

---

## Tags

Tags are organizational tools used to label resources in this project. They enable resource grouping, cost allocation, and policy application across all resources sharing the same tag key or value.

For this project, I used a tag named Env (short for Environment) on my EC2 instances. The values assigned to this tag are Production and Development to distinguish usage environments.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-security-iam_2e0e5a5d)

---

## IAM Policies

IAM policies are rule-based permissions that define who can access specific AWS resources and what actions they are allowed to perform within the AWS account.

### The policy I set up

For this project, we created an IAM policy using JSON to define specific permissions and access controls for AWS resources.

I’ve created a policy that allows the intern to perform any action on EC2 instances tagged with "development". They can view details of all instances but are explicitly denied permission to delete or create tags on any instance.

### When creating a JSON policy, you have to define its Effect, Action and Resource.

In a JSON policy, Effect specifies if an action is allowed or denied. Action lists what operations are permitted (e.g., "ec2:*"), and Resource defines which AWS resources the policy applies to.

---

## My JSON Policy

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-security-iam_1c864649)

---

## Account Alias

An account alias is a user-friendly nickname for our AWS account. Instead of using the long numeric account ID, we can use the alias to simplify login and reference to the account in AWS services.

Creating an account alias took just 30 seconds—a quick configuration in the IAM dashboard. Now, the AWS Management Console uses the alias instead of the numeric account ID for easier access and identification.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-security-iam_0eb4439b)

---

## IAM Users and User Groups

### Users

IAM users are individuals or entities that can sign in to and access our AWS account. Each user has unique credentials and can be assigned specific permissions to interact with AWS resources.

### User Groups

IAM user groups are like folders that organize IAM users, allowing you to apply permissions and access settings to all users in the group at once, rather than configuring each user individually.

We attached the policy we created to the user group, meaning any user added to this group will automatically inherit the permissions defined in the NextWorkGroupDevelopmentPolicy IAM policy.

---

## Logging in as an IAM User

The first method is to email sign-in instructions directly to the user. The second method is to download a .csv file that contains the user's login credentials and sign-in details for manual distribution.

Once logged in as our IAM user, we observed that access to several panels on the main AWS console dashboard was denied. This is expected, as permissions were limited to the development EC2 instance to restrict the intern from viewing other resources.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-security-iam_6f2ab446)

---

## Testing IAM Policies

We tested our JSON IAM policy by attempting to stop both the development and production instances.

### Stopping the production instance

When we attempted to stop the production instance, an error occurred. This happened because the instance is tagged with "production", which falls outside the scope of our permission policy. Interns are only permitted to manage development instances.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-security-iam_0e7a9d6a)

---

## Testing IAM Policies

### Stopping the development instance

Next, we attempted to stop the development instance and successfully observed the instance state change to Stopped. This confirmed that our permission policy correctly allows the intern to stop instances tagged as development.

![Image](http://learn.nextwork.org/excited_gray_zealous_miracle_fruit/uploads/aws-security-iam_1811801c)

---

## The IAM Policy Simulator

### How I used the simulator

---

---
