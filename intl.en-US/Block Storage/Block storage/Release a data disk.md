# Release a data disk {#concept_bly_hrh_ydb .concept}

We recommend you release a data disk when you no longer require it to avoid incurring excess fees. Releasing a data disk is a permanent, irreversible action and is irreversible. After its release, data on the cloud disk cannot be restored, exercise caution when performing this action.

## Note {#section_kyx_lrh_ydb .section}

When releasing a cloud disk, note that:

-   Only cloud disks that are in the **Available** state can be released independently. Other cloud disks, such as those used as system disks, or Subscription billed cloud disks used as data disks, can only be released together with ECS instances. If a cloud disk is in the **In Use** state, you must first detach it from the instance.
-   By default, automatic snapshots are released together with their cloud disks. However, manually created snapshots are not. You can change the snapshot release configuration when attaching a cloud disk.

    **Note:** To make sure you have sufficient storage space for the automatic snapshots, we recommend that you release automatically or manually created snapshots that you no longer require. For more information about snapshot quota, see [Limits](../reseller.en-US/Product Introduction/Limits.md#).

-   You can have data backed up before releasing a cloud disk. For example, by creating a snapshot.

## Procedure {#section_hdx_mrh_ydb .section}

1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).
2.  In the left-side navigation pane, choose **Storage & Snapshots** \> **Disks**.
3.  In the top navigation bar, select a region.
4.  Select the disk that you want to release and make sure that it is in the **Unattached** state. Then, in the **Actions** column, choose **More** \> **Release**.
5.  In the Release Disk dialog box, read the note and click **Confirm Release**.

## Related API {#section_pyx_lrh_ydb .section}

[DeleteDisk](../reseller.en-US/API Reference/Disk/DeleteDisk.md#)

