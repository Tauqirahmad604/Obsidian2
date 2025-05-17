
1. RDS proxy(connection pooling)
2. RDS custom
3. Amazon Aurora
4. Proxy fleet - Aurora
5. Aurora - Custom Endpoints
6. Aurora - Serverless
7. Global Aurora
8. RDS Backup
9. Aurora Database Cloning
10. Aurora Backtraking
11. RDS & Aurora Security
12. ElastiCache 
13. ElastiCache Security
14. ElasticCache Session Store
15. Option group and Parameter group
16. AWS Database Migration Service (AWS DMS)
17. Kerberose authentication





![[Pasted image 20241211175933.png]]

![[Pasted image 20241211183004.png]]



![[Pasted image 20241211184234.png]]




### **Key Features of RDS Read Replicas**

1. **Replication**:
    
    - RDS automatically replicates data from the source database (primary instance) to the read replica using asynchronous replication.
    - Any changes made to the primary database are propagated to the replicas.
2. **Read-Only**:
    
    - Replicas can only process read operations like `SELECT` queries, not write operations (`INSERT`, `UPDATE`, or `DELETE`).
3. **Scalability**:
    
    - Useful for applications with high read demands, as you can distribute the read workload across replicas.
4. **High Availability**:
    
    - In some cases, read replicas can also be promoted to standalone databases in the event of a failure in the primary database.
5. **Multi-Region Availability**:
    
    - You can create read replicas in the same AWS Region or in different Regions for **disaster recovery** and to serve read traffic closer to end users.

![[Pasted image 20241211185930.png]]



![[Pasted image 20241211190112.png]]



![[Pasted image 20241211191158.png]]



![[Pasted image 20241211193439.png]]


![[Pasted image 20241212001301.png]]

### **Amazon RDS vs. Custom RDS (Self-Managed Database on EC2)**

Amazon **RDS (Relational Database Service)** is a **fully managed** database service, whereas **Custom RDS** refers to **self-managing a database on an EC2 instance**. Here’s a detailed comparison:

---

## **1️⃣ Overview**

| Feature                    | **Amazon RDS (Managed Service)**                                | **Custom RDS (Self-Managed on EC2)**                        |
| -------------------------- | --------------------------------------------------------------- | ----------------------------------------------------------- |
| **Management**             | Fully managed by AWS                                            | You manage everything                                       |
| **Database Setup**         | AWS handles provisioning, patching, and updates                 | You install, configure, and maintain the DB manually        |
| **Backup & Recovery**      | Automated backups, snapshots, and point-in-time recovery (PITR) | Manual setup for backups & disaster recovery                |
| **Scaling**                | Vertical & horizontal scaling via AWS                           | Manual scaling (resize EC2, configure replication)          |
| **High Availability (HA)** | Built-in Multi-AZ support                                       | You must configure HA (e.g., clustering, replication)       |
| **Monitoring & Logs**      | AWS CloudWatch, Performance Insights                            | Requires custom monitoring (e.g., Prometheus, Grafana)      |
| **Security**               | Encryption, IAM authentication, AWS Secrets Manager             | Manual setup (SSL, IAM, Firewalls)                          |
| **Database Engines**       | MySQL, PostgreSQL, SQL Server, MariaDB, Oracle, Aurora          | Any database (including MongoDB, Cassandra, etc.)           |
| **Maintenance**            | AWS applies patches and updates                                 | You must handle updates manually                            |
| **Customization**          | Limited OS & DB tuning options                                  | Full control over OS, DB configurations, and versions       |
| **Cost**                   | Pay-as-you-go pricing (storage + compute)                       | EC2 pricing (can be cheaper but requires management effort) |


![[Pasted image 20241212003236.png]]

### **What is Proxy Fleet in Amazon Aurora?**

#### **📌 Definition:**

A **Proxy Fleet** in **Amazon Aurora** refers to **Aurora's built-in connection pooling mechanism** that manages and scales database connections efficiently. It acts like **Amazon RDS Proxy** but is **fully integrated into Aurora**, reducing the need for an external proxy service.

---

