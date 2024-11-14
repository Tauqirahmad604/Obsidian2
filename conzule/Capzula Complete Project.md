
1. Create kubernetes Cluster with two nodes.

2. Install traefik and argocd on it with the help of files shared by ustad ahmad

3. Run a deployment and service with type loadbalancer of argocd and expose it outside

4. Now access the argocd with the Domain name you gave.

5. Configure argocd with the repository of github to do this follow following setup

![[Pasted image 20240826182629.png]]

6. Go to repositories section in the argocd

![[Pasted image 20240826182846.png]]

7. Click on (connect repo using ssh).

8. ![[Pasted image 20240826183100.png]]

9. Here write the information as needed. SSH repo url of argocd repository. Create SSH key in your local keep that public key in the ==Deploy Key== section in github repository and private key on here in ArgoCD.

10. Use ECDSA key for use do not use RSA key it will not work.

11. It will connected successfully.

12. To connect and run pipeline successfully store you variable the the Secret and Variable as actions .

![[Pasted image 20240826184054.png]]

13. Here Store Your Project name and gcp service account private key which is in the json format we have store before and github token.

14. Given are the permissions which you have to turn on in the Service Account.


- Artifact Registry Administrator
    
- Cloud SQL Client
    
- Secret Manager Secret Accessor
    
- Storage Admin

![[Pasted image 20240826184652.png]]

