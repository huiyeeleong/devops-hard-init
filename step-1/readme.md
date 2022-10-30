When running EKS, it requires specific networking. Because all environments will most likely be different, there's a CloudFormation template for this exact purpose.

To create your cluster VPC with public and private subnets

Open the AWS CloudFormation console at https://console.aws.amazon.com/cloudformation.

From the navigation bar, select a Region that supports Amazon EKS.

Choose Create stack, With new resources (standard).

For Choose a template, select Specify an Amazon S3 template URL.

Paste the following URL into the text area and choose Next:

https://s3.us-west-2.amazonaws.com/amazon-eks/cloudformation/2020-10-29/amazon-eks-vpc-private-subnets.yaml
On the Specify Details page, fill out the following:
Stack name: Choose a stack name for your AWS CloudFormation stack. For example, you can call it eks-vpc.

VpcBlock: Choose a CIDR range for your VPC. Each worker node, pod, and load balancer that you deploy is assigned an IP address from this block. The default value provides enough IP addresses for most implementations, but if it doesn't, then you can change it. For more information, see VPC and subnet sizing in the Amazon VPC User Guide. You can also add additional CIDR blocks to the VPC once it's created.

PublicSubnet01Block: Specify a CIDR block for public subnet 1. The default value provides enough IP addresses for most implementations, but if it doesn't, then you can change it

PublicSubnet02Block: Specify a CIDR block for public subnet 2. The default value provides enough IP addresses for most implementations, but if it doesn't, then you can change it

PrivateSubnet01Block: Specify a CIDR block for private subnet 1. The default value provides enough IP addresses for most implementations, but if it doesn't, then you can change it

PrivateSubnet02Block: Specify a CIDR block for private subnet 2. The default value provides enough IP addresses for most implementations, but if it doesn't, then you can change it

(Optional) On the Options page, tag your stack resources. Choose Next.

On the Review page, choose Create.

When your stack is created, select it in the console and choose Outputs.

Record the SecurityGroups value for the security group that was created. When you add nodes to your cluster, you must specify the ID of the security group. The security group is applied to the elastic network interfaces that are created by Amazon EKS in your subnets that allows the control plane to communicate with your nodes. These network interfaces have Amazon EKS in their description.

Record the VpcId for the VPC that was created. You need this when you launch your node group template.

Record the SubnetIds for the subnets that were created and whether you created them as public or private subnets. When you add nodes to your cluster, you must specify the IDs of the subnets that you want to launch the nodes into.