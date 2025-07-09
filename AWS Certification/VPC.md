I have created vpc with /30 cidr what will happen?


![[Pasted image 20250101192921.png]]



![[Pasted image 20250101195219.png]]



![[Pasted image 20250101204039.png]]



![[Pasted image 20250101204942.png]]



![[Pasted image 20250101205101.png]]



![[Pasted image 20250101205317.png]]



![[Pasted image 20250101210942.png]]



![[Pasted image 20250101211944.png]]



![[Pasted image 20250101212541.png]]



![[Pasted image 20250101214409.png]]


![[Pasted image 20250101215412.png]]



![[Pasted image 20250101215534.png]]



![[Pasted image 20250101220026.png]]



![[Pasted image 20250101220214.png]]



![[Pasted image 20250101220255.png]]

It **translates** the private IP of the instance to its own public IP for outbound traffic.

![[Pasted image 20250101222525.png]]

### **Scenario: Client-Server Communication**

1. **Your Browser as the Client**:
    
    - You type `http://example.com` into the browser.
    - Your computer sends a request to the server hosting `example.com` over the Internet.
    - The server is listening on a **well-known port**, such as **port 80** (for HTTP).
2. **Operating System Assigns an Ephemeral Port**:
    
    - Your computer's operating system dynamically assigns a temporary **ephemeral port** (e.g., **port 49152**) for this outgoing connection.
    - The request is sent from your computer's ephemeral port **49152** to the server's well-known port **80**.
3. **The Server Responds**:
    
    - The server receives your request and sends a response (e.g., the webpage data) back to your computer.
    - The response is sent to your computer’s ephemeral port **49152**, which the operating system has opened for this purpose.
4. **Connection Closes**:
    
    - Once the data transfer is complete, the ephemeral port **49152** is closed, and the operating system makes it available for other processes.



![[Pasted image 20250101222721.png]]




### **Key Points About Stateful Firewalls**:

1. **Stateful Behavior**:
    
    - Most firewalls and security groups are stateful, meaning they track connections.
    - When a connection is initiated, return traffic is allowed automatically, regardless of the ephemeral port.
2. **Stateless Behavior**:
    
    - If a firewall or NACL is stateless, you would need to explicitly allow return traffic on ephemeral ports (e.g., `32768-65535`).


![[Pasted image 20250101223314.png]]


![[Pasted image 20250101223514.png]]


![[Pasted image 20250101225205.png]]


![[Pasted image 20250101225559.png]]


![[Pasted image 20250101230037.png]]


![[Pasted image 20250101232508.png]]


![[Pasted image 20250101232651.png]]



![[Pasted image 20250101232814.png]]
