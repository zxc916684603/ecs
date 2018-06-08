# Roll back a cloud disk {#concept_pkk_wf3_ydb .concept}

When errors occur to a cloud disk, if you have [Create snapshots](intl.en-US/User Guide/Snapshots/Create snapshots.md#) for it, you can use the **Disk Rollback** feature to restore the disk to a healthy status at a given time point.

## Note {#section_i4y_dg3_ydb .section}

Before you roll back a cloud disk, consider the following:

-   Rolling back a cloud disk is an irreversible action. Once rollback is complete, data cannot be restored. Therefore, proceed with caution.

-   After the disk is rolled back, data from the creation date of the snapshot to the rollback date is lost.

-   After a system disk is restored, the logon password or the SSH key pair of the ECS instance is retained.


## Prerequisites {#section_k4y_dg3_ydb .section}

Before rolling back a cloud disk, ascertain the following:

-   [Create snapshots](intl.en-US/User Guide/Snapshots/Create snapshots.md#) for the cloud disk, and no snapshot creation is in progress.

-   The cloud disk has not been released.

-   The cloud disk has been [attached to an ECS instance](intl.en-US/User Guide/Cloud disks/Attach a cloud disk.md#) and the instance is in the [Stopped](intl.en-US/User Guide/Instances/Start or stop an instance.md#) status.

    **Note:** For a Pay-As-You-Go VPC-Connected ECS instance, if the [../DNA0011810291/EN-US\_TP\_9595.md\#](../intl.en-US/Pricing/No fees for stopped instances (VPC-Connected).md#) feature is enabled, to stop an instance, in the Notice dialog box, click **OK**. Then in the Stop dialog box, select **Keep Instance with Fees**, and click OK to stop the instance in the Keep Instance Fees Apply mode. If you use the **No fees for stopped instances \(VPC-Connected\)** feature, you may not be able to start the instance successfully after changing the system disk.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9676/5328_en-US.png)


## Procedure {#section_o4y_dg3_ydb .section}

To roll back a cloud disk , follow these steps:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  In the left-side navigation pane, click **Instances**.
3.  Select a region.
4.  Find an instance and click its ID to go to the Instance Details page.
5.  In the left-side navigation pane, click **Instance Snapshots**.
6.  Find a snapshot, and in the **Actions** column, click  **Disk Rollback**.
7.  In the dialog box, click **OK**.

    **Note:** If you select **Start the instance immediately after the rollback**, the instance starts automatically after the disk is restored.


## Related APIs {#section_r4y_dg3_ydb .section}

[../DNA0011860945/EN-US\_TP\_9891.md\#](../intl.en-US/API Reference/Disk/ResetDisk.md#)

## Follow-up operations {#section_s4y_dg3_ydb .section}

If you resize a cloud disk after creating a snapshot, connect to the instance to resize its file system.  For more information, see:

-   [Linux \_ Resize a data disk](intl.en-US/User Guide/Cloud disks/Resize cloud disks/Linux _ Resize a data disk.md#)
-   [Windows \_ Resize a data disk](intl.en-US/User Guide/Cloud disks/Resize cloud disks/Windows _ Resize a data disk.md#)

