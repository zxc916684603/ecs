# IP addresses of a classic network-connected ECS instance {#concept_lky_f3w_ydb .concept}

IP addresses are mainly used for remote access to your instance or the services deployed on your instance. Currently, in the classic network provided by Alibaba Cloud, IP addresses are uniformly distributed. They are divided into public and private IP addresses.

## Intranet IP addresses {#section_dlg_g3w_ydb .section}

Each classic network-connected ECS instance is assigned with an intranet IP address.

**Scenarios**

Intranet IP addresses can be used in the following scenarios:

-   Load balancing
-   Mutual intranet access between ECS instances
-   Mutual intranet access between ECS instances and other cloud services, such as OSS and RDS

Communication traffic through intranet IP addresses within an intranet is free of charge For more information, see[Intranet](intl.en-US/Product Introduction/Network & Security/Intranet.md#)

**Modify an intranet IP address**

Once a classic network-connected ECS instance is created, you cannot change its intranet IP address.

**Note:** Do not change an intranet IP address within a guest operating system. Otherwise, communication within an intranet gets interrupted.

## Public IP addresses {#section_hlg_g3w_ydb .section}

If you purchase bandwidth for Internet access, a public IP address is assigned to your classic network-connected ECS instance.  You cannot change the public IP address once it is assigned.

**Scenarios**

A public IP address is used in the following scenarios:

-   Mutual access between an ECS instance and the Internet
-   Mutual Internet access between ECS instances and other Alibaba Cloud services

**Assign a public IP address**

For a Pay-As-You-Go classic network-connected ECS instance  with no public IP address,

 you cannot assign a public IP address after the instance is created. For a classic network-connected ECS instance, 

**Note:** 

-   you cannot unbind or release its public IP address 
-    in the next purchase cycle, the public IP address is retained,Even if you drop through but the instance cannot access the Internet.

**Billing**

You are billed for usage of Internet outbound traffic only.  For more information,  Billing of network bandwidth.

## Multicast and broadcast {#section_nlg_g3w_ydb .section}

Intranet IP addresses cannot be used for multicast or broadcast.

