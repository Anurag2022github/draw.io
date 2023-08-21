---
title: "AWS Basic Architecture"
datePublished: Sun Jul 09 2023 17:56:52 GMT+0000 (Coordinated Universal Time)
cuid: cljvql09w000009mofabqawzj
slug: aws-basic-architecture
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1688924911039/e27f7fdc-bc96-45ed-bb72-b8478cd8495c.gif
tags: aws, devops, amazon-web-services, 90daysofdevops, trainwithshubham

---

![](https://cdn.hashnode.com/res/hashnode/image/upload/v1688732652219/22477be5-39ff-45b6-8706-3e7ea4278687.png align="center")

AWS Cloud: AWS Cloud refers to the suite of cloud computing services provided by Amazon Web Services (AWS). It offers on-demand access to virtualized computing resources such as storage, servers, databases, and networking, allowing organizations to build and deploy applications without the need for physical infrastructure.

VPC (Virtual Private Cloud): VPC is a virtual network that enables users to launch AWS resources in a logically isolated section of the AWS Cloud. It provides control over the networking environment, including IP address range selection, creation of subnets, configuration of route tables, and network gateways. VPC allows organizations to securely connect their resources and define network-level access controls.

Regions: AWS is divided into multiple geographically distributed regions, such as N.Virginia, which are comprised of several availability zones. Each region is an independent infrastructure hub with its own set of AWS services. Regions help organizations ensure low-latency access, disaster recovery, and compliance with data sovereignty regulations.

Availability Zones: Availability Zones (AZs) are physically separate data centers within an AWS region. They are designed to provide fault tolerance and high availability for applications. Each AZ has independent power, cooling, and networking infrastructure, reducing the risk of simultaneous failures. Deploying resources across multiple AZs ensures resilience and business continuity.

Load Balancer: An AWS Load Balancer distributes incoming application traffic across multiple EC2 instances or containers to enhance availability and fault tolerance. It automatically scales resources based on demand, improves application performance, and performs health checks to ensure only healthy instances receive traffic. Load balancers also provide SSL termination and support for multiple protocols.

Auto Scaling: Auto Scaling automatically adjusts the number of EC2 instances or containers based on the configured policies and observed traffic patterns. It ensures optimal resource utilization and provides elasticity for applications to handle varying workloads. Auto Scaling helps maintain application availability and saves costs by scaling resources up or down as needed.

Public vs Private Subnets: Subnets are logical divisions within a VPC that allow organizations to group resources based on network requirements. A public subnet is associated with a route table that has an internet gateway, allowing resources within it to have direct internet access. In contrast, a private subnet lacks direct internet access and relies on network address translation (NAT) to communicate with the internet.

RDS (Amazon Relational Database Service): RDS is a managed database service offered by AWS. It simplifies the process of setting up, operating, and scaling a relational database in the cloud. RDS supports popular database engines like MySQL, PostgreSQL, Oracle, and SQL Server. It handles administrative tasks such as backups, software patching, and automated backups, allowing developers to focus on application development rather than database management.