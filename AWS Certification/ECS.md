1. **Task Placement Stratigies**(AZ balanced Spread, AZ balanced binpack)
2. **Constrains**
3. ECS Service Discovery
4. ECS Service Connect
5. AWS Cloud Map Service Registry
6. Roll Back in ECS
7. Fargate tasks **use `awsvpc` network mode by default**, so each task gets its **own ENI and private IP**.
8. EC2 use bridge network by default
9. Diff bw service atuoscaling and cluster autoscaling


- **Task**: A running instance of a containerized application in AWS ECS.
- **Task Definition**: A blueprint that defines how a task should run (container image, CPU, memory, networking, etc.).
- **Service**: Manages and maintains a specified number of running tasks, ensuring availability and load balancing.

![[Pasted image 20241218001022.png]]


![[Pasted image 20241218010747.png]]



![[Pasted image 20241218181432.png]]



![[Pasted image 20241218181609.png]]




![[Pasted image 20241218181756.png]]



Yes, when you create an ECS cluster and choose the **"EC2 Linux + Networking"** or **"EC2 Windows + Networking"** launch type using the AWS Management Console, an Auto Scaling group is automatically created. This happens as part of the process of setting up the ECS instances (the EC2 instances that form the ECS cluster).


1. Go to AGS
2. Edit Scaling Limit
3. Enter the desired instances number
4. The ec2 with auto matically created and registered in ECS



![[Pasted image 20241218193101.png]]
 


![[Pasted image 20241218193238.png]]


![[Pasted image 20241218193455.png]]



1. You need to deploy a docker application on ecs but want to minimize cost by sharing instances between multiple tasks. Which launch type you will use and why?

![[Pasted image 20250304191220.png]]


1. You are running a service on ECS fargate and your application is facing high network latencty. How would you troubleshot and optimize network performance?
   
   ![[Pasted image 20250304191648.png]]


2. What Are VPC Flow Logs?

3. You need to deploy a service on ECS and ensure zero downtime during deployments? How would you configure this?

![[Pasted image 20250304192426.png]]


1. You are tasked with scaling ECS servie up and down automatically? How would you do that?

![[Pasted image 20250304193057.png]]


1. You are running an ECS service with Fargate and you want to run that specific task run on a specific period how would you set that?

![[Pasted image 20250304193922.png]]


1. How does ECS handle container placement within a cluster?

![[Pasted image 20250304195224.png]]


### **How Does Fargate Handle Tasks?**

- **Each ECS task gets its own Fargate instance.**
- There is **no shared EC2 host** like in EC2 launch mode.
- Each task is **fully isolated** with its own **CPU, memory, and networking (ENI)**.



1. How you can do path based routing in ECS?
2. How to make secure communication between ECS services?
3. How we can add variables in ECS via secret manager?
4. What is diff bw vpc CIDR and subnet CIDR?
5. I have set up my ecs with fargate now I want to add my domain tauqir.com in it and a also want to enable SSL on my domain how can I achieve this.
6. If I have 2 container running in ecs fargate and they are not connecting with other how can I troubleshoot this.


![[Pasted image 20250517043929.png]]



## Does each ECS task get its own IP?

### It depends on the **network mode**:

|Network Mode|Task IP Address Behavior|
|---|---|
|**bridge (default for EC2)**|Tasks share the EC2 instance’s IP; containers get private ports on the instance. No unique IP per task.|
|**host**|Tasks use the EC2 instance’s network stack and IP. No unique IP per task.|
|**awsvpc**|Each task gets its own **Elastic Network Interface (ENI)** and **private IP**. So **yes**, each task has its **own IP address** on the VPC.|