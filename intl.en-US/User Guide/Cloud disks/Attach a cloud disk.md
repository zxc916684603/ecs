# Attach a cloud disk {#concept_llz_b4c_ydb .concept}

You can create a cloud disk and attach it to an ECS instance to work as a data disk.  You have two options to attach a cloud disk: attach them on the Instance Disks page or on the Disk List page. Before you attach a cloud disk to an ECS instance, consider the following:

-   If you want to attach multiple cloud disks to one ECS instance, attach them on the Instance Disks page. 
-   If you want to attach multiple cloud disks to various ECS instances, attach them on the Disk List page.

## Note {#section_utx_d4c_ydb .section}

Before you attach a cloud disk to an ECS instance, consider the following:

-   If a cloud disk is created together with an ECS instance, you do not have to attach the disk.
-   You can attach a cloud disk to work as a data disk only, but not as a system disk.
-   To attach a cloud disk to an ECS instance, the instance must meet the following requirements:
    -   The instance must be in the**Running**（Running）or **Stopped** status \(Stopped\) , but not  in the **Locked** status \(Locked\).
    -   The instance must not have payment overdue.
-   The disk to be attached must be in the  **Available**status.
-   The cloud disk and the ECS instance must be in the same region and the same zone.
-   Up to 16 cloud disks can be attached to an ECS instance to work as data disks. One cloud disk cannot be attached to multiple instances simultaneously.
-   A cloud disk can be attached to an ECS instance, regardless of the billing method of the instance.

## Prerequisites {#section_xtx_d4c_ydb .section}

