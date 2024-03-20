## STEP 5: IAM OIDC PROVIDER.
- AWS ALB Ingress Controller is a specific implementation of an Ingress Controller designed to work with AWS's Application Load Balancer (ALB).
- It integrates Kubernetes ingress resources with AWS ALBs, allowing Kubernetes services to be exposed via ALBs.
- The AWS ALB Ingress Controller specifically provisions ALBs on AWS and configures them based on the Ingress resources defined in your Kubernetes cluster.

However, for the AWS ALB Ingress controller that is running needs to access the application load balancer. It needs to have IAM integrated, and to do this, we can use the IAM OIDC provider.

The AIM OIDC provider is crucial when setting up IAM roles for service accounts in AWS EKS, as it defines the OIDC provider that AWS will use for authentication and token validation within your Kubernetes cluster. 

To Run the command:
```bash
eksctl utils associate-iam-oidc-provider --cluster demo-cluster-1 --approve
```
This created the IAM and connected it to the cluster the OIDC provider.

Returning to our ALB controller, we would like to provide access to a pod in Kubernetes to access several AWS services, including the Application Load Balancer.
This will require IAM roles and policies because it needs to communicate with AWS APIs. 
Let's download the IAM policy using the command below:
```bash
curl -O https://raw.githubusercontent.com/kubernetes-sigs/aws-load-balancer-controller/v2.5.4/docs/install/iam_policy.json
```
The IAM policy has the necessary permission. You can check the file on you browser before downloading on your console.

After downloading the IAM Policy, you can create a policy named AWSLoadBalancerControllerIAMPolicy using the command:
```bash
aws iam create-policy --policy-name AWSLoadBalancerControllerIAMPolicy --policy-document file://iam_policy.json
```

Now using the IAM role we'll create a service account and attaches it to the policy we just created. Run the command below.
```bash
eksctl create iamserviceaccount \
  --cluster=demo-cluster-1 \
  --namespace=kube-system \
  --name=aws-load-balancer-controller \
  --role-name AmazonEKSLoadBalancerControllerRole \
  --attach-policy-arn=arn:aws:iam::<your-aws-account-id>:policy/AWSLoadBalancerControllerIAMPolicy \
  --approve
```


