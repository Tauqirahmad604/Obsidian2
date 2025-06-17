
1. Route53 - Hosted zones
2. Route53 - TTL
3. CNAME v ALIAS
4. Route53 - Routing Policing
5. How to migrate domain from one provider to other





![[Pasted image 20241212230247.png]]


![[Pasted image 20241212230705.png]]



![[Pasted image 20241212231006.png]]




![[Pasted image 20241212231315.png]]


![[Pasted image 20241212233815.png]]



![[Pasted image 20241213012323.png]]



![[Pasted image 20241213012536.png]]


![[Pasted image 20241213012643.png]]


![[Pasted image 20241213013946.png]]


### 1. Simple Routing Policy

Routes traffic to a single resource (like one server or IP). Used when you have only one endpoint.

---

### 2. Weighted Routing Policy

Distributes traffic across multiple resources based on set weights (e.g., 70% to server A, 30% to server B).

---

### 3. Latency-based Routing Policy

Routes users to the region that provides the lowest latency (fastest response time) based on their location.

---

### 4. Failover Routing Policy

Routes traffic to a primary resource and switches to a backup if the primary becomes unhealthy.

---

### 5. Geolocation Routing Policy

Routes traffic based on the geographic location of the user (e.g., users in the US go to a US server).

---

### 6. Geoproximity Routing Policy

Routes traffic based on the user’s proximity to a resource and can shift traffic using a bias value (requires Traffic Flow).

---

### 7. Multi-value Answer Routing Policy

Returns multiple healthy records to the user, acting like basic DNS-based load balancing.