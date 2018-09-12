# Upgrade configurations of Subscription instances {#concept_jl1_2bf_5db .concept}

If a Subscription instance type cannot meet your business needs, you can upgrade the instance type by using the feature of upgrading configurations.

Apart from upgrading the instance type, you can use this feature to do the following:

-   **Convert the billing method of data disks**: Convert the billing method of data disks from Pay-As-You-Go to Subscription. The billing method of system disks cannot be changed.
-   **Change the Internet bandwidth**: Adjust the Internet bandwidth. This applies to the instances in a classic network and instances in a VPC that are not bound with EIPs. If you do not purchase the Internet bandwidth when creating an instance, no public IP address is assigned. In this case, you can use this feature to assign a public IP address to the instance when needed.

## Fees {#section_u4k_fyd_xdb .section}

After upgrading the configuration, you must make up the difference for the rest of the current billing cycle.

## Limits {#section_v4k_fyd_xdb .section}

This feature has the following limits:

-   Only applicable to Subscription instances.

-   The interval between two upgrades should be no less than five minutes.

-   You can only upgrade the instance type \(including vCPU cores and memory size\), but cannot upgrade one item solely.

-   Not supported within or between such instance type families: d1, d1ne, i1, i2, ga1, gn5, f1, f2, f3, ebmc4, ebmg5, sccg5, and scch5. For the instance type families that support this feature and the rules for upgrading instance types, see [instance type families that support upgrading instance types](intl.en-US/User Guide/Instances/Change configurations/Instance type families that support upgrading instance types.md#).

-   This feature can be used to change the Internet bandwidth only for VPC instances bound with no EIPs and classic network instances.

-   You can change the billing method from Pay-As-You-Go to Subscription only for data disks, not for system disks.

-   In the current billing cycle, if you have already performed the [renewal for configuration downgrade](../../../../intl.en-US/Pricing/Renew instances/Renew for configuration downgrade.md#) operation, you cannot upgrade the configuration until a new billing cycle begins. That is, the configuration cannot be upgraded during the remaining time of the current billing cycle.

-   After upgrading an instance type or changing the Internet bandwidth of a classic network instance from 0 Mbps to a non-zero value for the first time, you must restart the instance on the console or through the [RebootInstance](../../../../intl.en-US/API Reference/Instances/RebootInstance.md#) API to activate the new configuration.


## Procedure {#section_gvw_myd_xdb .section}

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home).
2.  In the left-side navigation pane, click **Instances**.
3.  Select a region.
4.  Select the Subscription instance to upgrade. In the **Actions** column, click **Change Configuration**.
5.  In the Configuration Change Guide dialog box, select **Upgrade Configuration** and click **Continue**.
6.  On the Upgrade Configuration page, perform any of the following operations:
    -   Select a new **Instance Type**.

        **Note:** The page displays all the new instance types that are available for your instance.

    -   If a [Pay-As-You-Go data disk is attached](intl.en-US/User Guide/Cloud disks/Attach a cloud disk.md#) to your instance, you can convert its billing method to Subscription.
    -   If the instance is a classic network instance or a VPC instance that is not bound with an EIP, you can modify its Internet bandwidth.

        **Note:** If you do not purchase the Internet bandwidth when creating an instance, no public IP address is assigned. In this case, you can use this feature to assign a public IP address to the instance when needed.

7.  Confirm the price, click **Create Order**, and then finish the upgrade as instructed.
8.  After upgrading an instance type or changing the Internet bandwidth of a classic network instance from 0 Mbps to a non-zero value for the first time, you must restart the instance on the console or through the [RebootInstance](../../../../intl.en-US/API Reference/Instances/RebootInstance.md#) API to activate the new configuration.

    **Note:** You do not have to restart a VPC instance if its Internet bandwidth is increased from 0 Mbps to a non-zero value for the first time.


You can also use the [DescribeResourcesModification](../../../../intl.en-US/API Reference/Others/DescribeResourcesModification.md#) API to query the instance types that can be upgraded.

