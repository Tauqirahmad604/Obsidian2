#### API Gateway is a managed AWS service that provides a secure, scalable front door to expose and manage your APIs by routing client requests to backend services like Lambda or HTTP servers.

Why we need it?

How was application serving in monolithic.
![[Pasted image 20250517060146.png]]



Now look at the benifits of Api Gateway. The things we need to manage on own API by our own like authencitaion, authorization, SSL termination it is now managed buy aws Api Gateway.


![[Pasted image 20250517061158.png]]


![[Pasted image 20250517070008.png]]
# What is **API Gateway**?

Imagine API Gateway as a **doorway or gate** to your application on the internet.

- It **listens** to incoming requests (like when someone visits your website or app).
    
- It **decides** what to do with these requests.
    
- Then it **passes** those requests to the right place (your backend, a Lambda function, or another service).
    
- Finally, it sends back the **response** to the user.
    

---

# Is API Gateway a server where I deploy my code?

**No!**

API Gateway is **not a server where you write or run your application code**. Instead, it is a **managed service by AWS** that helps you:

- Expose your APIs (your application’s endpoints) securely.
    
- Manage traffic, like controlling how many people can use your API at once.
    
- Authenticate users.
    
- Transform requests/responses (optional).
    

---

# So, where does my API code run?

Your actual **application code** — the logic of what your API does — has to run **somewhere**:

1. **On Lambda:**  
    Serverless compute that runs your code without you managing servers.
    
2. **On a server (EC2, VPS, or on-premises):**  
    Your own server or VM running an application (like Node.js, Python, Java, etc.).
    
3. **In a container (ECS, EKS):**  
    Docker containers running your app.
    

---

# Why do people often use API Gateway + Lambda?

Because:

- Lambda is **serverless** (no servers to manage).
    
- API Gateway is a **managed API front door**.
    
- Together, you get a **fully serverless API** that scales automatically.
    

---

# Can I use API Gateway without Lambda?

Yes! You can point API Gateway directly to:

- Your existing backend server.
    
- An HTTP endpoint anywhere on the internet.
    

API Gateway will **forward the request** to that server and return the response to the client.

---

# Simple analogy:

|Thing|What it is in real life|
|---|---|
|**API Gateway**|The receptionist/front desk|
|**Your backend API server**|The worker who does the actual job|
|**Lambda**|A robot worker who does a task quickly when asked|

API Gateway takes the request from the visitor and sends it either to:

- A **robot (Lambda)** that runs your code on demand, or
    
- A **worker (your server)** who does the job.
    

---

# Summary

- **API Gateway = Managed doorway for your API.**
    
- It **does NOT run your code**.
    
- Your code must run on Lambda or a server.
    
- API Gateway forwards client requests to Lambda or your backend.
    
- You can use API Gateway alone to **forward requests to your existing server** (no Lambda needed).