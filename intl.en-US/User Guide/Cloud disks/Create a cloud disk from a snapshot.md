# Create a cloud disk from a snapshot {#concept_yyn_11b_ydb .concept}

You can take a snapshot of an existing system disk or data disk, and create a cloud disk from the snapshot. The new disk can be attached to any instance in the same zone of the same region.  This article describes how to create a cloud disk from a snapshot in the ECS console.

## Scenarios {#section_bbc_ybb_ydb .section}

If you have to access data from a snapshot, but do not want to [Roll back a cloud disk](intl.en-US/User Guide/Cloud disks/Roll back a cloud disk.md#) , you can create a cloud disk from the snapshot to access data that you need. For example, if your instance encounters a system disk failure, you can use an existing snapshot to create a cloud disk, and attach the disk to a healthy instance. By doing so, you can restore the data of the impaired instance.

## Disk Performance {#section_cbc_ybb_ydb .section}

SSD Cloud Disks and Ultra Cloud Disks that are not created from snapshots can exhibit the maximum performance to its capacity, and no preconditioning is needed. However, for cloud disks created from snapshots, the initial performance decreases because data has to be accessed from OSS before being written into the disk. We recommend that you write and read every data block at least once before production use. For more information about OSS, see [What is OSS](../../../../intl.en-US/Product Introduction/What is OSS.md#).

## Note {#section_dbc_ybb_ydb .section}

Before you create a cloud disk, consider the following:

-   Only [Pay-As-You-Go](../../../../intl.en-US/Pricing/Pay-As-You-Go.md#) cloud disks can be created in this way, and they can be used as data disks only.

    **Note:** You can create cloud disks to work as data disks when creating an ECS instance. Those disks have the same billing method as that of the instance.

-   You can create a new empty cloud disk. For more information, see [Create a cloud disk](intl.en-US/User Guide/Cloud disks/Create a cloud disk.md#).
-   The quota of the Pay-As-You-Go cloud disks that are used as data disks of each account in all regions is five times than that of the Pay-As-You-Go instances. For more information, see [Limits](intl.en-US/User Guide/Limits.md#).
-   Currently, you cannot merge multiple cloud disks. After cloud disks are created, they are independent from each other, and you cannot merge their space by formatting.  We recommend that you determine the number and size before you create cloud disks.
-   You can create a snapshot for a single cloud disk, so we do not recommend that you create LVM \(Logical Volume Manager\) volumes, which may cause data loss when you use the snapshot to rollback the cloud disk.
-   After a Pay-As-You-Go cloud disk is created, you can convert its billing method to Subscription:
    -   If it is attached to a Subscription instance, use the [Upgrade configurations of Subscription instances](intl.en-US/User Guide/Instances/Change configurations/Upgrade configurations of Subscription instances.md#) feature.
    -   If it is attached to a Subscription instance, use the [Switch from Pay-As-You-Go to subscription](../../../../intl.en-US/Pricing/Switch from Pay-As-You-Go to subscription.md#) feature.
-   If a cloud disk is created in this way, and its billing method is not converted, you can [Detach a cloud disk](intl.en-US/User Guide/Cloud disks/Detach a cloud disk.md#) and [Release a cloud disk](intl.en-US/User Guide/Cloud disks/Release a cloud disk.md#) at any time.

## Prerequisites {#section_hbc_ybb_ydb .section}

Before you start, make sure the following:

-   You have created a snapshot for your instance, and you make sure the region and zone. For specific actions, see [Create snapshots](intl.en-US/User Guide/Snapshots/Create snapshots.md#).
-   because, to attach a cloud disk to an instance, they must be in the same zone of the same region.[Attach a cloud disk](intl.en-US/User Guide/Cloud disks/Attach a cloud disk.md#) The instance and the coud disk must be in the same region and zone.

## Procedure {#section_lbc_ybb_ydb .section}

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home).
2.  In the left-side navigation pane, select **Snapshots and Images** \> **Snapshots**.
3.  In the upper-right corner of the Disk List page, click **Create Cloud Disk** to go to the Create page.
4.  Select a region and zone.

    **Note:** If you want to attach the cloud disk to an ECS instance, they must be in the same zone of the same region.

5.  Configure the cloud disk:
    1.  Select a cloud disk category. The category of the source disk of the snapshot has no influence on this configuration.
    2.  Click **Create a disk with snapshot** and select a snapshot.
    3.  Specify the size of the cloud disk. The size range is 20 GiB−32768 GiB. If the selected snapshot is smaller than 20 GiB, you can adjust the size manually. For a snapshot larger than 20 GiB, the size is adjusted automatically according to the snapshot size. However, if you replace the snapshot, you must manually set the size.
    4.  For Purchase Plan, set the quantity.
6.  Check **Overview** and the cost.
7.  Click **Buy Now**, confirm you order, and make the payment.

Go back to the Cloud Disks page and refresh it. You can find the **status** of the new cloud disk is **Available** when the new disk is created successfully.

## Follow-up operations {#section_pbc_ybb_ydb .section}

[Attach a cloud disk](intl.en-US/User Guide/Cloud disks/Attach a cloud disk.md#)

## Related APIs {#section_qbc_ybb_ydb .section}

Create a cloud disk: [CreateDisk](../../../../intl.en-US/API Reference/Disk/CreateDisk.md#)

