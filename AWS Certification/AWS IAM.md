1. AWS Organizations
2. Organiztional Units
3. IAM Conditions
4. IAM Identity Center(SSO)
5. EC2 Instance Profile
6. How would you prevent the creation of AWS resources unless they have a specific tag?
7. If I have 50 users in my aws and I want to check the permission of all users how can I do this?
8. What is docker layer?
9. How to add enviroment variable at build time in docker?
10. If you want to give access to another account you need to create a role and then other account must assume that role and then he can access services in your account.
11. If I want to share session of my server or vm with any one how to do that?


### EC2 Instance Profile

![[Pasted image 20250517221015.png]]


You **attach an instance profile to an EC2 instance**, and **that instance profile contains the IAM role**.  
➡️ **IAM role = permissions** 
➡️ **Instance profile = the container that EC2 understands and uses to get the role**

---

## 🔍 Why Not Just Attach the IAM Role Directly?

Because the **EC2 service needs a special format** to associate IAM credentials — that’s where the **instance profile** comes in.

### Think of it like this:

| Concept              | Description                                                               |
| -------------------- | ------------------------------------------------------------------------- |
| **IAM Role**         | The set of permissions (what actions are allowed on which AWS resources). |
| **Instance Profile** | A wrapper that delivers the IAM role to the EC2 instance.                 |
| **EC2 Needs**        | An **instance profile**, not a role directly.                             |

👉 When you attach a role to an EC2 instance, you're **really attaching the instance profile** behind the scenes.

## Behind the Scenes (AWS Console or CLI)

- When you create a role for EC2 using the console, AWS **automatically** creates an instance profile with the **same name** as the role.
    
- If using the CLI or Terraform, you may need to **explicitly create and associate the instance profile.**





## AWS Policies Overview

AWS uses a variety of policy types to manage access and permissions for users, services, and resources. Each policy type serves a specific purpose in ensuring security, compliance, and operational control.

---

### 1. **Identity-based Policies (IAM Policies)**

These policies are attached to IAM users, groups, or roles. They define **what actions are allowed or denied** for those identities on specific AWS resources.

✅ **Example Use Case**:  
Allow a user to start EC2 instances and read from S3 buckets.

---

### 2. **Resource-based Policies**

Attached directly to AWS resources such as S3 buckets, Lambda functions, SNS topics, or SQS queues. They define **who (principal) can access the resource and what actions they can perform**.

✅ **Example Use Case**:  
Grant read access to an S3 bucket for another AWS account.

---

### 3. **Service Control Policies (SCPs)**

Used within AWS Organizations. SCPs set **permission boundaries** for AWS accounts, OUs (Organizational Units), or the entire organization. They **restrict what permissions can be granted**, even if an IAM policy allows them.

✅ **Example Use Case**:  
Prevent all member accounts from creating resources outside a specific region.

---

### 4. **Permissions Boundaries**

Define the **maximum permissions** an IAM user or role can have. They don’t grant permissions themselves, but rather act as an upper limit.

✅ **Example Use Case**:  
Allow a developer to be granted any permissions, but restrict them to S3 and DynamoDB only.

---

### 5. **Session Policies**

Temporary policies that can be passed when a role is assumed using AWS STS (Security Token Service). They provide **additional restrictions during the session's lifetime**.

✅ **Example Use Case**:  
Allow temporary read-only access to a specific folder in S3.

---

### 6. **Access Control Lists (ACLs)**

Legacy mechanism used in services like S3 and VPC to **grant specific permissions to individual AWS accounts**. While still supported, they are less flexible than policies and not recommended for new designs.

---

## 📌 Summary Table

| **Policy Type**         | **Attached To**                      | **Purpose**                            |
| ----------------------- | ------------------------------------ | -------------------------------------- |
| Identity-based Policies | IAM users, groups, roles             | Grant permissions to perform actions   |
| Resource-based Policies | S3, Lambda, SNS, SQS, etc.           | Control access to the resource itself  |
| SCPs                    | AWS Organizations (Accounts/OUs)     | Restrict permissions across the org    |
| Permissions Boundaries  | IAM users or roles                   | Limit the max permissions allowed      |
| Session Policies        | Temporary sessions (STS)             | Restrict permissions during a session  |
| ACLs                    | S3 buckets, network interfaces, etc. | Legacy access control between accounts |


### 1. **IAM security tools** 
 
i.  **Credentials Report**
   It have all the credentials report of the user. Like when user was created, password is enabled or disabled, when last time password was used etc.
   
   
ii.  **Access Advisor**
   It shows the service permissions granted to a user and when those services were last accessed. You can use this information to revise your policies.


![[Pasted image 20250101175707.png]]


![[Pasted image 20250101181329.png]]



![[Pasted image 20250101191018.png]]



![[Pasted image 20250101191927.png]]


![[Pasted image 20250101203517.png]]