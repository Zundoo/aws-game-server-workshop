---
title: "4.1.1. VPC"
weight: 411
---

# 4.1.1. Provisioning Virtual Private Cloud (VPC)

*   **Objective**: Create an isolated virtual network environment on AWS infrastructure to host all game server resources.
*   **Step-by-Step Implementation**:
    1. Navigate to the **VPC Console** > select **Your VPCs** > click **Create VPC**.
    2. Configure the following parameters:
        * **Name tag**: `game-server-vpc`
        * **IPv4 CIDR block**: `10.0.0.0/16` (Provides up to 65,536 private internal IP addresses).
    3. Click **Create VPC**.
