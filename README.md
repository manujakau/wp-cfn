# WordPress CloudFormation Templates

## WordPress Stack Infrastructure

![WordPress](https://user-images.githubusercontent.com/44127516/100315512-6d11aa80-2fc1-11eb-9044-0796ba89f0d1.jpg)

diagram keys:
  IGW - Internet Gateway, 
  ALB - Application Load Balancer, 
  NAT GW - Nat Gateway, 
  ASG - Auto Scaling Group, 
  AZ0-1 - Availability Zone 1 & 2
  
Resource Aspects within Code:

  •	VPC – Virtual Private Cloud
  •	IGW – Internet Gateway
  •	IGWAtt - Internet Gateway Attachment
  •	PubSub1 – Public Subnet One
  •	PubSub2 – Public Subnet Two
  •	PrivSub1 – Private Subnet One
  •	PrivSub2 – Private Subnet Two
  •	DBSub1 – Private Subnet Database One
  •	DBSub2 – Private Subnet Database Two
  •	NatGWEIP1 – Nat Gateway Elastic IP 1
  •	NatGWEIP2 - Nat Gateway Elastic IP 2
  •	NatGW1 – Nat Gateway One
  •	NatGW2 – Nat Gateway Two
  •	PubRTB1 – Public Route Table One
  •	PrivRTB1 – Private Route Table One
  •	PrivRTB2 – Private Route Table Two
  •	DBRTB1 – Database Route Table One
  •	DBRTB2 – Database Route Table Two
  •	ALB – Application Load Balancer
  •	WpHostSG – WordPress EC2 Security Group
  •	WpEC2Group – WordPress EC2 Auto Scaling Group
  •	ScalingPolicy – Auto Scale Base on system load
  •	LaunchConfig – Auto Scaling EC2 launch Configuration
  •	 RDSDBSG – Database Security Group
  •	RDSDB – RDS MySQL Database
  •	BastionHost – Bastion Host for ssh into WordPress EC2
  •	WPbastionSG – Bastion Host Security Group
  •	SiteURL – WordPress URL


## Deploy WordPress Stack
  
    1. Install aws cli
    2. Configure AWS profile
    3. Update default public key name in main.yaml paramerter section [parameter - KeyNmae].
    4. Change default wordpress DB variables in paramerter section [parameter - DBNAME, DBUSER, DBPASSWORD].
    5. Run "aws cloudformation create-stack" from master branch.
        ex: aws cloudformation create-stack --stack-name WordPress-Infra --template-body file://main.yaml --profile <aws prefile here> --region eu-central-1
    
    *Stack ami mappings configured only for eu-central-1 and eu-north-1. Need to be update which is mapped ami's upon deploying in differnt region.
    **Also stack can be deploy via AWS Cloud-Formation GUI.

## Troubleshoot Request Timeout
  
 If load-balancer url getting timeout, check WordPress VPC default security group. If the security group ingress referring to itself like first image, then modify the ingress to allow all traffic like in second image.
 
![VPC-defaultSG](https://user-images.githubusercontent.com/44127516/100249708-8b39c500-2f45-11eb-9b65-e02ed8248ecc.png)

![VPC-all-traffic](https://user-images.githubusercontent.com/44127516/100249722-8f65e280-2f45-11eb-8449-6ab7e4e2939b.png)
