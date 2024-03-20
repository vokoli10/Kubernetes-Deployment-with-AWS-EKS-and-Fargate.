## STEP 2: KUBECTL, EKSCTL AND AWS CLI INSTALLATIONS.

Before we begin creating clusters on EKS, there are three prerequisites that are needed in order to interact with EKS.

- Kubectl: A command-line utility for managing Kubernetes clusters is called Kubectl. See Installing or upgrading Kubectl for further details. View [link](https://kubernetes.io/docs/tasks/tools/install-kubectl-linux/) for additional details.

After installation, to confirm the availability run the command:
 ```bash
  kubectl version --client
 ```

- Eksctl: A command-line utility that streamlines numerous repetitive chores when working with EKS clusters. 
Click the following [link](https://docs.aws.amazon.com/emr/latest/EMR-on-EKS-DevelopmentGuide/setting-up-eksctl.html) to view additional details.

After installtation, to confirm the availbility, run the command:
```bash
eksctl version
```

- AWSCLI: A command-line tool for working with AWS services, including Amazon EKS. For more information, see the [link](https://docs.aws.amazon.com/emr/latest/EMR-on-EKS-DevelopmentGuide/setting-up-cli.html) for installtion .

After installtion, to confirm the availability, run the command:
```bash
aws --version
```

After Instllation, it's important to configure the AWSCLI with your Access keys and Secret access keys. Run the command:
```bash
aws configure
```


  
