![[Pasted image 20241031180720.png]]

#### User Data Key Points


EC2 doesn't know what the user data contains, it's just a block of data.

The user data is not secure, anyone can see what gets passed in. For this reason it is important not to pass passwords or long term credentials.

User data is limited to 16 KB in size. Anything larger than this will need to pass a script to download the larger set of data.

User data can be modified if you stop the instance, change the user data, then restart the instance.

The contents are only excecuted once at launch.

![[Pasted image 20241031181608.png]]



![[Pasted image 20241031190754.png]]

#### General Purpose

![[Pasted image 20241031191104.png]]


#### Compute Optimized

![[Pasted image 20241031191304.png]]


#### MEMORY Optimized

![[Pasted image 20241031191545.png]]


#### Storage Optimized

![[Pasted image 20241031192346.png]]




#### SECURITY GROUP

If we create a security group and attach it to an EC2 instance, then create another security group for a different instance, we can specify the first security group as a source in the second one to allow them to communicate with each other.



![[Pasted image 20241031212241.png]]



/project/git/mojo-keystone
tail -f /opt/bitnami/apache2/logs/test-app-error.log
cat /opt/bitnami/apache2/conf/extra/httpd-vhosts.conf
