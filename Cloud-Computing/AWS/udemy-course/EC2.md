# Elaastic Compute Cloud (EC2)

## Introduction

- Virtual machine on the host computers of AWS
- provides resizable compute capacity in the cloud
- You can create it on:
  - Shared hardware
  - Dedicated hardware
- You can have:
  - Linux instances
  - Windows instances
- You have root access to the EC2 instances
- You can stop, restart, reboot, or terminate the instance
- The uptime that AWS can garantee 99.95% for each month

### Instance Access

- To access an instance you need a key and key pair name
  - Public and private key
- When login in you need to specify the
  - private key
  - key name
- You can download the key only once
- If you launch without a key pair, you will not be able to access it via SSH or RDP (for windows)
  
### EC2 Specs
- There is a 20 AWS instances soft limit
- They have 2 types of Block store devices (hard drive):
  - Elastic Block Store (EBS)  
    - Persistent
    - Network attached virtual drives, not part of your instance
    - 2 types of volumes:
      - root volume (OS)
      - data volume (all other)
  - Instance store
    - It is not persistant, if you terminate the instance everything is wiped
    - The virtual hard drive of the host
    - Limited to 10GB per device
- EBS-Backed EC2 instance is with EBS root volume / Instance-store backed EC2 is with instance store

### EC2 instances families

- General purpose
  - Balanced memory and CPU
  - Suitable for most apps
  - M3, M4, T2 families
- Compute Optimized
  - More CPU than memory
  - Compute and High performance computing intensive use
  - C2, C4
- Memory optimized
  - More RAM/memory
  - Memory intensive apps, DB, caching
  - R3, R4
- GPU compute instances
  - Graphics optimized
  - High performane adn parallel computing
  - G2
- Storage Opimized
  - Very low latency, I/O
  - i/O intensive apps, data warehousing, Hadoop
  - I2, D2

## EC2 Block store types

- Hard drives, CDs, SSD, etc

### EBS types

- General Purpose
  - SSD-Backed (solid states drives)
  - Use cases:
    - good for transactional workloads, such as small databaes & boot volumes, low latency interactive apps
  - 1TiB-6TiB (Tibibyte)
  - Max IOPS, 10,000 (input output operations per second)
- Provisioned IOPS:
  - SSD-Backed
  - USe for mission critical applications, I/O intensive, databases
  - Provides sustainable IOPS performance and Low latency
  - Max IOPS/Volume 32,000
  - 4TiB-16TiB
- Through Optimized HDD (not SSD)
  - Ideal for streaming, big data, log processing, and data warehousing
  - Can not be used as boot volumes
  - Use for frequently accessed, throughput intensice workloads
  - Size 600Gib- 16TiB
  - Throughput is the amount of data that can pass, not the Input output operations, this measures bits written, not operations donee
- Cold HDD
  - Ideal for less frequently accessed wordloads
  - Can not be boot volume
  - Size 500 GiB - 16 TiB
- Magnetic EBS (HDD) (Old generation)
  - For transactional workloads, where performance does not depend on IOPS, rather on MB/Sec transfer rates
  - HDD backed
  - Use for infrequently accessed data
  - Volumes sizes 1GiB - 1TiB

### Block Device Mapping

- instance with multiple block storages
- AMI = amazon machine image
- Block device mapping is the mapping of block storage devices in an AMI, it includes which are the volumes, how many volumes and from which type of volumes should be launched when you launch a EC2 instance with an AMI
  - This includes both EBS and instance store volumes
  - Used to define which block storage volumes (root and data) to include/create when an instance is launched from the AMI
  - You can view it and it shows both EBS and Instance-store volumes
  - When launching an EC2 instance from an AMI the block device mapping might change because not all types of EC2 instances support the same block stores
- Once the instance is launched you can add and remove EBS volumes, but you can't do it with instance store
- Once the instance is running, the AWS console only shows EBS volumes, not instance stores, when looking at the block device mapping
  - To see the instance store volumes of the block device mapping, you need to qury the instance metadata
- Limits of the changes to blcok device mapping:
  - For the AMI block device mappings, for root volume, you can only modify volume size, volume type and the delete on termination flag
  - You can't decrease an EBS volume size when you modify its size
### EBS

- You can create a point-in-time snapshots of your EBS vollumes
  - You can do it manually or automated through the life cycle management
- Snapshots are saved in an S3 bucket
- EBS has 99.999& availability

