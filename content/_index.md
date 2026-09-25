---
title : "Workshop Overview"
date : "2026-09-25" 
weight : 1 
chapter : false
---

# AWS REAL-TIME GAME SERVER WORKSHOP

#### Lab Overview
This workshop focuses on the process of architecting, deploying, and testing a high-concurrency cloud infrastructure tailored for a **Real-time Game Server** operating on persistent **WebSocket** connections. 

The entire framework is engineered and provisioned using the **Amazon Web Services (AWS)** ecosystem combined with containerization practices and in-memory databases to achieve ultra-low latency data propagation, high availability, and smart automated scalability during player surges.

![Overall AWS Game Server Architecture Diagram](/images/architecture-diagram.png?featherlight=false&width=90pc)

{{% notice info %}}
**Security Notice**: The infrastructure applies a 3-Tier Architecture to completely isolate the compute and database layers within **Private Subnets**. The Application Load Balancer (ALB) in the Public Subnet acts as the single secure entry point from the public internet.
{{% /notice %}}

#### 🛠️ Core AWS Ecosystem Services Utilized

*   **Amazon VPC**: Constructing isolated virtual networks, segmenting subnets, and managing tight security group firewall policies.
*   **Amazon ECR & Docker**: Containerizing Node.js WebSocket applications and orchestrating secure, centralized private registry management.
*   **Amazon Elastic Container Service (ECS)**: Orchestrating and maintaining container application runtimes serverlessly via AWS Fargate.
*   **Application Load Balancer (ALB)**: Unified public entry facade managing automated network protocol upgrades from HTTP to WebSockets.
*   **Amazon ElastiCache Redis**: Secure In-Memory cache tier (TLS encryption in-transit enabled) syncing game session data across scaling servers.
*   **Amazon CloudWatch**: Collecting hardware performance counters and managing centralized container log streams.

#### 💡 Technical Highlights & Production Troubleshooting

1.  **Resolving Redis TLS Connection Hangs**: Learn to fix network timeout issues caused by the *Encryption in-transit* feature by synchronizing the `--tls` flag on the terminal and configuring the source code to use the `rediss://` protocol.
2.  **Fixing CloudWatch Logs Authorization**: Troubleshoot `AccessDeniedException` by attaching the `CloudWatchAgentServerPolicy` to the IAM Role and configuring the `--log-driver=awslogs` parameter.
3.  **High-Concurrency Stress Testing**: Utilize Artillery to simulate **1,000 concurrent virtual users** and process **46,500 real-time messages**, successfully verifying the container Auto Scaling policy triggered at a 70% CPU threshold.

---

#### 📂 Workshop Implementation Navigation

1. [4.1. Networking](4-workshop/4.1-networking/)
2. [4.2. Container](4-workshop/4.2-container/)
3. [4.3. Database](4-workshop/4.3-database/)
4. [4.4. Game Server](4-workshop/4.4-game-server/)
5. [4.5. Load Balancing](4-workshop/4.5-load-balancing/)
6. [4.6. Scaling](4-workshop/4.6-scaling/)
7. [4.7. Monitoring](4-workshop/4.7-monitoring/)
8. [4.8. CI/CD](4-workshop/4.8-cicd/)
9. [4.9. Load Testing](4-workshop/4.9-load-testing/)
10. [4.10. Cleanup](4-workshop/4.10-cleanup/)
