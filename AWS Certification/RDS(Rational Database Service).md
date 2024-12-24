
2. RDS proxy
3. RDS custom
4. Amazon Aurora
5. Proxy fleet - Aurora
6. Aurora - Custom Endpoints
7. Aurora - Serverless
8. Global Aurora
9. RDS Backup
10. Aurora Database Cloning
11. RDS & Aurora Security
12. ElastiCache 
13. ElastiCache Security
14. ElasticCache Session Store





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



![[Pasted image 20241212003236.png]]


![[Pasted image 20241212005642.png]]


![[Pasted image 20241212005831.png]]



![[Pasted image 20241212005923.png]]



![[Pasted image 20241212013124.png]]



![[Pasted image 20241212013311.png]]



![[Pasted image 20241212013541.png]]



![[Pasted image 20241212184107.png]]

![[Pasted image 20241212184927.png]]

![[Pasted image 20241212190347.png]]

![[Pasted image 20241212191014.png]]

### **Replication**

Replication refers to the continuous process of copying data from one database (source) to another (target) in real time or near real time. It ensures that the target database is up-to-date with changes in the source.

### **Cloning**

Cloning refers to creating an exact, one-time copy of an existing database or dataset at a specific point in time. It is not continuous like replication.

![[Pasted image 20241212191742.png]]

![[Pasted image 20241212192314.png]]



![[Pasted image 20241212200110.png]]


![[Pasted image 20241212200236.png]]


![[Pasted image 20241212210254.png]]


![[Pasted image 20241212210628.png]]



![[Pasted image 20241212221653.png]]



![[Pasted image 20241212221827.png]]

![[Pasted image 20241212222001.png]]