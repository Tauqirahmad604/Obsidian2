
1. Create a new secret manager ==MY_SECRET== and input the values of enviroment variables in the field of Secret values.

2. Go to the service account and add the role of ==Secret Manager Secret Accessor== in your service account.

3. Then run this command in your pipeline to access the enviroment variable added in the secret.

   - name: Build and push Docker image
        run: |
          CAPZULA_ENV=$(gcloud secrets versions access latest --secret="CAPZULA_ENV")
          echo "CAPZULA_ENV=$CAPZULA_ENV" > .env
          gcloud auth configure-docker us-west2-docker.pkg.dev --quiet
          docker build --build-arg CAPZULA_ENV="$CAPZULA_ENV" -t us-west2-docker.pkg.dev/capzula/capzula-repo/dev:GITHUB_SHA .
          docker push us-west2-docker.pkg.dev/capzula/capzula-repo/dev:$GITHUB_SHA
      

![[Screenshot from 2024-08-12 20-13-29.png]]
