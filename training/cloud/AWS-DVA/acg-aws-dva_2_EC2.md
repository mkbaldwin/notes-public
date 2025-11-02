# EC2 - Elastic Compute Cloud

* Like a VM only hosted in the cloud
* You are in complete control of your instances
* Pay as you go model
* EC2 instance type determines CPU, memory, storage capabilities

## Instance Types

* **General Purpose** - Balance of compute, memory, and networking
* **Compute Optimized** - Higher CPU Power
* **Memory Optimized** - Fast performance for memory intensitve workloads
* **Accelerated Computing** - Includes special hardware accelerators or co-processors (GPU, FPGA).
* **Storage Optmized** - Focused on large storage quantities

## EBS Volumes

* Elastic block store
* Storage volume that can be attached to your EC2 instance
* Use the same way as any system disk
* Can only be attached to an EC2 instance located in the same AZ
* Features
  * Designed for mission critical production loads
  * Highly Available (replicated within single AZ)
  * Scalable - increase size without downtime
* Volume Types
  * **General Purpose SSD** 
    * gp2 - Balance or price and performance. 3 IOPS/GB max 16,000 IOPS/volume. Volumes under 1TB can burst to 3,000 IOPS.
    * gp3 - Latest generation. Baseline of 3,000 IOPS for any volume size. Can be 1GB to 16TB. Up to 16,000 IOPS. Currently cheaper than gp2.
  * **Provisioned IOPS SSD** 
    * io1 - Up to 64,000 IOPS per volume. 50 IOPS/GiB. Designed for IO intensive applications.
    * io2 - Latest generation with higher durability and IOPS. Same price as io1. 500 IOPS/GiB max 64,000 IOPS per volume. Designed for 99.999% durability.
    * io2 block express = SAN storage in the cloud. EBS express architecture. 4x IOPS throughput. Up to 64TB and 256,000 IOPS per volume. 99.999% durability. Great for large mission critical apps such as SAP HANA, Oracle, etc.
* **Throughput Optimized HDD (st1)**
  * Low cost HDD volume
  * Cannot be used as a boot volume
  * Baseline Performance 40MB/s per TB, burst 250MB/s per TB, max 500MB/s per volume
  * Great for throughput intensive workloads with large amounts of data (data warehosuse, big data)
* **Cold HDD (sc1)**
  * Lowest cost
  * Baseline throughput 12MB/s per TB, burst 80MB/s per TB, max 250MB/s per volume
  * Cannot be used as a boot volume
  * Good for infrequently accessed data with lower performance needs.

| IOPS | Throughput |
|------|------------|
| Read/Write operations per second | Bits read or written per second |
| Quick Transactions, Low Latency Apps | Large Data, Complex Queries |
| Provisioned IOPS SSD (io1 or io2) | Throughput Optimized HDD (st1) |

Mounting an EBS volume

```
mkfs -t xfs /dev/xvdf
mkdir /newvolume
mount /dev/xvdf /newvolume
```

Auto mount: Edit `/etc/fstab` add 

```
/dev/xvdf   /newvolume  xfs defaults,nofail 0   0
```

Note: this is tab separated.

## Elastic Load Balancer

* Application Load Balancer
  * Works on HTTP/HTTPS traffic
  * Operates at Level 7 (application aware)
  * Balance traffic between a set of servers
  * Can route to different servers based on defined rules
* Network Load Balancer
  * Works on TCP traffic
  * Layer 4
  * High Performance
  * Most expensive option
* Classic Load Balancer
  * Legacy option
  * TCP/Layer 4 w/some layer 7 features
* `X-Forwarded-For` header allws the web server to know the clietn IP connecting through the load balancer.
* Common Load Balancer error - 504: Gateway Timeouot - Target failed to respond
* Gateway Load Balancer
  * New Option
  * Load balancing for third party virtual appliances

## EC2 Image Builder

* Allows you to create AMIs for EC2 and container images
* Simple to use GUI
* Automates creating and maintaining images
* Can apply updates and run validation tests
* Steps
  1. Provide Base OS Image
  2. Define Software Packages
  3. Test
  4. Distribute to the regions you have selected
* Image Pipeline - Defines the configuration and end-to-end process of building an image.
* Image Recipie - Steps for building an image.
* Must create an IAM role to allow image builder to perform its tasks.

## Amazon Machine Images (AMIs)

* AMIs are regional
* Have to copy to each region you want to use it in
* Encryption
  * Unencrypted AMI to unencrypted AMI copy supported.
  * Encrypted AMI to encrypted AMI copy supported.
  * Unencrypted AMI to encrypted AMI copy supported.
  * Cannot copy from encrypted to unencrypted.
