Deploy The Uber App
Once the EKS cluster is built and the Kubernetes manifest is ready, you're now ready to deploy the Kubernetes manifest.

cd into the kubernetes_manifest directory
Run the following command: kubectl create -f deployment.yml
You'll see an output that specifies the service and deployment was created.

Run the following command to confirm that the deployment was successful: kubectl get deployments