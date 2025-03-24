# design-and-implement-a-secure-three-tier-architecture
create a complete network infrastructure with proper security controls and load balancing for a web application. The architecture must include web servers, application servers, and database servers, each in their own network tier with appropriate security boundaries.
Create an ARM template that implements the following architecture:

1. Network Infrastructure
Create a Virtual Network with address space 10.0.0.0/16
Create three subnets:
Web tier subnet (10.0.1.0/24)
Application tier subnet (10.0.2.0/24)
Database tier subnet (10.0.3.0/24)
Apply a single Network Security Group to all subnets
2. Security Groups
Create three Application Security Groups (ASGs), one for each tier:
Web servers ASG
Application servers ASG
Database servers ASG
Configure a Network Security Group with rules that:
Allow HTTP (80) and HTTPS (443) traffic from the internet to the web tier ASG
Allow HTTPS (443) traffic from the web tier ASG to the application tier ASG
Allow SQL Server (1433) traffic from the application tier ASG to the database tier ASG
Deny all other inbound traffic
3. Load Balancer
Create a public-facing Azure Load Balancer for the web tier
Configure the load balancer with:
A public IP address
A backend pool for web servers
Health probes for HTTP and HTTPS
Load balancing rules for ports 80 and 443
4. Virtual Machine Planning
DO NOT implement the actual VMs, but your ARM template should be designed to accommodate:
3 VMs for each tier (web, application, database)
Each VM should be assigned to its appropriate ASG
Web tier VMs should be configured to join the load balancer's backend pool
