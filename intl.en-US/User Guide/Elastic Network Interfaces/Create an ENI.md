# Create an ENI {#concept_gjc_4lj_zdb .concept}

You can create an elastic network card individually. You can create an ENI in the ECS console, and then [attach it to an instance](reseller.en-US/User Guide/Elastic Network Interfaces/Attach an ENI to an instance.md).

This document describes how to create an ENI in the ECS console.

## Limits {#section_nhd_3tk_zdb .section}

To create an ENI, you have the following limits:

-   Each ENI must be in a VSwitch of a VPC.
-   Each ENI must be in one security group.

## Prerequisites {#section_phd_3tk_zdb .section}

Before you create an ENI, finish the following operations:

-   Create a VPC and then create a VSwitch in the VPC.
-   Create a security group in the same VPC.

## Procedure {#section_rhd_3tk_zdb .section}

To create an ENI, follow these steps:

1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).
2.  In the left-side navigation pane, select**Networks & Security** \> **Network Interfaces**.
3.  Select a region.
4.  Click **Create**.
5.  In the Create dialog box, finish the following configurations:
    1.  Network Interface Name: Specify a name for the ENI.
    2.  VPC: Select a VPC. When you attach an ENI to an instance, they must be in the same VPC.

        **Note:** In addition, after an ENI is created, you cannot change the VPC.

    3.  **VSwitch**: Select a VSwitch. When you attach an ENI to an instance, they must be in the same zone, but they do not have to be in the same VSwitch. 

        **Note:** In addition, after an ENI is created, you cannot change the VSwitch.

    4.  IP: Specify an IPv4 address as the private IP address of the ENI. The IPv4 address must be available in the CIDR block of the specified VSwitch. If you do not specify one, an private IP address is automatically assigned to your ENI after the ENI is created.
    5.  SecurityGroup: Select a security group in the selected VPC.
    6.  Description: Give a brief description for the ENI for easing further management.
    7.  Click **OK**.

In the Network Interfaces page, refresh the table. When the new ENI is in the Available status, it is created successfully.

## Follow-up operations {#section_whd_3tk_zdb .section}

After you create an ENI, perform the following operations:

-   [Attaching an ENI to an instance](reseller.en-US/User Guide/Elastic Network Interfaces/Attach an ENI to an instance.md).
-   [Modifying attributes of the ENI](reseller.en-US/User Guide/Elastic Network Interfaces/Modify attributes of an ENI.md).
-   [Deleting the ENI](reseller.en-US/User Guide/Elastic Network Interfaces/Delete an ENI.md).

