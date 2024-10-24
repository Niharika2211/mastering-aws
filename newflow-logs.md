
# VPC Flow Logs Lab

This repository demonstrates how to create and work with Amazon VPC Flow Logs, capture network traffic, and analyze logs. The lab includes setting up a VPC, generating traffic, and storing flow logs in Amazon S3.

## Overview

Amazon VPC Flow Logs is a feature that captures information about IP traffic going to and from network interfaces in your VPCs. Flow log data can be published to the following locations:

- Amazon CloudWatch Logs
- Amazon S3
- Amazon Kinesis Data Firehose

VPC Flow Logs help with:
- Diagnosing overly restrictive security group rules
- Monitoring traffic reaching your instances
- Determining the direction of traffic to and from network interfaces

### Types of Flow Logs:
1. **VPC-level Flow Logs**
2. **Subnet-level Flow Logs**
3. **Instance-level Flow Logs**

You can create or delete flow logs without impacting network performance.

---

## Lab Instructions

### 1. Create a VPC and Instance
Set up a VPC and create an EC2 instance within it.

### 2. Install NGINX on the Instance
Connect to the instance and run the shell script to install, restart, and check the status of NGINX.

Create a file `install_nginx.sh` with the following content:

```bash
#!/bin/bash
sudo apt update
sudo apt install -y nginx
sudo systemctl start nginx
sudo systemctl enable nginx
sudo systemctl status nginx
```

### 3. Create an S3 Bucket
Create an S3 bucket where the flow logs will be stored.

### 4. Set Up VPC Flow Logs
Create flow logs for your VPC and configure them to be stored in the S3 bucket.

### 5. Generate Traffic
Use the following shell script to continuously generate traffic to your NGINX server.

Create a file `traffic_generator.sh` with the following content:

```bash
#!/bin/bash
while true; do
  curl ec2-18-213-110-137.compute-1.amazonaws.com | grep -i nginx;
  sleep 1;
done
```

### 6. Check S3 Bucket for Logs
After the traffic generation script runs, check your S3 bucket for the AWS logs.

---

## Analyzing Logs

VPC Flow Logs can be exported and shared in formats like Excel sheets for easy data manipulation and reporting. You can also integrate logs into Power BI to generate graphical representations, providing insights into network activity.

The Security and Governance team regularly audits these logs. If repeated suspicious hits are detected, they may block the involved IP addresses to ensure network security.

---



---

## Shell Scripts Directory

Create a directory called `shell-scripts/` and place the following shell scripts inside it:

- `install_nginx.sh`
- `traffic_generator.sh`
```
