
### Private Subnet
### NAT gateway
### Elastic IP

<img width="588" height="690" alt="image" src="https://github.com/user-attachments/assets/0bf93376-a8f2-48d5-bd2b-5eb06642153e" />

This diagram illustrates a standard AWS Virtual Private Cloud (VPC) architecture designed for a tiered application. It outlines how traffic flows from the internet through various security boundaries to reach compute resources.

Here is a breakdown of the components and the logic shown:

1. The Network Container (VPC)
VPC Scope: The large purple box represents the VPC itself, with a primary CIDR block of 10.0.0.0/16. This provides a private network space for all the resources inside.

Internet Gateway (IGW): The orange cloud icon at the top is the gateway that allows communication between the VPC and the internet.

2. The Public Tier (Public Subnets)
The diagram shows three public subnets (10.0.1.0/24, 10.0.2.0/24, and 10.0.3.0/23). These are "public" because their associated Route Table (shown with the 172.16.x.x entries) directs traffic to the Internet Gateway.

Subnet 01: Contains an Application Load Balancer (ALB), which typically acts as the entry point for external web traffic.

Subnets 02 & 03: Contain EC2 Auto Scaling Groups, suggesting these subnets host the web servers or front-end application logic.

3. The Private Tier (Private Subnets)
At the bottom, there are two private subnets. These are isolated from the direct internet.

Connectivity: They are connected to a separate Route Table. In a production environment, these usually host sensitive resources like databases or backend microservices.

Resource: One subnet contains an EC2 instance (indicated by the orange icon with the chip inside), likely an application or database server that should not be reachable directly from the public web.

Technical Observations & Inconsistencies
If you are using this as a reference for a real build, there are a few technical quirks to note in the image:

Route Table IP Ranges: The Route Tables show 172.16.0.0 series IPs. Usually, route tables inside a 10.0.0.0/16 VPC would show routes for the 10.0.0.0 range (local) and 0.0.0.0/0 (internet). The 172 addresses in the diagram might be placeholders or representing a peered network.

Subnet Masking: Subnet 03 uses a /23 mask (10.0.3.0/23), which is larger than the /24 masks used for the others. This is perfectly valid but means Subnet 03 has double the IP capacity of Subnet 01.

NAT Gateway Missing: For the Private Subnets to download updates from the internet (egress-only), you would typically see a NAT Gateway sitting in one of the Public Subnets, which isn't explicitly drawn here.
