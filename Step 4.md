## STEP 4: SETTING UP FARGATE PROFILE AND DEPLOYMENT.
Now, before we begin deployment, let's create a Fargate profile, preferably in our namespace; however, this could be done in your default namespace. 
Run the command below with your details.
```bash
eksctl create fargateprofile --cluster demo-cluster-1 --region us-east-1 --name alb-sample-app --namespace game-2048
```
 This program only uses the eksctl command in our previously stated cluster (demo-cluster-1) in region us-east-1 in our namespace (game-2048) to build a fargate profile. Once more, you are free to use the default namespace because it is not required. I do, however, much rather use my namespace.

Let's deploy our resources with the config yaml file in our repository. The config file as all the resources to be created including namspaces, deployment, services and Ingress. Run the command:
```bash
kubectl apply -f https://github.com/vokoli10/Kubernetes-Deployment-with-AWS-EKS-and-Fargate./blob/main/Config_2048.yaml
```
As you can see below, all the resources has been created. 

![image](https://i.imgur.com/nfYZP71.png)

Now all resources were created properly, as seen above, but however, for the ingress to work and function properly, it needs the ingress controller, and without this, the ingress is and will always be in a dead state. So basically, 4 out of the 4 resources were created, but 3 are running. All but ingress. Reason: There is no ingress-controller.
