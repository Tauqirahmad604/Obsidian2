Topics:
1. Health Checks
2. Types of Load balancer
3. Load Balancer Security Group
4. Sticky Sessions
5. Cross Zone Load Balancing
6. Load Balacancer SSL certificate
7. SSL SNI(Service Name Indication)
8. Connection draining


![[Pasted image 20241209161354.png]]

  ![[Pasted image 20241209161549.png]]


![[Pasted image 20241209161756.png]]

 ![[Pasted image 20241209161946.png]]


![[Pasted image 20241209162201.png]]

 ![[Pasted image 20241209162432.png]]

![[Pasted image 20241209162807.png]]

![[Pasted image 20241209163044.png]]





![[Pasted image 20241210163532.png]]


![[Pasted image 20241210163822.png]]



![[Pasted image 20241210173440.png]]


### What is it?

**AWS Gateway Load Balancer** is a service that helps you easily add and manage third-party tools (like security devices, firewalls, or monitoring tools) in your network. These tools inspect and process your network traffic.

### Key Idea:

Imagine you have a **cloud network** (like a private cloud environment in AWS) where data is coming in and out (from websites, apps, etc.). Sometimes, you need to check or filter that data before it goes to its destination—like making sure it's secure or checking for any problems.

**Gateway Load Balancer** helps you do that by automatically sending this traffic to **special tools** (called "virtual appliances") that process the traffic and then send it back to your network.


![[Pasted image 20241210173510.png]]




![[Pasted image 20241210174041.png]]



![[Pasted image 20241210174746.png]]





![[Pasted image 20241210175804.png]]




![[Pasted image 20241210175925.png]]




![[Pasted image 20241210180915.png]]


![[Pasted image 20241210181410.png]]



![[Pasted image 20241210182207.png]]


- When connection draining is enabled, the load balancer stops sending new traffic to the deregistering instance but continues to route existing connections to it.
- The instance is allowed to complete its in-flight requests within a specified timeout period, avoiding abrupt disconnections.
- Once all in-flight requests are processed, or the timeout period is reached, the instance is deregistered or stopped.



![[Pasted image 20241210182402.png]]



![[Pasted image 20241210182402.png]]


![[Pasted image 20241210182848.png]]


![[Pasted image 20241210183017.png]]



![[Pasted image 20241210185935.png]]

![[Pasted image 20241210214429.png]]


![[Pasted image 20241210214600.png]]

