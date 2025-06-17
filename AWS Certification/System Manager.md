
![[Pasted image 20250528163433.png]]



![[Pasted image 20250528164546.png]]



Without Systems Manager:

- You SSH into each EC2 instance one by one to update a package.
    
With Systems Manager (at scale):

- You send a command via SSM **once**, and it runs on **all 500 EC2 instances** automatically.




### **What You Can Manage with AWS Systems Manager:**

| Resource Type           | Can Be Managed? | Notes                                                     |
| ----------------------- | --------------- | --------------------------------------------------------- |
| **EC2 instances**       | ✅ Yes           | Most common use (Linux & Windows)                         |
| **On-premises servers** | ✅ Yes           | You can register them using **SSM Agent + Activation**    |
| **VMs in other clouds** | ✅ Yes           | Like VMs in Azure or GCP, if configured with SSM agent    |
| **Edge devices / IoT**  | ✅ Yes           | As long as they support SSM agent and have connectivity   |
| **ECS containers**      | 🟡 Partially    | Some integration possible via tasks and parameter store   |
| **EKS (Kubernetes)**    | 🟡 Partially    | Use Systems Manager Parameter Store & Secrets integration |