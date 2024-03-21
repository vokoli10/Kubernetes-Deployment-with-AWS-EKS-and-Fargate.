## STEP 6: AWS-LOAD-BALANCER-CONTROLLER.
Now, going back to the AWS-LOAD-BALANCER CONTROLLER we spoke about earlier, we are going to use helm charts to create the ALB controller and use the service account to run the pod. To add the Helm chart repository, run the command:
```bash
helm repo add eks https://aws.github.io/eks-charts
```
After adding, we then update the repository using the command below:
```bash
helm repo update eks
```
Now let's install the helm chart using the command below. Please make the appropriate modifications, such as vpcId, region, and clustername.
```bash
helm install aws-load-balancer-controller eks/aws-load-balancer-controller -n kube-system --set clusterName=demo-cluster-1  --set
serviceAccount.create=false  --set serviceAccount.name=aws-load-balancer-controller --set region=us-east-1 --set vpcId=0a1e98bf27f98a279
```
If you have done all the step as required, after running the previous command, you'd get the message saying: the AWS Load Balacer controller installed!

Now that this load balancer has been installed and is operational, make sure that at least two replicas are up and running. 
Anything besides this, we will have to troubleshoot. Use the following command to verify that two replicas are operating in two different AZs at minimum:
```bash
kubectl get deploy -n kube-system
```
As you can see below, at least 2 pods are running in the aws-load-balancer-controller we just created.
![Image Description](https://imgur.com/KKAEPOu)   ![Image Description](https://imgur.com/KKAEPOu)

![Image](https://imgur.com/tvp1xjd)



We can now verify through the GUI (AWS Console) whether the load balancer has been built by the aws-load-balancer-controller. 
The load balancer has been created, as can be seen below.






![Ingress](https://i.imgur.com/y1I4AG4.png)
