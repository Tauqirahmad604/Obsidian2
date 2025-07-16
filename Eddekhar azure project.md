
1. Open the properties of existing machine

![[Pasted image 20240627124804.png]]

2. Take the snapshot of OLD VM to backup it with name of ==stagingbackend_1==.

3. Create a new vm in the new subscription with same resources and properties in this machine

4. Password and Username for the new create VM name with Stagingbackend-1.

   Username = ==Stagbackend==
   Password = ==Eddekar20%!@2030==
   Public IP = ==20.83.187.169==
   Private IP = ==10.0.0.4==
   SSH = ssh Stagbackend@20.83.187.169
   
   
5.  Subnet we used is

     ==subnet = 10.0.0.0/24==
     
6. Attached the Static IP in the network interface after creating 

7. Copy all DEV files from OLD VM to new VM from ==/var/www/html==.

```
sudo scp -r devapi devFront devLanding Stagbackend@20.83.187.169:/var/www/html
```

8. If it say permission denied then run this command to give permissions

```
sudo chown -R Stagbackend:Stagbackend /path/to/dir/
sudo chmod -R 755 /path/to/dir

```

10. Then install node,npm,nvm,pm2 .

11. To run ==devapi== which is backend.

```
   npm run dev
```

12. To check running ports
```
netstat -tlnp
```
13. To curl
```
curl -vl http://localhost:5173
```

14. To send files from remote vm to local machine. Run this command on local

```
sudo scp Stagbackend@20.83.187.169:/var/www/html/devapi.tar.gz /home/tauqir/Downloads
```

15. To send files from local to remote vm run this command on remote.

```
sudo scp -i ~/.ssh/id_rsa /home/tauqir/Downloads/jigsawproject/2206294394.zip
tauqir@35.185.88.231:/home/tauqir
```

16. To access virtaul machine with the SSH key

```
sudo ssh -i ~/.ssh/'ssh-key-2023-04-11 1.key' ubuntu@207.127.102.30
```
username = ualimaan
password = ualimaan&a77e 
IP= 20.21.144.95
SSh = ssh ualimaan@20.21.144.95


docker tag bedrock:latest us-west2-docker.pkg.dev/capzula/capzula-repo/bedrock:latest

docker push us-west2-docker.pkg.dev/capzula/capzula-repo/bedrock:latest  

