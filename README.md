A simple vpc architecture with a load balancer and an auto scaling group
Overview:
By this project we create a vpc with public subnets and private subnets in two availability zones. Servers run in the private subnets, where these servers launched and terminated by Auto scaling group, These servers receives the requests from load balancer. The servers can connect to the internet by using NAT gateways. Where public subnets in each availability zone has a NAT gateway and a load balancer node.
Resouces used in this project:
VPC(public subnets, private subnets, load balancer, target group, NAT gateway, internet gateway, autoscaling group)
EC2(instances, security groups, elastic ips)
Project architecture:

 









Step wise procedure to achieve this architecture:
•	Create a vpc with public and private subnets in two availability zones 






•	Create a route table for both the public subnets and add association. And create each route table for each private subnet and add association respectively.

 


•	Create a internet gateway and attach to VPC that we have created and add a route to route table associated with public subnets.


 


•	Create two NAT gateways add route to each route table associated with private subnet respectively.

 


•	Create a template for auto scaling group so that  auto scaling group  will create minimum instances in each availability zone. Then create an auto scaling group with desired capacity of 2 by using templete that we created.  We find two instances created in each availability zone. Connect to these instances in both the private subnets and deploy a simple html page in each of them.

 



•	Create a target group with two instances in both the private subnets as targets and then create a load balancer with this target group. So that load balancer will send the requests to both the targets equally.

 

 



•	Load balancer sending the requests to both the instances.


 

 





About the project:
By this project we are going to know that, how to create a VPC that you can use for servers in a production environment. To improve resiliency, you deploy the servers in two Availability Zones, by using an Auto Scaling group and an Application Load Balancer. For additional security, you deploy the servers in private subnets. The servers receive requests through the load balancer. The servers can connect to the internet by using a NAT gateway. To improve resiliency, you deploy the NAT gateway in both Availability Zones.
