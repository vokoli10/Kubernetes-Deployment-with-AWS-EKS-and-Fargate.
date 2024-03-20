## STEP 4: SETTING UP FARGATE PROFILE AND DEPLOYMENT.
Now, before we begin deployment, let's create a Fargate profile, preferably in our namespace; however, this could be done in your default namespace. 
Run the command below with your details.
```bash
eksctl create fargateprofile --cluster demo-cluster-1 --region us-east-1 --name alb-sample-app --namespace game-2048
```
This command simply creates a fargate profile using the eksctl command in our cluster created earlier (demo-cluster-1) in region us-east-1 in our namespace (game-2048)
Again, you can use the default namespace as it's not necessary. However, i prefer using my namespace. 
