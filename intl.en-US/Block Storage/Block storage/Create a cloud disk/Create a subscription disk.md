# Create a subscription disk {#concept_apf_b4z_bgb .task}

This topic describes how to create an empty subscription disk in the ECS console. You can increase the storage space of an instance by attaching a subscription disk to it.

You can use either of the following methods to create a subscription disk:

-   Create a subscription disk and attach it to an ECS instance in the ECS console.
-   When you create an ECS instance, set its billing method to subscription and create disks for the instance. All the disks created together with this instance use the subscription billing method. For more information, see [Create an instance](../reseller.en-US/Instances/Create an instance/Create an instance by using the wizard.md#).

Note the following limits on creating subscription disks:

-   Subscription disks cannot be detached. They are released along with the instances to which they are attached. If you want to release a subscription disk, you can convert it to a pay-as-you-go disk, and then detach and release it.

For information about the subscription billing method, see [Subscription](../reseller.en-US/Pricing/Subscription.md#).

1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).
2.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.
3.  In the top navigation bar, select a region.
4.  On the Instances page, find the subscription instance for which you want to create a subscription disk. In the **Actions** column, choose **More** \> **Configuration Change** \> **Add Subscription Disk**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/79763/156871446839720_en-US.png)

5.  In the **Disk** section on the page that appears, complete the following settings: 

    -   Disk category: Select a disk category from the drop-down list. For information about how to select enhanced SSDs, see [ESSD cloud disk](reseller.en-US/Block Storage/Block storage/ESSD cloud disk.md#).
    -   Disk capacity: Enter a capacity for the disk. The allowed capacity ranges from 20 GiB to 32,768 GiB.
    -   Disk encryption: Select **Disk Encryption** if required. For information about the disk encryption feature, see [ECS disk encryption](../reseller.en-US/Block Storage/Block storage/ECS disk encryption.md#).
    -   \(Optional\) Select **Apply Automatic Snapshot Policy** and then select an existing automatic snapshot policy.

        You can also create an automatic snapshot policy. For details about how to create an automatic snapshot policy, see [Create an automatic snapshot policy](../reseller.en-US/Snapshots/Automatic snapshot policies/Create an automatic snapshot policy.md#).

    -   Quantity: Enter the number of disks you want to purchase.

        **Note:** You can create a total of 16 data disks for a single instance. Disks and Shared Block Storage devices used as data disks count towards this total.

    -   \(Optional\) Disk Name: Enter a name for the disk.
    -   \(Optional\) Description: Enter a description for the disk.
    -   To create a disk from a snapshot, click **Create from Snapshot**. For more information, see [Create a disk from a snapshot](reseller.en-US/Block Storage/Block storage/Create a cloud disk/Create a disk from a snapshot.md#).
    ![Creating a disk](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/79763/156871446834128_en-US.png)

6.  Select *ECS Terms of Service* .
7.  Click **Preview**.
8.  In the dialog box that appears, confirm the parameter settings and click **Create**.
9.  Select a payment method and click **Confirm to Pay** to make payment.
10. Click **Console** and go to the **Instances** page. Click the name of the instance to which the new subscription disk is attached.
11. Click **Disks** in the left-side navigation pane. In the disk list, find the subscription disk that you created. The disk is attached to the instance and is in the **In use** state.

-   To format and partition the disk, see [Format a data disk of a Linux instance](../reseller.en-US/Quick Start for Entry-Level Users/Step 4. Format a data disk/Format a data disk of a Linux instance.md#) or [Format a data disk for a Windows instance](../reseller.en-US/Quick Start for Entry-Level Users/Step 4. Format a data disk/Format a data disk for a Windows instance.md#).
-   To convert the disk to a pay-as-you-go disk, see [Convert the billing methods of cloud disks](reseller.en-US/Block Storage/Block storage/Convert the billing methods of cloud disks.md#).

**More information**  


[../DNA0011860945/EN-US\_TP\_9883.md\#](../reseller.en-US/API Reference/Disk/CreateDisk.md#)

[RunInstances](../reseller.en-US/API Reference/Instances/RunInstances.md#)

[CreateInstance](../reseller.en-US/API Reference/Instances/CreateInstance.md#)

