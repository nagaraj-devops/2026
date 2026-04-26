
### Private Subnet
### NAT gateway
### Elastic IP

# AWS VPC Architecture Overview

This document describes a tiered VPC architecture designed for high availability and security. The infrastructure is contained within a single VPC using the `10.0.0.0/16` CIDR block.

## Architecture Diagram
<img width="588" height="690" alt="image" src="https://github.com/user-attachments/assets/0bf93376-a8f2-48d5-bd2b-5eb06642153e" />

## Component Breakdown

### 1. Networking Foundation
* **VPC:** `10.0.0.0/16` (Provides 65,536 private IP addresses).
* **Internet Gateway (IGW):** Enables communication between the VPC and the internet.

### 2. Public Tier (Egress/Ingress)
The public tier consists of three subnets associated with a Route Table that has a path to the IGW (`0.0.0.0/0`).
* **Public Subnet 01 (`10.0.1.0/24`):** Hosts the **Application Load Balancer (ALB)** to distribute incoming traffic.
* **Public Subnets 02 & 03:** Host **EC2 Web Instances**. Subnet 03 uses a `/23` mask for a larger address pool.

### 3. Private Tier (Internal Only)
The private tier consists of two subnets used for application logic or databases.
* **Security:** These subnets do not have a direct route to the Internet Gateway.
* **Compute:** Hosts internal **EC2 Application Servers**. 
* *Note: To enable software updates, these should ideally route through a NAT Gateway located in the Public Tier.*

## Routing Logic (Recommended)
| Destination | Target | Description |
| :--- | :--- | :--- |
| `10.0.0.0/16` | Local | Internal VPC traffic |
| `0.0.0.0/0` | IGW | Public Internet access (Public Subnets only) |
