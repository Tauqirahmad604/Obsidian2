
1. S3 - Security Policy
2. S3 - Replication
3. S3 - Batch Replication
4. S3 - Requester Pay
5. S3 - Baseline Performence
6. S3 - Select & Glacier Select
7. S3 - Transfer Acceleration
8. S3 - Access Logs
9. S3 - Inventry


![[Pasted image 20241213215044.png]]


![[Pasted image 20241213215416.png]]


![[Pasted image 20241213215557.png]]

![[Pasted image 20241213222347.png]]


![[Pasted image 20241213222733.png]]

![[Pasted image 20241213223130.png]]


![[Pasted image 20241213225530.png]]

![[Pasted image 20241213230351.png]]


![[Pasted image 20241213230555.png]]

![[Pasted image 20241214000158.png]]

![[Pasted image 20241214001543.png]]


![[Pasted image 20241214001724.png]]


![[Pasted image 20241214002123.png]]



![[Pasted image 20241214002855.png]]



![[Pasted image 20241214003147.png]]

![[Pasted image 20241214003304.png]]



![[Pasted image 20241214003438.png]]



![[Pasted image 20241214005033.png]]



![[Pasted image 20241214005300.png]]



![[Pasted image 20241214005841.png]]



![[Pasted image 20241214010001.png]]


Without S3 Select or Glacier Select:

- You must download the entire object (which could be gigabytes or terabytes in size) and process it locally or in your application.
- This can lead to high data transfer costs and increased processing time.

With S3 Select/Glacier Select:

- You can extract only the specific data you need (e.g., certain rows or columns), drastically reducing the amount of data transferred and processed.


![[Pasted image 20241214010302.png]]



### **With Batch Operations**

You need to update the access permissions for 10 million objects in an S3 bucket. Using Batch Operations, you can automate this task with a single job submission, and AWS handles the rest.

---

### **Without Batch Operations**

You would need to write a custom script or manually update permissions object-by-object, which could take hours or days depending on the scale and compute resources.



![[Pasted image 20241231234947.png]]


**S3 Transfer Acceleration** is a feature in Amazon S3 that enables faster data transfers to and from S3 buckets over long distances. It leverages Amazon CloudFront’s globally distributed edge locations to route data through optimized network paths, resulting in reduced latency and improved transfer speeds, especially for large objects or geographically distant clients.



![[Pasted image 20241231235346.png]]


