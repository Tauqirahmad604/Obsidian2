
1. Lamda Concruccy
2. Lamda Snapstart
3. DynamoDB Accelrator (DAX)
4. DynamoDB Stream



![[Pasted image 20241219195503.png]]

![[Pasted image 20241219195857.png]]



![[Pasted image 20241219203446.png]]



![[Pasted image 20241219203558.png]]


![[Pasted image 20241219204427.png]]


![[Pasted image 20241219204727.png]]




![[Pasted image 20241219220751.png]]


In AWS Lambda, **concurrency** refers to the number of function instances that are executing at the same time. Each instance of a Lambda function can handle one request at a time, so concurrency determines how many requests can be processed simultaneously.

## **What is Concurrency in AWS Lambda?**

💡 **Concurrency** in Lambda refers to the number of **simultaneous executions** of your function at any given time.

### **🔹 Types of Concurrency in AWS Lambda**

AWS Lambda supports three types of concurrency:

|**Type**|**Description**|
|---|---|
|**Unreserved Concurrency**|Default, shared across all functions in your account.|
|**Reserved Concurrency**|Limits concurrency for a specific function (prevents overuse).|
|**Provisioned Concurrency**|Keeps functions "warm" for predictable latency.|

---

### **🔹 Example of Concurrency in Lambda**

- If **1000 requests** arrive at the same time, and your function takes **1 second** to execute, Lambda will run **1000 instances** simultaneously.
- If you set **reserved concurrency = 100**, then only **100 requests** will be processed at a time. The rest **will be throttled** (fail or retry).

### **How Concurrency Works in Lambda:**

1. When a Lambda function is triggered, AWS Lambda creates an instance of the function to handle the request.
2. If multiple requests arrive at the same time, Lambda will spin up additional instances to handle each request concurrently.
3. The **concurrency limit** determines how many such instances can run at the same time.
4. By default, Lambda provides your account with a total concurrency limit of **1,000 concurrent executions** across all functions in an AWS Region.


![[Pasted image 20241219225934.png]]


**SnapStart** in AWS Lambda is a feature designed to improve the **startup performance** of Java-based Lambda functions by reducing the "cold start" time. Cold starts occur when AWS spins up a new instance of your Lambda function to handle a request, which can involve loading the runtime, initializing dependencies, and setting up your application. For Java functions, this process can be particularly slow because of the way the Java Virtual Machine (JVM) initializes.

### **Limitations of SnapStart:**

1. **Java Runtime Only**:
    - Currently, SnapStart is supported only for Lambda functions using the **Java 11 runtime**.


![[Pasted image 20241219230204.png]]



![[Pasted image 20241219235120.png]]



![[Pasted image 20241220003947.png]]


![[Pasted image 20241220004148.png]]



![[Pasted image 20241220004418.png]]



![[Pasted image 20241220005008.png]]


![[Pasted image 20241220005101.png]]


![[Pasted image 20241220005501.png]]



![[Pasted image 20241220005631.png]]


DynamoDB Streams is like a "log" that tracks changes to your data in a DynamoDB table, such as when data is added, updated, or deleted. It helps you **react to those changes** automatically.

### **How It Works in Simple Terms:**

1. **Changes to Data**: When you add, update, or delete items in your DynamoDB table, those changes are captured in a stream.
2. **Stream Records**: The stream records the changes with details like what data was changed and how (added, updated, deleted).
3. **Process the Changes**: You can set up a system (like AWS Lambda) to listen to the stream and automatically take action when something changes (e.g., send an email or update another system).


![[Pasted image 20241220010051.png]]



![[Pasted image 20241220010234.png]]



![[Pasted image 20241220010433.png]]



![[Pasted image 20241220010612.png]]



![[Pasted image 20241220010742.png]]



![[Pasted image 20241220011735.png]]



![[Pasted image 20241220012009.png]]


# AWS VPC Endpoint Services vs AWS Gateway VPC Endpoints


In AWS, both VPC Endpoint Services and Gateway VPC Endpoints provide connectivity between resources within your Virtual Private Cloud (VPC) and AWS services, but they serve different purposes and have different use cases:

1. VPC Endpoint Service:

- VPC Endpoint Services allow AWS services hosted in a VPC to be accessed by resources in other VPCs or from the internet (depending on your configuration).
- You create a VPC Endpoint Service to expose your own service or application within your VPC to other VPCs without exposing it to the public internet.
- This is useful when you want to build a service that other AWS accounts or VPCs can access securely without requiring public IP addresses or traversing the internet.
- Examples of services that can be exposed through VPC Endpoint Services include AWS PrivateLink, AWS Marketplace, and custom services running within your VPC.

2. Gateway VPC Endpoint:

- Gateway VPC Endpoints provide private connectivity to AWS services such as Amazon S3 and DynamoDB from within your VPC.
- They act as a gateway that routes traffic from your VPC to the AWS service over the AWS private network, bypassing the internet.
- Gateway VPC Endpoints are useful when you need to access AWS services privately from your VPC without going over the internet, improving security and reducing data transfer costs.
- They currently support Amazon S3 and DynamoDB, allowing you to access these services without using public IP addresses or going through a NAT gateway.

In summary, VPC Endpoint Services are used to expose your own services or applications securely to other VPCs, while Gateway VPC Endpoints provide private connectivity to specific AWS services from within your VPC. The choice between the two depends on whether you need to expose your own service or access AWS services privately within your VPC.



![[Pasted image 20241220012123.png]]


![[Pasted image 20241220014005.png]]


![[Pasted image 20241220014345.png]]



