## STEP 3: CLUSTER CONFIGURATION.
Now let's create our cluster. Search for EKS on the AWS Console and click on clusters. Now, in order to create it, there are lots of parameters to be included, as you can on the left panel. There should be somewhat easier way to do this.
One of the most preferred ways to create a cluster in an organization is using the eksctl. This is a command-line utility used to manage eks clusters. This was one of the prerequites we install in step 2.
Run the command:
``` bash
eksctl create cluster --name demo-cluster-1 --region us-east-1 --fargate
```
This simply mean we are creating a cluster with the name demo-cluster-1 in us-east-1 region using fargate. Fargate preety much does the handling of creating the VPC, NAT gateway, Subntes, Elastic Ip, Network Interfaces etc.

This usually takes 15–20 minutes depending on your internet connection, among other things, so exercise a bit of patience here as the cluster is being built. After setting up the cluster, you can also check the GUI (AWS Console) for confirmation.

Cluster has beeen setup. Now how do we interact with it like we always do via the CLI to check our Deployments, Pods, and services. 
To do this, we have to update our kubeconfig file, we can then access our cluster via the CLI instead of the GUI. Run the command below to update the config file.
```bash
aws eks update-kubeconfig --name demo-cluster-1 --region us-east-1
```
