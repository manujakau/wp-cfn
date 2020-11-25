## WordPress CloudFormation Templates

# WordPress Infrastrcture

![WordPress](https://user-images.githubusercontent.com/44127516/100247762-5a589080-2f43-11eb-80a7-8e15d48851ae.jpg)

diagram keys:
  IGW - Internet Gateway
  ALB - Application Load Balancer
  NAT GW - Nat Gateway
  ASG - Auto Scaling Group
  AZ0-1 - Availability Zone 1 & 2
  
  
  # Deploy WordPress Stack
  
    1. Install aws cli
    2. Configure AWS profile
    3. Run "aws cloudformation create-stack" from master branch.
        ex: aws cloudformation create-stack --stack-name WordPress-Infra --template-body file://main.yaml --profile <aws prefile here> --region eu-central-1
        
    *Also stack can be deploy via AWS Cloud-Formation GUI.

