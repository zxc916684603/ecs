# Increase system disk size {#concept_kj1_mqg_ydb .concept}

To meet the growing business demands, you can increase the size of the system disk of your ECS instance by using **Change System Disk**  feature. This article introduces how to increase the size of a system disk while keeping the operating system and environment intact.

**Note:** You can change the operating system while increasing the size of a system disk. For more information, see [EN-US\_TP\_9640.md\#](intl.en-US/User Guide/Instances/Change the operating system.md#).

## Notes {#section_bff_fwh_ydb .section}

Before you begin, consider the following.

**Risks**

The risk of replacing the system disk is as follows:

-   You have to stop your instance to change its system disk, which may interrupt your business operations.
-   After replacement, you must redeploy the business runtime environment on the new system disk. There is a possibility of a long interruption of your business.
-   After the system disk is changed, a new cloud disk with a new disk ID is assigned, and the old one is released. Therefore, you cannot roll back the system disk by using any snapshot of the released cloud disk.

    **Note:** After the system disk is changed, you can still use those manually created snapshots of the released disk to create custom images. If you have applied an automatic snapshot policy to the old system disk and set the automatic snapshots to release when the disk is released, you must apply the policy to the new disk. Besides, all the automatic snapshots of the old disk are released.


**Limits and recommendations**

When changing the system disk, you must consider the following:

-   After the system disk is changed, your instance is assigned a new cloud disk as the system disk, with a new disk ID, and the old one is released.
-   You cannot replace the Cloud Type of the system disk.
-   After expansion,  the minimum capacity is as much as before, while the maximum capacity is 500 GiB. The capacity of the system disk cannot be reduced.
-   You cannot increase the size of the system disk that runs Windows 2003.
-   If your Subscription instance has been renewed for configuration downgrade, [../../../../dita-oss-bucket/SP\_2/DNA0011810291/EN-US\_TP\_9593.md\#](../../../../intl.en-US/Pricing/Renew instances/Renew for configuration downgrade.md#) you cannot modify the system disk capacity until you enter the next billing cycle.
-   The IP address and the MAC address remain unchanged after the system disk is changed.
-   We recommend that you create a snapshot for the system disk before you change the disk. Consider the following when creating the snapshot:
    -   We recommend that you create snapshots at off-peak business hours.  It may take about 40 minutes to create a snapshot of 40 GiB.  to create a snapshot of 40 GiB.  Therefore, leave sufficient time to create a snapshot. Creation of a snapshot may reduce the I/O performance of a block storage device, generally it is less than 10%, which results in sharp decrease in I/O speed.
    -   Make sure the system disk has enough available storage space when creating a snapshot, at least 1 GiB. Otherwise, the system may fail to start after the system disk is changed.
-   To make sure you have enough quota for automatic snapshots of the new system disk, you can delete the unnecessary snapshots of the old system disk. For more information, see [EN-US\_TP\_9691.md\#](intl.en-US/User Guide/Snapshots/Delete snapshots or automatic snapshot policies.md#).

## Procedure {#section_hff_fwh_ydb .section}

If you want to increase the size of the system disk while keeping the operating system and environment intact, follow these steps:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  In the left-side navigation pane, click **Instances**.
3.  Select a region.
4.  Find an instance to change the system disk, click the instance ID to go to the Instance Details page.
5.  Follow these steps to create a snapshot of the system disk:
    1.  In the left-side navigation pane, click **Instance Disks**.
    2.  Locate the system disk,  find **Actions**, and click  **Create Snapshot**.

        **Note:** For more information about the limits or note for creating a snapshot, see [EN-US\_TP\_9687.md\#](intl.en-US/User Guide/Snapshots/Create snapshots.md#).

6.  Follow these steps to create a custom image by using the snapshot:
    1.  In the left-side navigation pane, click **Instance Snapshots** to check the creation status and progress. When the progress is 100% and the status is  **Success**, in the **Actions** column, click **Create Custom Image**.

        **Note:** 

        -   For more information about the limits or note for creating a custom image, see [EN-US\_TP\_9696.md\#](intl.en-US/User Guide/Images/Create custom image/Create a custom mirror using a snapshot.md#).
        -   The custom image is displayed in the dropdown ist of the **Custom Image** l on the Replace System Disk page.
    2.  Go back to the  Instances. In the left-side navigation pane, select **Snapshots & Images** \> **Image**to check the creation status and progress of the custom image.
7.  When the progress is 100% and the status is **Available**, in the left-side navigation pane, click  **Instances**.
8.  In the Instance List, find the instance, and in the **Actions** column, select **More** \> **Stop**.

    **Note:** For a Pay-As-You-Go VPC-Connected ECS instance, if the [../../../../dita-oss-bucket/SP\_2/DNA0011810291/EN-US\_TP\_9595.md\#](../../../../intl.en-US/Pricing/No fees for stopped instances (VPC-Connected).md#) feature is enabled, in the Notice dialog box, click **OK**,  On the in the Stop dialog box, select **Keep Instance with Fees**, and click OK to stop the instance in the Keep Instance Fees Apply mode. If you use the **No fees for stopped instances \(VPC-Connected\)** you may not be able to start the instance successfully after changing the system disk.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9676/5328_en-US.png)

9.  When the instance is in the **Stopped** status, in the Actions column, select**Action** **More** \> **Replacing the system tray**.
10. In the pop-up dialog box, after carefully reading the notes about replacing the system tray, click **OK, replace the system disk**.
11. On the Change System Disk page, complete the configurations:
    1.  **Image type**: Click the **Custom Image** tab  and select the created custom image in the drop-down list.
    2.  **System disk**: Specify a new size for the system disk according to your business needs. The maximum size is 500 GiB.  GiB.  The size limit for changing is determined by the image and the current size of the system disk, as displayed in the following table.

        |Image|Capacity Limit for capacity expansion \(GiB\)|
        |:----|:--------------------------------------------|
        |Linux \(excluding CoreOS\) + FreeBSD|\[Max\{20, current size of the system disk\}, 500\]|
        |CoreOS|\[Max\{30, current size of the system disk\}, 500\]|
        |Windows|\[Max\{40, current size of the system disk\}, 500\]|

        **Note:** You cannot modify the Cloud Type of the system tray.

    3.  **Security**:
        -   If a Windows image is used, set a logon password.
        -   If a Linux image is used and the instance is I/O optimized,  you can choose to set a password or bind an SSH key pair for logon.
    4.  Confirm the **configuration cost**: includes the price of the mirror and the price of the system disk. For more information, see [Cloud Product Price](https://www.alibabacloud.com/zh/product/ecs#pricing).
    5.  Click ECS Service Terms and Product Terms of Service and then click **Confirm to change**.

Go back to the ECS console to check the status of the process. It may take a few minutes to process the change. After the system disk is changed, the instance starts automatically.

## Follow-up operations {#section_xff_fwh_ydb .section}

After the system disk is changed, you may have to perform the following:

-   If your instance is running a Linux image and any data disk has been attached to the instance and set to automatically mount the file systems at the beginning, the mount information is lost while changing the system disk. Therefore, you must write the new partition and mounting information to the /etc/fstab file on the new system disk and mount the file systems. You must not partition or format the data disk again. Follow these steps to mount the file systems.  For more information about the commands, see [../../../../dita-oss-bucket/SP\_2/DNA0011854887/EN-US\_TP\_9604.md\#](../../../../intl.en-US/Quick Start for Entry-Level Users/Step 4: Format a data disk/Linux _ Format and mount a data disk.md#):
    1.  \(Optional\) Make backup of the /etc/fstab file.
    2.  Write the new partition and mounting information to the /etc/fstab file.
    3.  Check the new partition information in the /etc/fstab file.
    4.  Mount the file systems.
    5.  To view disk space and usage: run the command `df -h`.

        After mounting, do not need to restart the instance to use the new file system directly.

-    [EN-US\_TP\_9689.md\#](intl.en-US/User Guide/Snapshots/Apply automatic snapshot policies to disks.md#). Optionally, apply an automatic snapshot policy to the new system disk.  The link between an automatic snapshot policy ID and a disk ID is broken after the system disk is changed.  You need to set up an automatic snapshot policy for the new system disk.

