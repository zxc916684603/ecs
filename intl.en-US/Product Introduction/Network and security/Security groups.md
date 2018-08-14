# Security groups {#concept_o2y_mqw_ydb .concept}

A security group is a virtual firewall that provides stateful packet inspection \(SPI\). Security groups are used to set network access control for one or more ECS instances. As an important means of security isolation, security groups are used to divide security domains on the cloud.

A security group is a logical group that contains instances in the same region with the same security requirements and mutual trust. Each instance belongs to at least one security group, which must be specified at the time of creation. Instances in the same security group can communicate through the intranet network, but instances in different security groups cannot communicate by default. However, mutual access between two security groups can be authorized.

## Security group restrictions {#section_t1g_4qw_ydb .section}

-   A single security group cannot contain more than 1,000 instances. If you require intranet mutual access between more than 1,000 instances, you can allocate them to different security groups and authorize mutual access.
-   Each instance can join up to five security groups by default. You can [open a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex) to raise the upper limit to a maximum of 16.
-   There a maximum limit for the number of security groups you can have for a region. The limit depends on your level of experience with Alibaba Cloud. For new users, the limit is 100 security groups. For more experienced users, the limit is higher.
-   Adjusting security groups will not affect the continuity of user service.
-   Security groups are stateful. If an outbound packet is permitted, inbound packets corresponding to this connection will also be permitted.
-   Security groups have two network types: classic network and Virtual Private Cloud \(VPC\).
    -   Classic network instances can join security groups on classic networks in the same region.
    -   VPC instances can join security groups on the same VPC.

## Security group rules {#section_vsf_nqw_ydb .section}

Security group rules can be set that permit or forbid ECS instances in a security group from accessing a public network or intranet in the inbound and outbound directions.

You can create or delete security group rules at any time. Once changes are made, the updated security group rules are automatically applied to ECS instances in the security group.

When setting security group rules, make sure they are concise. If you add an ECS instance to multiple security groups, hundreds of rules may apply to the instance, which may cause connection errors when you access the instance.

## Security group rule restrictions {#section_wsf_nqw_ydb .section}

Each security group can have a maximum of 100 security group rules.

