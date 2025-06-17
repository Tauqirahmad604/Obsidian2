##### TOPICS:
##### 1. EBS VOLUME
##### 2. DELETE ON TERMINATION
##### 3. EBS SNAPSHOT
##### 4. EBS VOLUME TYPES(GENERAL PURPOSE, PROVISION(IOPS))
##### 5. EBS MULTI ATTACH
##### 6. EBS ENCRYPTION





![[Pasted image 20241205175609.png]]


![[Pasted image 20241205180043.png]]


![[Pasted image 20241205180703.png]]



### EBS Snapshot Features

![[Pasted image 20241205181801.png]]


**Incremental Snapshots**: Archiving stores a **full copy** of the snapshot, even if the original snapshot was incremental. This makes the archived version much larger.

- Example: Incremental snapshots may occupy only 10 GB in the standard tier, but archiving them could result in a full 100 GB snapshot being stored, leading to higher costs.

## How It Works:

1. 📦 You take your **first snapshot** → it's a **full copy** of the entire EBS volume.
    
2. 🧩 You take a **second snapshot** → only the **blocks that changed** since the first snapshot are saved.
    
3. 📅 You take more snapshots → each one only saves the **changed blocks** since the previous snapshot.
    

So the size and duration of snapshots **decrease significantly** after the first full snapshot.


###   EBS Volume Types

![[Pasted image 20241205194819.png]]


![[Pasted image 20241205195334.png]]


![[Pasted image 20241205200201.png]]


![[Pasted image 20241205200429.png]]


### Summary

![[Pasted image 20241205200650.png]]


![[Pasted image 20241206211050.png]]


![[Pasted image 20241206211950.png]]



![[Pasted image 20241206212035.png]]



## Encryption at Rest vs Encryption in Transit

When securing cloud-based applications and data, it's important to understand the difference between **encryption at rest** and **encryption in transit**.

### ✅ Encryption at Rest

Encryption at rest refers to **protecting data while it is stored** on disk or in persistent storage. This ensures that if unauthorized access occurs (e.g., via stolen backups or compromised storage), the data remains unreadable.

**Examples:**

- Encrypted data stored in Amazon S3, RDS, or EBS volumes.
    
- AWS KMS used to manage and control encryption keys.
    

**Benefits:**

- Protects data from unauthorized access on physical media.
    
- Helps comply with security standards like GDPR, HIPAA, and PCI-DSS.
    

### ✅ Encryption in Transit

Encryption in transit protects data **while it is being transmitted** across networks. This ensures that any data moving between services, applications, or users is encrypted and cannot be intercepted or altered during transmission.

**Examples:**

- HTTPS communication using TLS (e.g., between a web client and a load balancer).
    
- TLS-enabled connections to databases like Amazon RDS or Aurora.
    
- Secure service-to-service communication within a VPC.
    

**Benefits:**

- Prevents data eavesdropping and man-in-the-middle attacks.
    
- Ensures confidentiality and integrity of data during transmission.