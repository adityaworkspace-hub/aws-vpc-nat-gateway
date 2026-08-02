![AWS](https://img.shields.io/badge/AWS-VPC-orange)
![EC2](https://img.shields.io/badge/EC2-Running-success)
![DevOps](https://img.shields.io/badge/DevOps-Lab-blue)
![Status](https://img.shields.io/badge/Project-Completed-brightgreen)



AWS VPC - Public & Private Subnet Architecture

Project Overview

This project demonstrates how to build a secure AWS Virtual Private Cloud (VPC) with:

- Custom VPC
- Public Subnet
- Private Subnet
- Internet Gateway
- NAT Gateway
- Route Tables
- Elastic IP
- EC2 Web Server
- EC2 Database Server

The goal is to:

- Allow the Public EC2 instance to access the Internet.
- Allow the Private EC2 instance to access the Internet through the NAT Gateway.
- Keep the database server isolated from direct Internet access.

![NAT Gateway](screenshots/NATGATEWAY.png)


Services Used

- Amazon VPC
- Amazon EC2
- Internet Gateway
- NAT Gateway
- Elastic IP
- Route Tables
- Security Groups
- MobaXterm

Network Details

| Resource | CIDR |
|----------|---------|
| VPC | 192.168.0.0/16 |
| Public Subnet | 192.168.1.0/24 |
| Private Subnet | 192.168.3.0/24 |

Step 1 - Create VPC

Created a custom VPC with the CIDR block:

192.168.0.0/16

![VPC](screenshots/vpc-created.png)

Step 2 - Create Public Subnet

Created the Public Subnet with the CIDR block:

192.168.1.0/24

![Public Subnet](screenshots/public-subnet.png)

Step 3 - Create Private Subnet

Created the Private Subnet with the CIDR block:

192.168.3.0/24

![Private Subnet](screenshots/private-subnet.png)

Step 4 - Create Internet Gateway

Created and attached an Internet Gateway to the VPC.

![Internet Gateway](screenshots/internet-gateway.png)

Step 5 - Configure Public Route Table

| Destination | Target |
|------------|---------|
| 192.168.0.0/16 | local |
| 0.0.0.0/0 | Internet Gateway |

![Public Route Table](screenshots/route-table-public.png)

Step 6 - Allocate Elastic IP

Allocated an Elastic IP for the NAT Gateway.

![Elastic IP](screenshots/eip.png)

Step 7 - Create NAT Gateway

Created the NAT Gateway in the Public Subnet.

![NAT Gateway](screenshots/nat-gateway.png)

Step 8 - Configure Private Route Table

| Destination | Target |
|------------|---------|
| 192.168.0.0/16 | local |
| 0.0.0.0/0 | NAT Gateway |

![Private Route Table](screenshots/route-table-private.png)

Step 9 - Launch Public EC2 Instance

Launched a Web Server in the Public Subnet.

![Public EC2](screenshots/ec2-public.png)

Step 10 - Launch Private EC2 Instance

Launched a Database Server in the Private Subnet.

![Private EC2](screenshots/ec2-private.png)

Connectivity Test

Verified the following:

- Successfully connected to the Public EC2 instance using SSH in MobaXterm.
- Confirmed that the Private EC2 instance has no public IP address.
- Verified outbound Internet access from the Private EC2 instance through the NAT Gateway in MobaXterm.

![SSH Test](screenshots/ssh-test.png)

Learning Outcomes

- Created a custom VPC.
- Configured Public and Private Subnets.
- Attached an Internet Gateway.
- Created a NAT Gateway with an Elastic IP.
- Configured Public and Private Route Tables.
- Launched EC2 instances in different subnets.
- Implemented secure AWS networking using AWS best practices.

Author

ADITYA MANIVANNAN

AWS Cloud | DevOps Engineer
