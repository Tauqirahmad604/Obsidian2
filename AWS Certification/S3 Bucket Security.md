![[Pasted image 20241214012811.png]]


![[Pasted image 20241214012938.png]]




![[Pasted image 20241214013110.png]]




![[Pasted image 20241214013240.png]]



- AWS KMS has limits on the number of requests you can make per second, which could be a concern for high-throughput workloads. The default limits are:
    - **5,000 requests per second** for encryption and decryption operations.
    - **100 requests per second** for other operations like creating or disabling keys.
- You can request an increase in these limits, but it may not always be suitable for extremely high-volume applications.




![[Pasted image 20241214013740.png]]



![[Pasted image 20241214013941.png]]



![[Pasted image 20241214014406.png]]



![[Pasted image 20241214014503.png]]



![[Pasted image 20241216232215.png]]




### What is CORS?

**CORS** (Cross-Origin Resource Sharing) is a security feature implemented by web browsers to prevent websites from making requests to a different domain (or origin) than the one the page was loaded from.

For example, if your website (`www.mywebsite.com`) tries to fetch data from a different website (like `www.s3bucket.com`), the browser might block this request to protect user data.

However, sometimes you **want** your website to interact with data from another domain (like fetching an image from Amazon S3). That's where **CORS** comes in! It lets you control which websites are allowed to access your data.

### Why Use CORS in S3?

When you store data in **Amazon S3** (like images, videos, or files), and you want to let other websites or applications access this data, you need to configure **CORS** in S3 to allow them to do that.

For example, if you have a **website hosted at `www.mywebsite.com`** and your images are stored in **S3**, you need CORS to allow `www.mywebsite.com` to access those images.



![[Pasted image 20241216232658.png]]



![[Pasted image 20241216232836.png]]



![[Pasted image 20241216233918.png]]



![[Pasted image 20241216233957.png]]



![[Pasted image 20241216234713.png]]



![[Pasted image 20241216234934.png]]



![[Pasted image 20241216235140.png]]



**Amazon S3 Glacier Lock** is a feature that allows you to **lock your data** in Amazon S3 Glacier Vaults using a **"write-once-read-many" (WORM)** model. This ensures that data cannot be **deleted** or **modified** for a specified period of time, which is useful for regulatory compliance, data retention, and archiving purposes.


![[Pasted image 20241216235444.png]]



## **Governance Mode**

- **Description**: Governance Mode allows you to protect objects from being deleted or modified, but authorized users (with special permissions) can **bypass** the lock to delete or update the objects if needed.


## **Compliance Mode**

- **Description**: Compliance Mode is **strict** and ensures that no one, including the **root user** or AWS administrators, can modify or delete an object until the retention period expires.



![[Pasted image 20241217000444.png]]




![[Pasted image 20241217000556.png]]