You must create an ECS instance and a cloud disk in the same region and zone. For more information, see  [Create a cloud disk](intl.en-US/User Guide/Cloud disks/Create a cloud disk.md#)and the [../DNA0011854887/EN-US\_TP\_9601.md\#](../intl.en-US/Quick Start for Entry-Level Users/Step 2. Create an instance.md#) in Quick Start.

## Attach a cloud disk on the Instance Disks page {#section_ytx_d4c_ydb .section}

To attach one or multiple cloud disks to a specified ECS instance, follow these steps:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  In the left-side navigation pane, click **instances**.
3.  Select a region.
4.  Find an ECS instance and click its ID to go to the Instance Details page.
5.  In the left-side navigation pane, click **Instance Disks**, and on the Disk List page, click **Attach Disk**.

    ![](images/4420_en-US.png)

6.  In the dialog box, complete the following configurations:
    -   **Target Disk**: Select a cloud disk in the **Available** status  in the same region and zone.
    -   **Release Disk with Instance**: If you select this option, the disk is released when you release its instance.
    -   **Delete automatic snapshots when releasing disk**: If you select this option, all the automatic snapshots of the target disk are deleted when you release it. However, all the manual snapshots are retained.  To keep complete data backup, we recommend that you do not select this option. 

        Click **OK**, and then **Attach.**.

        ![](images/4421_en-US.png)

7.  Refresh the Disk List. 

    When the status of the cloud disk is **In Use**, the attachment is successful.

8.  According to the content of the cloud disk and the operating system of the ECS instance, perform different operations to make the disk ready for use. As shown in the following table.

    |Disk content|Operating system of the ECS instance|Follow-up operations|
    |:-----------|:-----------------------------------|:-------------------|
    |A new empty cloud disk|Linux|[../DNA0011854887/EN-US\_TP\_9604.md\#](../intl.en-US/Quick Start for Entry-Level Users/Step 4: Format a data disk/Linux _ Format and mount a data disk.md#). If the cloud disk is larger than 2 TiB, see  [Partition and format data disk more than 2 TB](intl.en-US/User Guide/Cloud disks/Partition and format data disk more than 2 TB.md#).|
    |Windows|[Windows \_ Format a data disk](../intl.en-US/Quick Start for Entry-Level Users/Step 4: Format a data disk/Windows _ Format a data disk.md#). If the cloud disk is larger than 2 TiB, see [Partition and format data disk more than 2 TB](intl.en-US/User Guide/Cloud disks/Partition and format data disk more than 2 TB.md#).|
    |A cloud disk from a snapshot|Linux|Connect to the Linux instance and run the `mount` command to mount the partitions to make the disk ready for use.|
    |Windows| The cloud disk is ready for use.|


## Attach a cloud disk on the Disk List page {#section_i5x_d4c_ydb .section}

To attach a cloud disks to an ECS instances, follow these steps:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  In the left-side navigation pane, select  ** Block Storage \> ** \> **Cloud Disks**.
3.  Select a region.
4.  Find a cloud disk in the **Available** status, and in the **Actions** column, select  **More \> ** \> **Attach**.

    ![](images/4422_en-US.png)

5.  In the dialog box, complete the following configurations:
    -   **Target Instance**: Select an ECS instance in the same zone.
    -   **Release Disk with Instance**: If you select this option, the disk is released when you release its instance.
    -   **Delete automatic snapshots when releasing disk**: If you select this option, all the automatic snapshots of the selected disk are deleted when you release the disk. However, all the manual snapshots are retained. To keep complete data backup, we recommend that you do not select this option. 

        Click **Attach**.

        ![](images/4423_en-US.png)

6.  Refresh the disk list. 

    When the status of the cloud disk is  **In Use**, the attachment is successful.

7.  According to the content of the cloud disk and the operating system of the ECS instance, perform different operations to make the disk ready for use. As shown in the following table.

    |Disk content|Operating system of the ECS instance|Follow-up operations|
    |:-----------|:-----------------------------------|:-------------------|
    |A new empty cloud disk|Linux|[../DNA0011854887/EN-US\_TP\_9604.md\#](../intl.en-US/Quick Start for Entry-Level Users/Step 4: Format a data disk/Linux _ Format and mount a data disk.md#). If the cloud disk is larger than 2 TiB, see [Partition and format data disk more than 2 TB](intl.en-US/User Guide/Cloud disks/Partition and format data disk more than 2 TB.md#).|
    |Windows|[Windows \_ Format a data disk](../intl.en-US/Quick Start for Entry-Level Users/Step 4: Format a data disk/Windows _ Format a data disk.md#). If the cloud disk is larger than 2 TiB, see [Partition and format data disk more than 2 TB](intl.en-US/User Guide/Cloud disks/Partition and format data disk more than 2 TB.md#).|
    |A cloud disk from a snapshot|Linux| Connect to the Linux instance and run the  `mount`command to mount the partitions to make the disk ready for use.|
    |Windows| The cloud disk is ready for use.|


## Follow-up operations {#section_r5x_d4c_ydb .section}

After a cloud disk is attached to an ECS instance, you can perform one of the following operations according to your business needs:

-   Reinitialize [EN-US\_TP\_9679.md\#](intl.en-US/User Guide/Cloud disks/Reinitialize a cloud disk.md#)a cloud disk to restore it to the initial status after it is created.
-   You can increase the size of the cloud disk by resizing it.  For more information, see [Linux \_ Resize a data disk](intl.en-US/User Guide/Cloud disks/Resize cloud disks/Linux _ Resize a data disk.md#) or [Windows \_ Resize a data disk](intl.en-US/User Guide/Cloud disks/Resize cloud disks/Windows _ Resize a data disk.md#).
-   You can create a snapshot  [Create snapshots](intl.en-US/User Guide/Snapshots/Create snapshots.md#) of the cloud disk to back up data. Alternatively, you can [Apply automatic snapshot policies to disks](intl.en-US/User Guide/Snapshots/Apply automatic snapshot policies to disks.md#) create an automatic snapshot policy and apply it to the disk to create snapshots automatically.
-   If you want to restore the cloud disk to the status at a given time point, you can use its snapshot to [Roll back a cloud disk](intl.en-US/User Guide/Cloud disks/Roll back a cloud disk.md#) roll back the disk.
-   If your instance does not need a cloud disk, to reduce the cost, you can  [Detach a cloud disk](intl.en-US/User Guide/Cloud disks/Detach a cloud disk.md#) detach and [Release a cloud disk](intl.en-US/User Guide/Cloud disks/Release a cloud disk.md#) release it.

## Related APIs {#section_u5x_d4c_ydb .section}

[AttachDisk](../intl.en-US/API Reference/Disk/AttachDisk.md#)

