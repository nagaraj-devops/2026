# AWS Networking Security Guide: SG vs NACL

This guide explains the two layers of network security within an AWS VPC: Security Groups and Network Access Control Lists (NACLs).

---

## 1. Security Groups (Instance Level)
A Security Group acts as a **virtual firewall** for your EC2 instances. It operates at the instance level (specifically the Elastic Network Interface).

### Key Characteristics:
* **Stateful:** If you allow inbound traffic on a specific port, the outbound response is automatically allowed, regardless of outbound rules.
* **Rules:** Supports **Allow** rules only. There is an implicit "deny all" for anything not defined.
* **Evaluation:** All rules are evaluated before traffic is permitted.

### Inbound vs. Outbound
| Direction | Behavior |
| :--- | :--- |
| **Inbound** | Controls incoming traffic to the instance (e.g., Allow port 80/443 for web traffic). |
| **Outbound** | Controls outgoing traffic from the instance (Default is usually "Allow All"). |

---

## 2. Network ACLs (Subnet Level)
A Network Access Control List (NACL) is an optional layer of security that acts as a **firewall for controlling traffic in and out of one or more subnets**.

### Key Characteristics:
* **Stateless:** Return traffic must be explicitly allowed by a rule in the opposite direction.
* **Rules:** Supports both **Allow** and **Deny** rules.
* **Evaluation:** Rules are processed in **numerical order** (starting from the lowest number).

### Inbound vs. Outbound
| Direction | Behavior |
| :--- | :--- |
| **Inbound** | Controls traffic entering the subnet boundary. |
| **Outbound** | Controls traffic leaving the subnet boundary. |

---

## 3. Comparison Summary

| Feature | Security Group (SG) | Network ACL (NACL) |
| :--- | :--- | :--- |
| **Scope** | Instance Level (ENI) | Subnet Level |
| **State** | **Stateful** | **Stateless** |
| **Rules** | Allow only | Allow and Deny |
| **Rule Order** | Evaluates all rules | Processes in numeric order |
| **Applied to** | Instances/Resources | All resources in a Subnet |

---

## 4. Common Traffic Scenarios

### Web Server Example
If you have a web server in a public subnet:
1.  **Security Group Inbound:** Allow Port 80 (HTTP) and 443 (HTTPS) from `0.0.0.0/0`.
2.  **NACL Inbound:** Allow Port 80/443 from `0.0.0.0/0`.
3.  **NACL Outbound:** Must allow **Ephemeral Ports** (typically 1024-65535) to send the response back to the client.

### Database Server Example
If you have a DB in a private subnet:
1.  **Security Group Inbound:** Allow Port 3306 (MySQL) or 5432 (PostgreSQL) only from the **Web Server Security Group ID**.
2.  **Security Group Outbound:** Usually restricted to specific update repositories.
