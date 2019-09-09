# Authorize internal network communication between ECS instances for different accounts through the API {#concept_40597_zh .concept}

This topic describes how to authorize internal network communication between ECS instances for different accounts in the same region.

## Background {#section_o1v_5zf_q09 .section}

You can authorize internal network communication in either of the following modes:

-   Communication between ECS instances: You can authorize internal network communication between two ECS instances that belong to the same account.
-   Communication between accounts: You can authorize internal network communication between all ECS instances that belong to two different security groups within the same region, including those purchased after authorization.

    **Note:** To enable internal network communication between different accounts, you can authorize communication between security groups in each account. Then, ECS instances in the security groups can communicate over the internal network. Modifying security group configurations will affect all ECS instances in a security group, as well as services running on these ECS instances. Use caution when performing this operation.


## Limits {#section_nd1_ihg_dhv .section}

Security groups are virtual firewalls for ECS instances. Security groups do not provide communication and networking capabilities. After you authorize internal network communication between instances in different security groups, ensure that the instances can establish internal network communication.

-   If all instances are of the classic network type, they must be in the same region.
-   If all instances are of the VPC type, instances in different VPCs cannot communicate with each other. We recommend that you establish public network communication methods, or use [Express Connect](../../../../reseller.en-US/Product Introduction/What is Express Connect?.md#), [VPN Gateway](../../../../reseller.en-US/Product Overview/What is VPN Gateway?.md#), or [Cloud Enterprise Network](../../../../reseller.en-US/Product Introduction/What is Cloud Enterprise Network?.md#).
-   If instances are of different network types, enable [ClassicLink](../../../../reseller.en-US/Network/Connect a classic network to a VPC.md#) to allow communication between instances.
-   If instances are located in different regions, we recommend that you establish public network communication methods, or use [Express Connect](../../../../reseller.en-US/Product Introduction/What is Express Connect?.md#),[VPN Gateway](../../../../reseller.en-US/Product Overview/What is VPN Gateway?.md#), or [Cloud Enterprise Network](../../../../reseller.en-US/Product Introduction/What is Cloud Enterprise Network?.md#).

## Prerequisites {#section_8w3_hgg_snp .section}

Alibaba Cloud CLI is used to call ECS APIs. Make sure that you have [installed](https://partners-intl.aliyun.com/help/doc-detail/90765.htm) Alibaba Cloud CLI and [configured](https://partners-intl.aliyun.com/help/doc-detail/90766.htm) it for use.

## Authorize internal network communication between ECS instances {#section_vsk_hvp_e2b .section}

1.  Query the internal IP addresses and security group IDs of the two ECS instances.

    You can obtain the IDs of the security groups to which the ECS instances belong through the console or by calling the [../../../../dita-oss-bucket/SP\_2/DNA0011860945/EN-US\_TP\_9865.md\#](../../../../reseller.en-US/API Reference/Instances/DescribeInstances.md#) operation. The following table lists the information of two ECS instances.

    |Instance|IP address|Security group|Security group ID|
    |--------|----------|--------------|-----------------|
    |Instance A|10.0.0.1|sg1|sg-bp1azkttqpldxgtedXXX|
    |Instance B|10.0.0.2|sg2|sg-bp15ed6xe1yxeycg7XXX|

2.  Add a rule to sg1 to allow inbound traffic from 10.0.0.2.

    ``` {#codeblock_mtg_8ws_st6}
    aliyun ecs AuthorizeSecurityGroup --SecurityGroupId sg-bp1azkttqpldxgtedXXX --RegionId cn-qingdao --IpProtocol all  --PortRange=-1/-1. --SourceCidrIp 10.0.0.2 --NicType intranet
    ```

3.  Add a rule to sg2 to allow inbound traffic from 10.0.0.1.

    ``` {#codeblock_qhe_2kw_vg5}
    aliyun ecs AuthorizeSecurityGroup --SecurityGroupId sg-bp15ed6xe1yxeycg7XXX --RegionId cn-qingdao --IpProtocol all  --PortRange=-1/-1. --SourceCidrIp 10.0.0.1 --NicType intranet
    ```

    **Note:** 

    -   In the preceding examples, region ID cn-qingdao is for reference only. Replace it with the actual region ID.
    -   In the preceding examples, the [../../../../dita-oss-bucket/SP\_2/DNA0011860945/EN-US\_TP\_9917.md\#](../../../../reseller.en-US/API Reference/Security groups/AuthorizeSecurityGroup.md#) operation is called to add security group rules. The key parameters for this operation include SecurityGroupId and SourceCidrIp.
4.  Wait for a short period of time and run the ping command to check whether the two ECS instances can communicate with each other over the internal network.

## Authorize internal network communication between accounts {#section_2mo_hb6_m5k .section}

1.  Query the names and security group IDs of the two accounts.

    You can obtain the IDs of the security groups to which the accounts belong by using the console or calling the [../../../../dita-oss-bucket/SP\_2/DNA0011860945/EN-US\_TP\_9865.md\#](../../../../reseller.en-US/API Reference/Instances/DescribeInstances.md#) operation. The following table lists the information of two accounts.

    |Account|Account ID|Security group|Security group ID|
    |-------|----------|--------------|-----------------|
    |Account A|a@aliyun.com|sg1|sg-bp1azkttqpldxgtedXXX|
    |Account B|b@aliyun.com|sg2|sg-bp15ed6xe1yxeycg7XXX|

2.  Add a rule to sg1 to allow inbound traffic from sg2.

    ``` {#codeblock_4vb_cvf_y8x}
    aliyun ecs AuthorizeSecurityGroup --SecurityGroupId sg-bp1azkttqpldxgtedXXX --RegionId cn-qingdao --IpProtocol all  --PortRange=-1/-1. --SourceGroupId sg-bp15ed6xe1yxeycg7XXX --SourceGroupOwnerAccount b@aliyun.com --NicType intranet
    ```

3.  Add a rule to sg2 to allow inbound traffic from sg1.

    ``` {#codeblock_uof_ae4_3y7}
    aliyun ecs AuthorizeSecurityGroup --SecurityGroupId sg-bp15ed6xe1yxeycg7XXX --RegionId cn-qingdao --IpProtocol all  --PortRange=-1/-1. --SourceGroupId sg-bp1azkttqpldxgtedXXX --SourceGroupOwnerAccount a@aliyun.com --NicType intranet
    ```

    **Note:** 

    -   In the preceding examples, region ID cn-qingdao is for reference only. Replace it with the actual region ID.
    -   In the preceding examples, the [../../../../dita-oss-bucket/SP\_2/DNA0011860945/EN-US\_TP\_9917.md\#](../../../../reseller.en-US/API Reference/Security groups/AuthorizeSecurityGroup.md#) operation is called to add security group rules. The key parameters for this operation include SecurityGroupId, SourceGroupId, and SourceGroupOwnerAccount.
4.  Wait for a short period of time and run the ping command to check whether the ECS instances in two security groups can communicate with each other over the internal network.

