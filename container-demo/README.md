
## Build a VPC, ECS Cluster, and ALB:
![infrastructure](images/private-subnet-public-lb.png)
```
cd ~/environment/container-demo

aws cloudformation deploy --stack-name container-demo --template-file cluster-fargate-private-vpc.yml --capabilities CAPABILITY_IAM
aws cloudformation deploy --stack-name container-demo-alb --template-file alb-external.yml
```
At a high level, we are building what you see in the diagram. We will have 3 
availability zones, each with a public and private subnet. The public subnets
will hold service endpoints, and the private subnets will be where our workloads run.
Where the image shows an instance, we will have containers on AWS Fargate.
