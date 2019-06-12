# AWS Certified Solutions Architect - Associate Course

Amazon web service course for the exam of associate exam.

# Introduction to cloud computing and aws global infrastructure

## On premise data center

- Data center is a location where there is a lot of servers hosting the application and data.
- You can have multiple data centers to prevent down time
- Server can be divided virtually to host multiple apps in one server
- The problem is that they cost a lot.
- Components:
  - Netword
  - Security
  - Servers (compute)
  - WAN Wide are network to connect the servers
  - Internet
  - Storage
  - File Sharing
- **When you move to the cloud all this is taken care of by the cloud provider: AWS**
- Load Balancing
  - Distributes workload in the different computer resources
- DC Multi-Tenancy
  - Host multiple clients/users on the same infrastructure, so you virtualize the services.
- Servers
  - Physical -> physical computers
  - Virtual -> Same computer but divided into diferent vms
    - In AWS is cales EC2 (Elastic compute cloud)

## Cloud computing

- is the delivery of on-demand computing resources over the internet
- Sharing computing resources instead of having local servers
- internet based computing shared processing resources and data to computers and other devices on demand
- Advantages:
  - No setup fees
- Even though the computers are usually shared you can ask for a dedicated server

### Cloud computing offerings

- Infrastructure as a service (IaaS)
  - connectivity
  - security
  - You will install all, you will only rent the servers
- Platform as a service (PaaS)
  - It will give you the database but it wont handle it for you
- Database as a service (Daas)
  - Database is handled for you
- Software as a service
  - Like Office 365
  - They sell the software in the cloud and you don't need to worry about anything

### Cloud types

- Public cloud
  - Having the costumers have their own portal
  - Everyone can access it
- Private cloud
  - client build their own automated cloud by their own
- Hybrid cloud connection between private and public cloud

### Cloud vs on premise

- On cloud you do operational expenses instead of capital expenses (which is when you invest in the servers instead of paying for the service)
- On cloud your time to deploy is way less
- On cloud dev and test environments are easier
- Flexibility and elasticity
  - You can grow and short the cloud
- Automation
  - Everything is automated in the cloud
- The cons of the cloud is that you don't know where your data is. It is somewhere but you don't know where exactly

# Getting started in AWS

- When you create a new AWS account you are creating a root account which you should not use for day to day usage. You should create users inside the account to prevent having all the permissions by default

## IAM

- Controls the access to the services and environment in AWS
- Users
  - usuarios que se pueden verificar
  - Cada user tiene ciertos permisos
  - Por default no tiene ningún permiso
- Roles
  - virtual user, like the application
- Groups
  - Define permissions to a whole group of users
  - You can have the group permissions and extra permissions
- Always give the minimum set of permissions
- ARN = Amazon resource name
  - Is an id for all the resources in AWS

# Virtual Private Cloud

## VPC Intro

- VPC is a virtua network or data center inside AWS for one client or one department in an enterprise
- You create your own private mini cloud in which you control all of it
- VPC is region specific
- It can have more than 1 availability zone, with a VPC subnet
- In a VPC you have full control over the resources and the instances
- Similar to having your own data center inside AWS
- Isolated from other VPCs on AWS
- You can have more than one IP address subnets inside a VPC.
- Components in a VPC
  - CIDR and IP address subnets
    - IP addresses which are just for your VPC
  - Implied router
    - When using multiple availability zones you get a router so that they can communicate between each other and the outside. This is automatically set up so you don't need to worry
  - Route tables
  - internet gateway
    - What connects your VPC to the internet
  - Security Groups
    - Virtual Firewalls inside the instances to prevent one to connect to the other
  - Network Access Control List (ACL)
    - Applied to full subnet
  - Virtual private gateway
    - Lets the outside go into the vpc, using vpn or direct conections

## Implied Router and Route Tables

### Implied Router

- What connects different subnets together
- Central VPC routing
- Connects different AZ's together and connects the VPC to the Internet Gateway
- Each subnet will have a route table the routed uses to forward traffic within the VPC
- The routes tables will also have entries to external destinations

### Route Tables

- Diccionario de direcciones y a dónde mandar los paquetes según su dirección
- You can have up to 200 route tables
- You can have up to 50 routes per route table
- Each subnet MUST be associated with only one route table at any given time
  - Each subnet can only be attached to one route table but the same route table can be attached to multiple subnets
- If you don't specify a subnet-to-route-table the subnet will be attached to the main route table of the VPC
- There are 2 types of route tables:
  - Main route table
    - Created by AWS when you create the VPC
    - Can not be deleted, but you can flag another route table as the main one and then delete it
- Custom route table, which you create for different subnets
- Every route table comes with a default route that allows the communication inside the VPC
  - This rule cannot be modified nor deleted
- By default all the VPC is routed to each other, and this cannot be modified
- All this routing is intraVPC, inside the same VPC

## IP Addressing, internet gateway and subnet types

### IP Addressing

- Inside a VPC you can have multiple services with different IP addresses, in order to define this IP addresses you create subnets which allow you to have more hosts inside the network.
- the encoding that AWS use is CIDR (Classless Inter-Domain Routing) and you need to decide the block range you want to use when you create the VPC
  - This cannot be changed in the future so it is the best solution to have more available IP addresses than less
  - If you need to change the the CIDR size you need to create a new VPC
- If you need more IP addresses you can add secondary CIDR blocks
  - This is to expand the VPC IP address ranges
