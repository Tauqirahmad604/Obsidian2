
1. Lamda Concruccy
2. Lamda Snapstart
3. DynamoDB Accelrator (DAX)
4. DynamoDB Stream



![[Pasted image 20241219195503.png]]

![[Pasted image 20241219195857.png]]



![[Pasted image 20241219203446.png]]



![[Pasted image 20241219203558.png]]



![[Pasted image 20241219203723.png]]


![[Pasted image 20241219204427.png]]


![[Pasted image 20241219204727.png]]




![[Pasted image 20241219220751.png]]


In AWS Lambda, **concurrency** refers to the number of function instances that are executing at the same time. Each instance of a Lambda function can handle one request at a time, so concurrency determines how many requests can be processed simultaneously.


### **How Concurrency Works in Lambda:**

1. When a Lambda function is triggered, AWS Lambda creates an instance of the function to handle the request.
2. If multiple requests arrive at the same time, Lambda will spin up additional instances to handle each request concurrently.
3. The **concurrency limit** determines how many such instances can run at the same time.


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




![[Pasted image 20241220012123.png]]


![[Pasted image 20241220014005.png]]


![[Pasted image 20241220014345.png]]