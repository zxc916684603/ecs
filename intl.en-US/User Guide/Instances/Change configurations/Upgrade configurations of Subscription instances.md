# Upgrade configurations of Subscription instances {#concept_jl1_2bf_5db .concept}

The **Upgrade Configuration** feature helps you to upgrade the specifications of your Subscription instances to meet your business needs. However, you may have to pay the price difference  for the upgrade. While you are changing the instance type, you can also perform any of the following operations:

-   **Convert the billing method of cloud disks** that are used as data disks from Pay-As-You-Go to Subscription. Note that you cannot change the billing method of system disks.
-   **Adjust the Internet bandwidth** of a VPC-Connected ECS instance that no EIP address is bound to or a classic network-connected ECS instance. You can use this feature to assign an Internet IP address to the instance.

## Fees {#section_u4k_fyd_xdb .section}

After upgrading the configuration, you must make up the difference for the rest of the current billing cycle.

## Limits {#section_v4k_fyd_xdb .section}

This section introduces how to **upgrade configurations** in the ECS console. 

-   It is only applicable to Subscription instances.

-   You can use it to upgrade the specifications of vCPU and RAM simultaneously, but not separately, by changing the instance type.

-   Some instance types are not supported. For more information, see [Instance type families](../intl.en-US/Product Introduction/Instance type families.md#).

-   It can be used to change Internet bandwidth of only VPC-Connected ECS instances that no EIP address is bound to and classic network-connected ECS instances.

-   It can be used to change the billing method of cloud disks that are used as data disks, but not that of system disk.

-   During the current billing cycle, if you have performed the Renew for Configuration Downgrade operation, [Renew for configuration downgrade](../intl.en-US/Pricing/Renew instances/Renew for configuration downgrade.md#) you cannot upgrade configurations until the next billing cycle.

-   After you change the instance types or increase the Internet bandwidth of a classic network-connected ECS instance from 0 Mbit/s to a non-zero value for the first time, you must restart the instance in the ECS console [RebootInstance](../intl.en-US/API Reference/Instances/RebootInstance.md#) or by using the RebootInstance interface for the new configuration to take effect.


## Procedure {#section_gvw_myd_xdb .section}

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home).
2.  In the left-side navigation pane, click **Instances**.
3.  Select a region.
4.  In the , find your instance, and in the **Actions** column, click **Change Configuration**.
5.  In the Configuration Change Guide dialog box, select **Upgrade Configuration** and click **Continue**.
6.  On the Upgrade Configuration page, perform any of the following operations:
    -   Select a new **Instance Type**.

        **Note:** The page displays all the new instance types that are available for your instance.

    -   If a Pay-As-You-Go data disk is [Attach a cloud disk](intl.en-US/User Guide/Cloud disks/Attach a cloud disk.md#) to your instance, you can **convert its billing method to Subscription**.

    -   If the instance is a classic network type instance or a VPC type instance that is not bound to an EIP, you can modify the bandwidth values.

        **Note:** If you do not purchase Internet bandwidth when you create the instance, that is, the Internet IP address is not assigned, you can assign an Internet IP address here by setting the Internet bandwidth to a non-zero value.

        ![](images/5422_en-US.png)

7.  Click **Pay** to complete the order.
8.  If you have changed the instance type, or if you have increased the bandwidth from 0 Mbit/s for your classic network-connected ECS instance, restart the instance in the console [RebootInstance](../intl.en-US/API Reference/Instances/RebootInstance.md#) or by using the RebootInstance interface.

    **Note:** You do not have to restart a VPC-Connected ECS instance if its bandwidth is increased from 0 Mbit/s for the first time.


