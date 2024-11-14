gcloud projects list

gcloud config set project capzula

gcloud container clusters get-credentials capzula-dev --region us-west2-a

kubectl get svc -n traefik

docker tag bedrock:latest us-west2-docker.pkg.dev/capzula/capzula-repo/bedrock:latest

docker push us-west2-docker.pkg.dev/capzula/capzula-repo/bedrock:latest

kubectl -n argocd get secret argocd-initial-admin-secret -o jsonpath="{.data.password}" | base64 -d

ARGOCD

username=admin
password=mJG3gTw8YmnbLS13

kubectl port-forward service/argocd-server -n argocd 8081:443

Yesterday

1. Cluster Setup k8s standard
2. disabled logs on cluster which can cause price issue
3. analysis of code on local
4. Configured github action pipeline
5. Service account setup
6. Service account key creation and permission setup
7. Service account key useage
8. GCP project id for github actions
9. Service account store as secret in github

Today

1. Created dev branch in the github bedrock-php repo
2. Created gcp artifact registory
3. Push docker image to the artifact registory
4. Setup traefik via helm as load balancer 
5. Setup argocd via helm
6. Created argocd repository in the github
7. Connected agrocd with github new repo argocd
8. Created 3 namespaces with dev, QA and prod
9. Work in progress with helm chart

eiCYc4ErG4%5DnMrXC(YGSRh

WORDPRESS

username= root
password= pak16073.


name: Deploying to production
on:
  push:
    branches:
      - main
  workflow_dispatch:
jobs:
  build-and-push:
    runs-on: ubuntu-20.04
    
    steps:
    - name: Checkout repository
      uses: actions/checkout@v2
    - name: Set up Google Cloud SDK
      uses: google-github-actions/setup-gcloud@v0.4.0
      with:
          service_account_key: ${{ secrets.GKE_SA_KEY }}
          project_id: ${{ secrets.GKE_PROJECT }}
          export_default_credentials: true
    - name: Build and push Docker image
      run: |
        gcloud auth configure-docker us-west2-docker.pkg.dev --quiet
        docker build -t us-west2-docker.pkg.dev/capzula/capzula-repo/test:1 .
        docker push us-west2-docker.pkg.dev/capzula/capzula-repo/test:1



1. create 3 name spaces (dev, qa, main/prod)
2. change configuration name to capzula
3. dev.capzula.com
4. store secret in dev namespace from service account key
5. manual deploy application on argocd

http://localhost:8080/wp/wp-login.php


kubectl port-forward svc/my-app-service 8080:80 -n dev

helm lint

kubectl exec -it -n dev redis-ccdb788b7-nrwzw -- /bin/sh

redis-cli -h localhost -p 6379

curl redis-dev:6379

[http://redis-dev.dev.svc.cluster.local:6379](http://redis-dev.dev.svc.cluster.local/)

kubectl port-forward svc/rabbitmq 15672:15672 -n dev

http://rabbitmq.dev.svc.cluster.local:5672

http://34.94.130.199:15672/

kubectl port-forward capzula-deployment2-6cd9b45597-5fks5 80:9000 -n dev

kubectl exec -it rabbitmq-746846cdf6-j7rdd -n dev -- printenv


kubectl exec -it redis-ccdb788b7-przs5 -n dev -- redis-cli ping


rabbitmy-dev.dev.svc.cluster.local 5672

telnet rabbitmq-dev.dev.svc.cluster.local 5672

telnet 34.118.233.95 5672

http node 

telnet redis.dev.svc.cluster.local 6379

telnet 34.118.230.106 6379

kubectl exec -it preview-dev-deployment-647dd65cd9-wtvlf -- printenv | grep REDIS

redis-cli -h redis.dev.svc.cluster.local -p 6379


kubeadm join 192.168.131.128:6443 --token ujm2eo.laaydeu01g9568fa \
	--discovery-token-ca-cert-hash sha256:ba7bccc0117d6be6395742e193f6790f0b7125a2224890da302c033bf32d1e53