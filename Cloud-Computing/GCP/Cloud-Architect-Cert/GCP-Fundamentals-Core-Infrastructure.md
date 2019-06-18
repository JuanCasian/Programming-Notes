# Google Cloud Platform Fundamentals: Core Infrastructure

## Introducing GCP

### What is cloud computing?

- Is a way of using IT which has these 5 traits:
  - Computing resources on demand and self-serivxe
  - Broad network access - access from anywhere
  - Resources pooling - huge pool of resources and then you are alocated a piece of it
  - Rapid elasticity - if you need more res, you can get more
  - Measured service - pay only what you use or reserve

### How did we get here?

1. You had data centers were each hardware was a full piece
2. Then all the datacenters where on a same place and you would connect to them. (colocation)
3. You virtualized the hardware to separate it into different components
4. Then everything started being used in containers, which would make it easier to make it elastic

### GCP computing architectures

- Google provides different types of services:
  - Infrastructure as a Service SaaS
    - In compute engines
    - You pay what you allocate
  - Hybrid
    - Kubernetes Engines
  - Platform as a Service (PaaS)
    - App Engine
    - bhinds application code into librearies that give access to the infrastructure
    - You pay for what you use

### GCP Regions and zones

- A zone is a deployment area
  - Is kind of a data center
- Zones group into regions which are independent geographical areas
  - Inside regions you got low latency connectivity
  - Under 5 miliseconds
- You can put some resources in a multi-region
  - which makes the resources place in more than 1 region to increase redundancy

### Pricing innovations

- Bills by the second
- When you run more time they give you a discount

### Multilayered security approach

- Servers and networking equipment are custom design by Google
- They design hardware security chips called Titan
- Servers use cryptographic signatures
- Designs and builds its own datacenters incorporating physical security
- The access to the datacenters is restricted
- Encrypted traffic within Google's network

## GCP resource Hierarchy


- Everything is organized into projects
- This projects can be organized into folders and folders inside folders
- All of this can be inside an organization node
- You can put security policies on each of this
- All GCP resources are inside projects
- Inheritance is from top to bottom
- Each resource can only have 1 project
- Each project has a name, ID and unique project number
- EX:
  - Atrato
    - Folder atrato1
      - Project DB
      - Project Node.js
    - Folder Atrato2
      - Project Autonomo
- To use folders you need an organization node
- Organization Policy Administrator
  - Controls everything
- Project Creator:
  - Can create projects
- To get an organization node:
  - You can use google cloud identity to get one
- The policies implemented in higher level can't take away permisions given on the lower level


## IAM

### Identity and Access management

- Lets administratos authorize stuff
- An IAM policy has 3 parts:
  - Who part:
    - tells who this policy is applicable too
    - can be a google account, a group, a service account, an entire gsuite, cloud identity domain
  - can do what part:
    - defined by an IAM role, which is a collection of permisions
    - There are 3 kinds of roles:
      - primitive roles
        - Applied to GCP project and they affect all resources:
          - owner, editor, viewer, billing administrator
      - predefined roles by GCP
        - Can be used in only resources, projects, folders, etc
      - custom roles
        - created by you
  - on which resource:
    - where is the policy going to apply

### IAM Roles

- Compute Engine instant admin role
  - Gives permisions for VMS
  - listing them, reading, changing tehir config, and starting and stopping them
- Costum rote:
  - created by yourself
  - caution:
    - are hard to use
    - can only be used at project and organization levels
- Service accounts:
  - account to authenticate a resources (ex: VMs) ID
  - useful if you want a vm to use a certain other resource but you don't want to give access to only one user
  - They use authenticate keys instead of passwords
  - You can assig IAM roles to it
  - Used to allow apps to manage GCP resources
  - Service accounts are also resources, so you can grant roles to control this accounts
  - You can be used as groups of resources

## Interacting with GCP

4 ways to interact

- Console
  - web based admin interface
  - Lets view and manage all projects and folders
  - Gives access to resources APIs
  - Gives acces to cloud shell
  - From Cloud shell you can use the tools of the SDK
- GCP Software Development Kit (SDK)
  - Set of tools thar you can use to manage the resources and apps on GCP
  - includes:
    - `gcloud` tool
      - main command line interface (CLI) for gcp products and services
    - `gsutil` tool
      - for Google cloud storae and ]
    - bq 
      - for big query
  - Can be accessed on the cloud shell
  - Install it on your own terminal
  - Download the docker image that already has it
- RESTful APIs
  - For applications that you program
  - usually use JSON
  - Enabled through GCP console
  - Most APIs use daily quotas and limits
  - APIs explorer is a tool that helps you to learn the APIs interactively
  - Google provides client libraries to code for APIS
    - Cloud clinet libraries
      - Best one
    - Google API client library 
- GCP mobile app
  - Lets you manage the resources for GCP

## Cloud Marketplace

- Tool for quick deployment of solutions
- Most of them don't have additional charges
- Some have usage fees
- GCP fixes the images software, but it does not once the image is deployed

