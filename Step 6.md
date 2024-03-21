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
Ensure you can see at least 2 pods are running in the aws-load-balancer-controller we just created. This simply means the aws-load-balancer-controller has acted upon the ingress services we had deployed earlier and can now be accessable by external users. Here is a screeenshot of mine:

![Image](https://i.imgur.com/tvp1xjd.png)


We can also verify through the GUI (AWS Console) whether the load balancer has been created by the aws-load-balancer-controller. If so, the Ingress services has an address and can now be reached externally.

![Image](https://i.imgur.com/KKAEPOu.png)


To verify this, we can copy the address on the ingress unto our browser.


![Ingress](https://i.imgur.com/y1I4AG4.png)

Yay! Users are able to access our application externally now that it is deployed.

Thank you for joining us on this journey to explore the power of AWS EKS with Fargate. We hope this guide has provided valuable insights and practical knowledge to help you succeed in your cloud-native endeavors.

PS: Remember to remove the cluster you made, or else you can continue to accrue charges. This is very important.
