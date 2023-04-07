# Build & Deploy the guestbook on IBM Cloud Container Registry
### Introduction to Containers w/ Docker, Kubernetes & OpenShift Course project

In this project it was required to
1.  Updation of the Dockerfile.
1.  The guestbook image being pushed to IBM Cloud Container Registry correctly.
1.  Index page of the deployed Guestbook – v1 application.
1.  Horizontal Pod Autoscaler creation. 
1.  The replicas in the Horizontal Pod Autoscaler being scaled correctly. 
1.  The Docker build and push commmands for updating the guestbook.
1.  Deployment configuration for autoscaling.
1.  Updated index page of the deployed Guestbook – v2 application after rollout of the deployment.
1.  The revision history for the deployment after rollout of the deployment.
1. The udpated deployment after Rollback of the update. 


## Verify the environment and command line tools

1. Open a terminal & make a new folder
```shell
mkdir project
```

2. Clone the git repository that contains the artifacts needed for this lab.
```shell
[!-d'guestbook'] && git clone https://github.com/ibm-developer-skills-network/guestbook
```

3. Change to the directory for this project
```shell
cd guestbook
```

## Build the guestbook app

1. Change to the v1/guestbook directory.
```shell
cd v1/guestbook
```

2. Export your namespace as an environment variable so that it can be used in subsequent commands.
```shell
export MY_NAMESPACE=sn-labs-$USERNAME
```

3. Build the guestbook app using the Docker Build command.
```shell
docker build . -t us.icr.io/$MY_NAMESPACE/guestbook:v1 
```

4. Push the image to IBM Cloud Container Registry.
```shell
 docker push us.icr.io/$MY_NAMESPACE/guestbook:v1
```
5. Verify that the image was pushed successfully.
```shell
ibmcloud cr images
```

6. Apply the deployment using:
```shell
kubectl apply -f deployment.yml
```

7. Open a New Terminal and enter the below command to view your application:
```shell
kubectl port-forward deployment.apps/guestbook 3000:3000
```
8. Launch your app