# Security groups {#concept_o2y_mqw_ydb .concept}

A security group is a logical group that groups instances in the same region with the same security requirements and mutual trust. Each instance belongs to at least one security group, which must be specified at the time of creation.  Instances in the same security group can communicate through the network, but instances in different security groups by default cannot communicate through an intranet. However, mutual access can be authorized between two security groups.

A security group is a virtual firewall that provides stateful packet inspection \(SPI\). Security groups are used to set network access control for one or more ECSs. As an important means of security isolation, security groups are used to divide security domains on the cloud.

## Security group restrictions {#section_t1g_4qw_ydb .section}

-   A single security group cannot contain more than 1,000 instances. If you require intranet mutual access between more than 1,000 instances, you can allocate them to different security groups and permit mutual access through mutual authorization.
-   Each instance can join up to five security groups.
-   Each user can have up to 100 security groups.
-   Adjusting security groups will not affect the continuity of user service.
-   Security groups are stateful. If an outbound packet is permitted, inbound packets corresponding to this connection will also be permitted.
-   Security groups have two network types: classic network and Virtual Private Cloud \(VPC\).
    -   Classic Network type instances can join security groups on classic networks in the same region.
    -   VPC type instances can join security groups on the same VPC.

## Security group rules {#section_vsf_nqw_ydb .section}

Security group rules can be set to permit or forbid ECS instances associated with security groups to access a public network or an intranet from inbound and outbound directions.

You can authorize or delete security group rules at any time. Security group rules you have changed will automatically apply to ECS instances associated with security groups.

When setting security group rules, make sure security group rules are simple. If you associate an ECS instance with multiple security groups, up to hundreds of rules may apply to the instance, which may cause connection errors when you access the instance.

## Security group rule restrictions {#section_wsf_nqw_ydb .section}

Each security group can have a maximum of 100 security group rules.

