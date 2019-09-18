# Create a pay-as-you-go disk {#concept_jx1_tx1_ydb .task}

This topic describes how to create an empty pay-as-you-go disk in the ECS console. You can increase the storage space of an instance by attaching a pay-as-you-go disk to it. You cannot create a separate system disk in the ECS console.

You can use either of the following methods to create a pay-as-you-go disk:

-   Log on to the ECS console. In the left-side navigation pane, choose **Storage & Snapshots** \> **Disks** to create a pay-as-you-go disk.
-   When you create an ECS instance, set its billing method to pay-as-you-go and create disks for the instance. All the disks created together with this instance use the pay-as-you-go billing method. For more information, see [Create an instance](../reseller.en-US/Instances/Create an instance/Create an instance by using the wizard.md#).

Note the following limits on creating pay-as-you-go disks:

-   In each region, the number of pay-as-you-go data disks that you create cannot be more than five times the number of pay-as-you-go instances under your account. For more information, see [Limits](reseller.en-US/Product Introduction/Limits.md#).
-   You cannot merge multiple disks by formatting them because they are independent of each other. Therefore, we recommend that you determine the number and capacity of disks that you need before you create them.
-   We recommend that you do not use Logical Volume Manager \(LVM\) to create logical volumes on multiple disks. This is because a snapshot can only back up data of a single disk. If you create a logical volume on several disks by using LVM, data discrepancies will occur when you roll back these disks.

For information about the pay-as-you-go billing method, see [Pay-As-You-Go](../reseller.en-US/Pricing/Pay-As-You-Go.md#).

You can also watch the following video to learn how to create, attach, and format a disk: [Attach a disk to a Windows instance](https://help.aliyun.com/document_detail/54748.html).

1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).
2.  In the left-side navigation pane, choose **Storage & Snapshots** \> **Disks**.
3.  In the upper-right corner of the Disks page, click **Create Disk**.
4.  Select the region and zone of the instance to which you want to attach the disk.
5.  Select a disk category and specify the disk capacity. Select **Disk Encryption** if required and set the Quantity parameter to specify the number of disks you want to purchase. 

    ![Creating a disk](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9669/15687707844412_en-US.png)

    **Note:** 

    -   Select **Apply Automatic Snapshot Policy** and then select or create an automatic snapshot policy to create automatic snapshots of the disk based on the policy. For details about how to create an automatic snapshot policy, see [Create an automatic snapshot policy](../reseller.en-US/Snapshots/Automatic snapshot policies/Create an automatic snapshot policy.md#).
    -   To check whether a disk needs to be encrypted, see [EN-US\_TP\_9560.md\#](reseller.en-US/Block Storage/Block storage/ECS disk encryption.md#).
    -   You can also create the disk from a snapshot. For more information, see [Create a disk from a snapshot](reseller.en-US/Block Storage/Block storage/Create a cloud disk/Create a disk from a snapshot.md#).
    -   For information about how to select enhanced SSDs, see [ESSD cloud disk](reseller.en-US/Block Storage/Block storage/ESSD cloud disk.md#).
6.  Select the terms of services in the Terms of Service section.
7.  Confirm your settings and the **Total** value displayed.
8.  Click **Preview**. In the dialog box that appears, click **Create**.

After the disk is created, go back to the Disks page and refresh the disk list.

**Unattached** is displayed in the **Status** column corresponding to the new disk.

-   To attach the disk to an ECS instance, see [Attach a cloud disk](reseller.en-US/Block Storage/Block storage/Attach a cloud disk.md#).
-   To convert the disk to a subscription disk, see [Convert the billing methods of cloud disks](reseller.en-US/Block Storage/Block storage/Convert the billing methods of cloud disks.md#).

**More information**  


[../DNA0011860945/EN-US\_TP\_9883.md\#](../reseller.en-US/API Reference/Disk/CreateDisk.md#)

[RunInstances](../reseller.en-US/API Reference/Instances/RunInstances.md#)

[CreateInstance](../reseller.en-US/API Reference/Instances/CreateInstance.md#)