### **🔹 Why is Proxy Fleet Needed?**

Traditional database connections are **expensive** because each connection consumes memory and CPU. **Applications that frequently open and close connections** (e.g., web apps, microservices, AWS Lambda functions) create **connection overload**.

💡 **Aurora's Proxy Fleet optimizes connection handling** by:

- Pooling and reusing database connections.
- Automatically managing connections without manual tuning.
- Reducing overhead and improving query performance.


![[Pasted image 20241212005642.png]]


![[Pasted image 20241212005831.png]]



![[Pasted image 20241212005923.png]]



![[Pasted image 20241212013124.png]]



![[Pasted image 20241212013311.png]]



![[Pasted image 20241212013541.png]]


**Amazon Aurora Global Database** is a **highly available, globally distributed database** that allows you to deploy **a single Aurora database across multiple AWS Regions**. It provides **low-latency global reads** and **fast cross-region disaster recovery**.

## **How Aurora Global Database Works?**

1. **Primary Region (Leader)**
    - Handles **read and write** operations.
    - Syncs data asynchronously to read-only **secondary regions**.
2. **Secondary Regions (Followers)**
    - Handle **read-only queries** to reduce latency for global users.
    - Can be **promoted** to primary in case of failover.
3. **Replication Mechanism**
    - Aurora **Global Replication** is faster than standard MySQL/PostgreSQL replication.
    - Uses **dedicated infrastructure** for replication to **avoid affecting primary DB performance**.


![[Pasted image 20241212184107.png]]

![[Pasted image 20241212184927.png]]

![[Pasted image 20241212190347.png]]


![[Pasted image 20241212191014.png]]

### **Replication**

Replication refers to the continuous process of copying data from one database (source) to another (target) in real time or near real time. It ensures that the target database is up-to-date with changes in the source.

### **Cloning**

Cloning refers to creating an exact, one-time copy of an existing database or dataset at a specific point in time. It is not continuous like replication.



## **Aurora Backtracking – Instant Point-in-Time Recovery**

### **📌 What is Aurora Backtracking?**

Aurora **Backtracking** allows you to **rewind** your Aurora **MySQL database** to a previous point **without restoring from a backup**. Instead of restoring from a snapshot, Aurora keeps track of changes and allows you to "go back in time" almost instantly.

💡 **Think of it like an "Undo" button for your database!**



![[Pasted image 20241212191742.png]]

![[Pasted image 20241212192314.png]]



![[Pasted image 20241212200110.png]]


![[Pasted image 20241212200236.png]]


![[Pasted image 20241212210254.png]]


![[Pasted image 20241212210628.png]]



![[Pasted image 20241212221653.png]]



![[Pasted image 20241212221827.png]]

![[Pasted image 20241212222001.png]]



![[Pasted image 20250305203452.png]]



![[Pasted image 20241231233920.png]]



![[Pasted image 20241231234220.png]]



## How RDS Failover Works (Without RDS Proxy)

### 1. **Multi-AZ Deployment Setup**

- When you enable **Multi-AZ** during RDS setup, AWS automatically creates a **standby replica** of your primary DB instance in a different **Availability Zone (AZ)**.
    
- The standby is **not readable or writable** — it's kept **in sync** with the primary using synchronous replication.
    

---

### 2. **What Triggers Failover?**

AWS automatically initiates failover in cases such as:

- Primary DB instance crash
    
- Hardware failure
    
- AZ outage
    
- Manual reboot with failover
    
- OS patching or maintenance events
    

---

### 3. **What Happens During Failover?**

- AWS **promotes the standby replica** to become the **new primary**.
    
- A new **standby is automatically created** in another AZ (if Multi-AZ is still enabled).
    
- **DNS endpoint remains the same** (e.g., `mydb.xxxxxxxxx.us-east-1.rds.amazonaws.com`), but it now points to the **new primary**.
    

---

### 4. **Client Connection Behavior**

- Because the endpoint stays the same, the app can reconnect **without needing to change the connection string**.
    
- However, the **application must handle connection interruptions** gracefully — failover usually takes **30–60 seconds**.