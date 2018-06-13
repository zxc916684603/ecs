# Change a system disk \(public image\) {#concept_n4k_x3j_ydb .concept}

If you want to change the operating system running on your instance, you can use the Change System Disk feature to complete it.By changing a system disk, the system disk of your instance is replaced with a new cloud disk, which has a new disk ID, and the original system disk is released. If you want to change the operating system running on your instance,  you can use the **Change System Disk** feature to complete it. You can replace the OS image with a public image, shared image, custom image, or an image from the image marketplace.

**Note:** Microsoft has terminated technical support for Windows Server 2003. To guarantee your data security, we do not recommend that you continue running Windows Server 2003 on your ECS instance,  This image is no longer available on the 2003 system. For more information, refer to [About Alibaba Cloud no longer supports Windows Server 2003 system mirroring](https://www.alibabacloud.com/help/faq-detail/59513.htm).

After replacing the system tray,

-   a new system disk with a new disk ID is assigned to your instance, and the original one is released.

-   The cloud type of the system disk cannot be replaced.

-   The IP address and the MAC address remain unchanged after the system disk is changed.

-   To make sure that your account have enough snapshot quota for the new system disk, you can delete unnecessary snapshots of the original system disk.


This article describes how to replace an existing image with a public image.  If you need to use a non-public mirror, refer to [EN-US\_TP\_9683.md\#](intl.en-US/User Guide/Cloud disks/Change the system disk (custom image).md#).

## Notes {#section_h1y_y3j_ydb .section}

Before you begin, consider the following.

**Risks**

The risk of replacing the system tray is as follows:

-   You have to stop your instance to change its system disk, which may interrupt your business operations.

-   After replacement, you must redeploy the business runtime environment on the new system disk. There is a possibility of a long interruption of your business.

-   Once you change the system disk, a new system disk, which has a new disk ID, is assigned. It means you cannot use all the snapshots of the original system disk to roll back the new system disk.

    **Note:** After you replace the system tray, the snapshot that you manually created is not affected, you can still create custom mirrors with these snapshots.  If you have applied automatic snapshot policies to the original system disk, and set the auto snapshots to be released with the disk, the snapshot policies cannot work any more and all the auto snapshots of the original system disk are deleted automatically.


**Considerations for changing between Windows and Linux**

Regions that are not in mainland China do not support replacement between Linux and Windows. 

**Note:** For instances in those regions, a Linux or Windows edition can be only replaced by another edition of the same operating system type.

After the OS is changed between Windows and Linux, the file systems of the data disks cannot be recognized.

-   If you do not have important data on the data disk, we recommend that you reinitialize the disk and format it to a recognizable file system.

-   If you have important data on the data disk, follow these tips:

    -   Replacing Windows with Linux: Install a software application, such as NTFS-3G, because the NTFS file system cannot be recognized by a Linux OS by default.
    -   Replacing Linux with Windows: Install a software application, such as Ext2Read or Ext2Fsd, because ext3, ext4, and xfs cannot be recognized by a Windows OS by default.

When you replace a Windows edition with a Linux edition, two authentication methods are available: a password and an SSH key pair.

## Prerequisites {#section_n1y_y3j_ydb .section}

If you want to change the OS to a Linux edition and to use an SSH key pair as the authentication method, create an SSH key pair.

Changing a system disk is so highly risky that it may cause data loss and business interruption. To minimize the impact of this operation, we recommend that you create a snapshot for the system disk.

**Note:** 

-   We recommend that you create snapshots at off-peak business hours.  It may take about 40 minutes to create a snapshot of 40 GiB. Therefore, leave sufficient time to create a snapshot.
-   To create a snapshot, make sure the system disk has sufficient space available. We recommend that at least 1 GiB storage space is reserved. Otherwise, the instance cannot be started after the system disk is changed.

## Procedure {#section_p1y_y3j_ydb .section}

Replace your system disk as follows:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  In the left-side navigation pane, click **Instances**.
3.  Select a region.
4.  Find an instance, and in the **Actions** column, select **More** \> **Stop**and follow the prompts on the page to stop the instance.

    **Note:** For a Pay-As-You-Go VPC-Connected ECS instance, if the No fees for stopped instances \(VPC-Connected\) feature is enabled, in the Notice dialog box, click **OK**,  On the Stop dialog box, select  **Keep Instance with Fees** and click OK to stop the instance in the Keep Instance, Fees Apply mode.  If you use the **No fees for stopped instances \(VPC-Connected\)** Otherwise, you may not be able to start the instance successfully after changing the system disk.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9676/5328_en-US.png)

5.  in the **Actions** column, select **More** \> **Replacing the system disk**.
6.  In the pop-up dialog box, after carefully reading the notes about replacing the system tray, click **OK, replace the system disk**.
7.  On the Change System Disk page, complete the configurations:
    1.  **Image type**:  Select **Public Image** and select an image from the drop-down list.

        **Note:** If you select an image other than a public image, see [EN-US\_TP\_9683.md\#](intl.en-US/User Guide/Cloud disks/Change the system disk (custom image).md#).

    2.  **System Disk**: You cannot change the cloud disk category. However, you can change the size of the disk to meet the requirements of your system disk. The maximum size is 500   GiB.  The size limit for changing is determined by the image and the current size of the system disk, as displayed in the following table.

        |Image|Capacity Limit for capacity expansion \(Gib\)|
        |:----|:--------------------------------------------|
        |Linux \(excluding CoreOS\) FreeBSD|\[Max\{20, current size of the system disk\}, 500\]|
        |CoreOS|\[Max\{30, current size of the system disk\}, 500\]|
        |Windows|\[Max\{40, current size of the system disk\}, 500\]|

        **Note:** If your instance was renewed for configuration downgrade, you cannot change the system disk size until the next billing cycle.

    3.  **Security**:
        -   If the new operating system is a Windows edition, a password is the only authentication method. 

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9682/5517_en-US.png)

        -   If you are changing the system disk of an I/O optimized instance, and the new operating system is a Linux edition, a password or an SSH key pair can be used as the authentication method. Set a password or bind an SSH key pair. 

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9682/5518_en-US.png)

    4.  Confirm **Instance Cost**: For more information on the price of system disk, see [Pricing of Elastic Compute Service](https://www.alibabacloud.com/product/ecs#pricing).
    5.  Click ECS Service Terms and Product Terms of Service and then click **Confirm to change**.

Log on to the ECS console to monitor the system status. It may take about 10 minutes to change the system disk. After the system disk is changed, the instance starts automatically.

## Follow-up operations {#section_bby_y3j_ydb .section}

After the system disk is changed, you may have to perform the following:

-   \(Optional\) [Set an automatic snapshot policy for the new system disk](intl.en-US/User Guide/Snapshots/Apply automatic snapshot policies to disks.md#). This operation  The automatic snapshot policy applied on the old disk automatically fails after a new system disk has been replaced. You need to set up an automatic snapshot policy for the new system disk.

-   If the original operating system is a Linux edition, data disks are attached to the instance, and the disks are set to be mounted automatically at startup of the instance, all mounting information is lost. Follow these steps to add new partition and mounting information to the /etc/fstab file. You do not have to partition or format the data disks again. For more information, see  Quick Start Linux \_ Format and mount a data disk.

    1.  Optional. Back up /etc/fstab.
    2.  Write new partition information to the /etc/fstab file.
    3.  Check new partition information in the /etc/fstab file.
    4.  Run `mount` to mount the partitions.
    5.  Run `df-h` command to check file system space and usage.

        After the data partitions are mounted, the data disks are ready for use. You do not have to restart the instance.


## Related APIs {#section_eby_y3j_ydb .section}

[../../../../dita-oss-bucket/SP\_2/DNA0011860945/EN-US\_TP\_9889.md\#](../../../../intl.en-US/API Reference/Disk/ReplaceSystemDisk.md#)

