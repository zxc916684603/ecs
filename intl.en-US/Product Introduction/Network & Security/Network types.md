# Network types {#concept_nfj_dz2_5db .concept}

Alibaba Cloud offers Virtual Private Cloud \(VPC\) networks and a Classic network.

## Virtual Private Cloud \(VPC\) {#section_ix4_gfw_ydb .section}

VPCs are isolated networks established in Alibaba Cloud and are logically isolated from each other.  You can customize the topology and IP addresses in a VPC.  We recommend VPCs, when you are skilled in network management and have higher network security requirements.

For more information about VPC, see Virtual Private Cloud documentation.

## Classic network {#section_jx4_gfw_ydb .section}

Classic network is majorly deployed in the public infrastructure of Alibaba Cloud, which is highly responsible for its planning and management. We recommend classic network, if your business requirements are higher in terms of network usability.

**Note:** If you did not purchased an ECS instance before 17:00 \(UTC+8\) on June 14, 2017, you cannot choose the Classic network.

## VPC vs. Classic network {#section_kx4_gfw_ydb .section}

The following table lists all the functional differences between the VPCs and the classic networks.

|Comparison items|VPC|Classic network|
|:---------------|:--|:--------------|
|Two-layer logic isolation|Supported|Not supported|
|Custom private network blocks|Supported| Not supported|
|Private IP addresses|Unique in one VPC. Replicable between VPCs.|Unique in the global Classic network|
|Communicate within or between private networks|Able to communicate within a VPC, but isolated between VPCs|Able to communicate in one region and under one account|
|Tunneling|Supported|Not supported|
|Custom router|Supported|Not supported|
|Routing table|Supported|Not supported|
|Switches|Supported|Not supported|
|SDN|Supported|Not supported|
|Self-built NAT gateway|Supported|Not supported|
|Self-built VPN|Supported|Not supported|

