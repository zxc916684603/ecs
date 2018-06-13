# Create a cloud disk {#concept_jx1_tx1_ydb .concept}

You can create a cloud disk to work as a data disk to expand the storage space in the ECS console or by using the API. This article introduces how to create a new empty cloud disk in the ECS console.

## Notes {#section_twr_tx1_ydb .section}

Before you create a cloud disk, consider the following:

-   Only [Pay-As-You-Go](../../../../intl.en-US/Pricing/Pay-As-You-Go.md#) cloud disks can be created in this way, and they can be used as data disks only.

    **Note:** You can create cloud disks as data disks when creating an ECS instance.  Those disks have the same billing method of the instance.

-   You can create a new empty cloud disk or [Create a cloud disk from a snapshot](intl.en-US/User Guide/Cloud disks/Create a cloud disk from a snapshot.md#).
-   The quota of the Pay-As-You-Go cloud disks that are used as data disks of each account in all regions is five times than that of the Pay-As-You-Go instances. For more information, see [Limits](intl.en-US/User Guide/Limits.md#).
-   Currently, you cannot merge multiple cloud disks. After cloud disks are created, they are independent from each other, and you cannot merge their space by formatting.  We recommend that you determine the number and size before you create cloud disks.
-   You can create a snapshot for a single cloud disk, so we do not recommend that you create LVM \(Logical Volume Manager\) volumes, which may cause data loss when you use the snapshot to roll back the cloud disk.
-   After a Pay-As-You-Go cloud disk is created, you can convert its billing method to Subscription:
    -   If it is attached to a Subscription instance, use the [Upgrade configurations of Subscription instances](intl.en-US/User Guide/Instances/Change configurations/Upgrade configurations of Subscription instances.md#) feature.
    -   If it is attached to a Subscription instance, use the [Switch from Pay-As-You-Go to subscription](../../../../intl.en-US/Pricing/Switch from Pay-As-You-Go to subscription.md#) feature.
-   If a cloud disk is created in this way, and its billing method is not converted, you can [Detach a cloud disk](intl.en-US/User Guide/Cloud disks/Detach a cloud disk.md#) and [Release a cloud disk](intl.en-US/User Guide/Cloud disks/Release a cloud disk.md#) at any time.

## Prerequisites {#section_vzk_3z1_ydb .section}

If you want to[Attach a cloud disk](intl.en-US/User Guide/Cloud disks/Attach a cloud disk.md#) to an instance, make sure they are in the same region and zone.

## Procedure {#section_axr_tx1_ydb .section}

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home).
2.  In the left-side navigation pane, select **Block Storage** \> **Cloud Disks**.
3.  In the upper-right corner of the Disk List page, click **Create Cloud Disk** to go to the  Create page.
4.  Select a region and zone.

    **Note:** If you want to attach the cloud disk to an ECS instance, they must be in the same zone of the same region.

5.  Select a cloud disk category and specify the disk size and the quantity. You can also choose [Create a cloud disk from a snapshot](intl.en-US/User Guide/Cloud disks/Create a cloud disk from a snapshot.md#).
6.  Confirm the configuration and the **cost**.
7.  Click **Buy Now**, confirm you order, and make the payment.

Go back to the Cloud Disks page and refresh it. You can find the new **cloud disk status** is **Available**.

## Follow-up operations {#section_exr_tx1_ydb .section}

[Attach a cloud disk](intl.en-US/User Guide/Cloud disks/Attach a cloud disk.md#)

## Related APIs {#section_gxr_tx1_ydb .section}

To create a disk after creating an instance: [CreateDisk](../../../../intl.en-US/API Reference/Disk/CreateDisk.md#)

To create a cloud disk when creating an instance: [RunInstances](../../../../intl.en-US/API Reference/Instances/RunInstances.md#) or [CreateInstance](../../../../intl.en-US/API Reference/Instances/CreateInstance.md#)

