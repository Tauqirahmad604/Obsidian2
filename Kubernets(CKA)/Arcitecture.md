
![[Pasted image 20250114000246.png]]



![[Pasted image 20250114004924.png]]



![[Pasted image 20250114005251.png]]



![[Pasted image 20250114012742.png]]



![[Pasted image 20250114012806.png]]



![[Pasted image 20250114013028.png]]


![[Pasted image 20250114013933.png]]


**Controller Manager**


![[Pasted image 20250114014354.png]]


![[Pasted image 20250114014722.png]]


![[Pasted image 20250114014819.png]]



![[Pasted image 20250114014928.png]]




kubectl exec -it php-7f47db95f7-fs969 -n pimcore -- bash -c "rm -rf /tmp && mkdir -p /tmp && chmod 777 /tmp"

kubectl exec -it php-7f47db95f7-fs969 -n pimcore -- bash -c "mkdir -p /var/tmp && chmod 777 /var/tmp && TMPDIR=/var/tmp apt update && TMPDIR=/var/tmp apt install -y php-imagick"


kubectl exec -it php-7f47db95f7-fs969 -n pimcore -- bash -c "cd /var/www/html && vendor/bin/pimcore-install --mysql-host-socket=pimcore-db --mysql-username=pimcore --mysql-password=pimcore --mysql-database=pimcore"


kubectl exec -it php-7f47db95f7-fs969 -n pimcore -- bash -c "mkdir -p /var/www/html/var/cache/dev && chown -R www-data:www-data /var/www/html/var && chmod -R 775 /var/www/html/var"


Now listen to my problem carefully I am running pod of pimcore but the issue is that I have to mannually copy my entire code in the running pod and manually after going inside the pod I need to run










