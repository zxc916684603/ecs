# Release a cloud disk {#concept_bly_hrh_ydb .concept}

Release a cloud disk in the Available status if your business does not require it. Otherwise, you are charged for it. Releasing a data disk is a permanent action and is irreversible. After release, the data on the data disk cannot be restored. Proceed with caution.

## Note {#section_kyx_lrh_ydb .section}

When releasing a cloud disk, consider the following:

-   Only the cloud disks that are in the **Available** status can be released independently. Other cloud disks, such as those used as system disks or those Subscription cloud disks used as data disks, can only be released together with ECS instances.  If a cloud disk is in the **In Use** status, you must first Detach it from the instance.

-   By default, the automatic snapshots are released together with their cloud disks. However, those created manually are not. You can change the snapshot release configuration when attaching a cloud disk.

    **Note:** Each cloud disk can have up to 64 snapshots. To make sure you have sufficient storage space for the automatic snapshots, we recommend that you release automatically or manually created snapshots that your business no longer require.

-   You can have data backed up before releasing a cloud disk. For example, Create a snapshot.


## Procedure {#section_hdx_mrh_ydb .section}

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  In the left-side navigation pane, select **Block Storage** \> **Cloud Disks**.
3.  Select a region.
4.  Select the disk that you want to release \(in the **Available** status\), and in the **Actions** column, select **More** \> **Release**.
5.  In the Release dialog box, read the note and click **Confirm Release**.

## Related APIs {#section_pyx_lrh_ydb .section}

[../DNA0011860945/EN-US\_TP\_9884.md\#](../intl.en-US/API Reference/Disk/DeleteDisk.md#)

