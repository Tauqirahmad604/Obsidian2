If you do not explicitly attach an ENI to your EC2 instance, **AWS automatically creates and attaches a primary ENI** when the instance is launched.

It allows the instance to communicate within the VPC and, if configured, with the internet or other networks.

ENI EC2 instance ko **VPC (Virtual Private Cloud)** ke network se connect karta hai.  
Yeh instance ko private ya public communication ke liye enable karta hai, depending on configuration