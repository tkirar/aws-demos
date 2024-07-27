### VPC Peering ###

![aws vpc](https://github.com/user-attachments/assets/c5b83e15-5814-449e-b0c8-b0e1593d293f)

  ## what is VPC Peering ##
  VPC peering is like creating a direct, private connection between two Virtual Private Clouds (VPCs).
  This allows resources in one VPC to communicate with resources in another VPC as if they were on the same network.

  ## What is VPC ##

  - VPC
   Virtual Private Cloud (VPC) is like a your private isolated area within a public cloud. Imagine renting a piece of the internet that only you can access and control.


### Instructions to create VPC peering ###

#### VPC ####
- Create VPC by names VPC-1 and VPC-2
- Provide CIDR values to the VPC-1 and VPC-2. CIDR basically defines IP in the given neteork range. Let CIDR be : 12.0.0.0/16 for VPC-1 and 13.0.0.0/16 for VPC-2
 
#### Subnet ####
A subnet, short for subnetwork, is a segmented piece of a larger network.A subnet is defined by a CIDR (Classless Inter-Domain Routing) block, which specifies the range of IP addresses it contains. 
For example, 10.0.1.0/24 represents a subnet with 256 IP addresses.

Public and Private Subnets:

- Public Subnet: A subnet that is associated with a route table containing a route to an internet gateway, allowing resources in the subnet to access the internet.
- Private Subnet: A subnet without a route to the internet gateway, meaning resources in the subnet cannot directly access the internet.

  #### Route Table ####
  - Create 2 Route tables rt-vpc-1 and rt-vpc-2
  - Associate both Route tables to their respective vpc-1 and vpc-2
  - 

  #### Internet Gateway ####
  - Create internet gateway so that vpc can connect to internet.
  - igw-vpc-1 for vpc-1 and  igw-vpc-2 for vpc-2. Attach both the internet gateway to thier respective VPC
  - Edit both the Route table rt-vpc-1 and rt-vpc-2. ADD 0.0.0.0 to internetgateway. So that traffic from internet can come to internet gateway ---> VPC
 
  #### VPC Peering ####
  - Create a vpc service and give name vpc-peering-betwwen-VPC1-and-VPC2
  - In oreder to access resouces from VPC1 and VPC2. Edit Both the route tables.
  - CIDR range of VPC-1 in the route table rt-vpc-2 and CIDR range of VPC-2 in the rt-vpc-1. So that both the route table can route traffic from one VPC to other.


  #### EC2 Instances ####
  - Create 2 instances with ubuntu image,t2.micro and install apache2. So that later we can check by fetching the web page.
  - one in vpc1 and subnet-vpc-1-1a and other in vpc2 and subnet-vpc-2-1a
  - after initializing both the instances ssh into both the instance and Curl private ip of both.
  - If peering is succesfull it would fetch the index.html data.

