# Create a disk from a snapshot {#concept_yyn_11b_ydb .task}

This topic describes how to create a disk in the ECS console by using a system disk snapshot or a data disk snapshot. After you create a disk, you can attach it to any instance in the same region and zone as the disk.

You have created a system disk snapshot or a data disk snapshot, and obtained the snapshot ID. For details about how to create a snapshot, see [Create a snapshot](intl.en-US/Snapshots/Use snapshots/Create a snapshot.md#).

We recommend that you create a disk from a snapshot in either of the following scenarios:

-   If you need to obtain data from a snapshot but you do not want to roll back the corresponding disk, you can create a disk from the snapshot and access the data that you need in the new disk.
-   If your ECS instance encounters problems due to a system disk failure, you can use a snapshot of the system disk to create a disk. Then attach the new disk as a data disk to a healthy ECS instance so that you can continue to read the data of the system disk.

Note the following limits on creating disks from snapshots:

-   By default, a disk created from a snapshot uses the pay-as-you-go billing method, and can only be used as a data disk. However, you can convert the billing method of the disk. For more information, see [Convert billing methods of disks](#).
-   When you access a disk created from a snapshot for the first time, you may experience a decrease in the disk performance because it takes some time for ECS to read data from OSS and write the data to the disk. We recommend that you do not use the disk until ECS finishes reading data from OSS and writing the data to the disk.
-   In each region, the number of pay-as-you-go data disks that you create cannot be more than five times the number of pay-as-you-go instances under your account. For more information, see [Limits](intl.en-US/Product Introduction/Limits.md#).
-   You cannot merge multiple disks by formatting them because they are independent of each other. Therefore, we recommend that you determine the number and capacity of disks that you need before you create them.
-   We recommend that you do not use Logical Volume Manager \(LVM\) to create logical volumes on multiple disks. This is because a snapshot can only back up data of a single disk. If you create a logical volume on several disks by using LVM, data discrepancies will occur when you roll back these disks.

By default, disks created from snapshots use the pay-as-you-go billing method. After you create a disk from a snapshot, you can convert the billing method of the disk to subscription:

-   If the disk is attached to a subscription instance, you can convert the disk billing method to subscription by upgrading the instance. For details about how to upgrade a subscription instance, see [Upgrade configurations of Subscription instances](../intl.en-US/Instances/Change configurations/Upgrade configurations/Upgrade configurations of Subscription instances.md#).
-   If the disk is attached to a pay-as-you-go instance, you can convert the disk billing method to subscription by converting the instance to a subscription instance. For details about how to convert a pay-as-you-go instance to a subscription instance, see [Switch from Pay-As-You-Go to Subscription billing](../intl.en-US/Pricing/Switch from Pay-As-You-Go to Subscription billing.md#).

You can also create a disk from a system disk snapshot or a data disk snapshot when you create an ECS instance. The disks created together with an ECS instance use the same billing method as the ECS instance.

1.  Log on to the [ECS console](https://ecs.console.aliyun.com).
2.  In the left-side navigation pane, choose **Storage & Snapshots** \> **Disks**.
3.  In the upper-right corner of the Disks page, click **Create Disk**.
4.  Select a region and zone. 

    **Note:** If you want to attach the disk to an ECS instance, they must be in the same region and zone.

5.  Complete the following settings: 
    1.  Select a disk category: **Ultra Disk**, **Enhanced SSD**, or **Standard SSD**.
    2.  Click **Create from Snapshot** and then select a snapshot. 
    3.  \(Optional\) Select **Apply Automatic Snapshot Policy** and then select an existing automatic snapshot policy. You can also create an automatic snapshot policy. For details about how to create an automatic snapshot policy, see [Create an automatic snapshot policy](../intl.en-US/Snapshots/Automatic snapshot policies/Create an automatic snapshot policy.md#).
    4.  Set the disk capacity. It must be greater than 20 GiB but less than 32,768 GiB. 

        **Note:** 

        -   If you do not set the capacity, the system automatically sets the capacity of the new disk to the snapshot size \(source disk capacity of the snapshot\).
        -   If the disk capacity you set is greater than the snapshot size, you must re-partition the disk to ensure that you can use the excess capacity.
        -   If the snapshot size is less than 2,048 GiB and you want to set the disk capacity to a value greater than 2,048 GiB, ensure that the snapshot' source disk uses the Globally Unique Identifier Partition Table \(GPT\). If the source disk does not use GPT, we recommend that you set the disk capacity to a value less than 2,048 GiB to avoid data loss that may occur during partitioning. For more information, see [Partition and format data disks larger than 2 TiB](intl.en-US/Block Storage/Block storage/Format a data disk/Partition and format data disks larger than 2 TiB.md#).
    5.  Set the Quantity parameter. 
    6.  Select **ECS Terms of Service**.
6.  Confirm your settings and the **Total** value displayed.
7.  Click **Preview**. Then, follow the on-screen tips to create the disk. After the disk is created, go back to the Disks page and refresh the disk list. Find the new disk. **Unattached** is displayed in the **Status** column corresponding to the disk.

After creating a disk from a snapshot, you must attach the disk to an ECS instance to restore the snapshot data. For a Linux instance, you also need to log on to the instance and run the mount command to mount the disk. For details about how to attach a disk, see [Attach a cloud disk](intl.en-US/Block Storage/Block storage/Attach a cloud disk.md#).

**More information**  


[../DNA0011860945/EN-US\_TP\_9883.md\#](../intl.en-US/API Reference/Disk/CreateDisk.md#)

[RunInstances](../intl.en-US/API Reference/Instances/RunInstances.md#)

[CreateInstance](../intl.en-US/API Reference/Instances/CreateInstance.md#)

