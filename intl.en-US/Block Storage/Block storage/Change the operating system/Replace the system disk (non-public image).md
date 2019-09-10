# Replace the system disk \(non-public image\) {#concept_vbb_ckj_ydb .task}

Replacing the system disk refers to the allocation of a new system disk for the instance. The original system disk is released and the system disk ID is updated. You can replace the system disk in the following scenarios: 1. You selected an incorrect operating system when you created an ECS instance and need to change the operating system. 2. When your business expands, you want to upgrade the system disk capacity or use another operating system.

Before you change the image of a system disk to a non-public image, follow these steps:

-   For custom images:
    -   To use an image captured from an existing ECS instance, you must create a system disk snapshot of this instance and use the snapshot to create a custom image. For more information, see [Create a snapshot](../reseller.en-US/Snapshots/Use snapshots/Create a snapshot.md#) and [Create a custom image by using a snapshot](reseller.en-US/Images/Custom image/Create custom image/Create a custom image by using a snapshot.md#). You must make a copy of the image if the captured image and the instance with the system disk that you want to replace are in different regions. For more information, see [Copy custom images](../reseller.en-US/Images/Custom image/Copy custom images.md#).
    -   To use a local image file, you must import the image in the console or use Packer to create and import the image. The image must be in the same region as your instance. For more information, see [Import custom images](../reseller.en-US/Images/Custom image/Import images/Import custom images.md#) and [../DNECS19100339/EN-US\_TP\_9698.md\#](../reseller.en-US/Images/Custom image/Create custom image/Use Packer to create a custom image.md#).
    -   If you want to use an image from another region, you must first make a copy of the image. For more information, see [Copy custom images](../reseller.en-US/Images/Custom image/Copy custom images.md#).

        **Note:** Images created by using this method appear in the **Custom Image** list when you change the system disk.

-   To use images owned by another Alibaba Cloud account, you must first let the other account share the images. Then, you can obtain the shared images. For more information, see [EN-US\_TP\_9700.md\#](reseller.en-US/Images/Custom image/Share custom images.md#).
-   If you want to change to a Linux operating system and use an SSH key pair for authentication, you must first create an SSH key pair. For more information, see [Create an SSH key pair](reseller.en-US/Security/Key pairs/Use an SSH key pair.md#).
-   Replacing a system disk is a high-risk operation that may cause data loss or service interruptions. To minimize the impact of replacing the system disk on your business, we recommend that you create a snapshot of the current system disk before replacing the system disk. For more information, see [Create a snapshot](../reseller.en-US/Snapshots/Use snapshots/Create a snapshot.md#).
-   If you want to replace the system disk of a Windows Server instance, make sure that the system disk has sufficient available space. We recommend that you reserve 1 GiB of available space. Otherwise, the system may fail to restart after the system disk is changed.

**Note:** Create snapshots during off-peak hours to minimize the impact on your business. The first time you create a 40 GiB snapshot requires about 40 minutes. Therefore, you must allocate sufficient time to create the snapshot. Creating a snapshot may temporarily reduce the I/O performance of a block storage device by about 10% and cause a temporary slowdown.

You can select a public image, shared image, custom image, or an image from the marketplace for the ECS instance when you change the system disk. This topic describes how to replace an image of a system disk with a non-public image. For more information about how to replace an image of a system disk with a public image, see [Replace the system disk by using a public image](reseller.en-US/Block Storage/Block storage/Change the operating system/Replace the system disk by using a public image.md#).

**Note:** Microsoft no longer offers support for Windows Server 2003. To make sure the safety of your data, we recommend that you stop using Windows Server 2003 for your ECS instances. Alibaba Cloud no longer provides images based on Windows Server 2003. For more information, see [Discontinuation of Windows Server 2003 system image](https://partners-intl.aliyun.com/help/faq-detail/59513.htm).

Replacing a system disk is a high-risk operation that may cause data loss or service interruptions. When you replace a system disk, you must carefully read the following:

-   Before you replace the system disk
    -   The original system disk is released after you replace the system disk. We recommend that you create a snapshot to back up the data before the replacement. For more information, see [Create a snapshot](../reseller.en-US/Snapshots/Use snapshots/Create a snapshot.md#).
    -   Your workloads are interrupted because you must stop the instance to replace the system disk. For more information, see [Start or stop an instance](../reseller.en-US/Instances/Manage instances/Start or stop an instance.md#).
    -   Make sure that you have enough snapshot quota to use the automatic snapshot policy for the new system disk. You can delete outdated system disk snapshots that you no longer require. For more information, see [Delete a snapshot](../reseller.en-US/Snapshots/Use snapshots/Delete a snapshot.md#).
    -   You cannot change the category of the system disk for your ECS instance.
-   After you replace the system disk
    -   The IP address and the MAC address of the ECS instance remain unchanged.
    -   A new system disk with a new disk ID is allocated to your instance, and the original system disk is released.
    -   Snapshots of the outdated system disk cannot be used to restore the new system disk.
    -   Manually created snapshots are not released. You can still use the outdated system disk snapshots to create custom images.
    -   If the outdated system disk has automatic snapshot policies with Delete Automatic Snapshots While Releasing Disk enabled, the automatic snapshots of the outdated system disk are automatically deleted. The outdated automatic snapshot policies are no longer applicable to new system disks. You must reset the policies.
    -   You must redeploy the service environment on the new system disk, which may cause a long interruption to your business.
-   Cross-OS system disk replacement

    **Note:** Cross-OS disk replacement refers to switching between Linux and Windows Server systems. After a system disk switches to a different operating system, the ECS instance cannot identify the file system format of the data disk. For regions outside mainland China, system disk replacement across operating systems is not supported. The system only supports replacement across different Linux distributions or different Windows Server versions.

    -   If the data disk does not contain important data, you can reinitialize the data disk and create a file system supported by the corresponding system for the data disk. For more information, see [Reinitialize a data disk](reseller.en-US/Block Storage/Block storage/Reinitialize a cloud disk/Reinitialize a cloud disk.md#).
    -   If important data exists on the data disk, follow these steps:
        -   For replacing Windows Server with Linux: Manually install the required file system driver, such as NTFS-3G. Linux is unable to recognize the NTFS file system.
        -   For replacing Linux with Windows Server: Manually install the required file system diver, such as Ext2Read and Ext2Fsd. Windows Server is unable to recognize some file systems, such as ext3, ext4, XFS.
        -   For replacing Windows Server with Linux: You can use either password authentication or SSH key pair authentication.

1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).
2.  In the left-side navigation pane, choose **Instances & Images** \> **Instances**.
3.  In the top navigation bar, select a region.
4.  Find the instance with the system disk that you want to replace. In the **Actions** column, choose **More** \> **Instance Status** \> **Stop**. When the instance status changes to **Stopped**, the instance is successfully stopped.
5.  In the **Actions** column, choose **More** \> **Disk and Image** \> **Replace System Disk**.
6.  In the dialog box that appears, read the precautions for replacing the system disk, and click **OK**.
7.  On the Change System Disk page, configure the following parameters. 
    1.  **Image Type**: Select **Custom Image**, **Shared Image**, or **Marketplace Image**, and select the image that you want.
    2.  **System Disk**: You cannot change the type of the system disk. However, you can resize the system disk based on your business needs and the new image. The maximum capacity of the new system disk is 500 GiB. The minimum capacity depends on the current capacity of the system disk and the size of the image. The following table lists the rules. 

        |Image|Resized capacity \(GiB\)|
        |:----|:-----------------------|
        |Linux \(excluding CoreOS\) + FreeBSD|From Max\{20 or current system disk capacity\} \(the greater of the two\) to 500|
        |CoreOS|From Max\{30 or current system disk capacity\} \(the greater of the two\) to 500|
        |Windows Server|From Max\{40 or current system disk capacity\} \(the greater of the two\) to 500|

        **Note:** If you have renewed your instance and downgraded the configurations, the system disk capacity cannot be changed until the next billing cycle starts.

    3.  **Security**: 
        -   If the new operating system is Windows Server, you can only use password authentication.
        -   If your instance is an I/O optimized instance and the new operating system is Linux, you can use either password authentication or SSH key pair authentication. You must set a logon password or bind an SSH key pair.
    4.  Confirm the **Instance Cost**. The cost includes both the image fee and the system disk fee.
    5.  Click **Confirm to Change**.

Log on to the ECS console to monitor the instance status. The replacement of the system disk requires about 10 minutes. After the system disk is replaced, the instance automatically restarts.

After changing the system disk, follow these steps:

-   Optional. The automatic snapshot policies of the outdated system disk are now invalid. You can set new automatic snapshot policies for the new system disk. For more information, see [Apply or disable an automatic snapshot policy](../reseller.en-US/Snapshots/Automatic snapshot policies/Apply or disable an automatic snapshot policy.md#).
-   If both the new and the outdated operating systems are Linux, the outdated instance has data disks mounted and automatic mounting of the partition at startup enabled: After the system disk is changed, the configuration for the mounting of the data disk partitions from the outdated system disk will be lost. You must configure the new partition in the /etc/fstab file and mount the partition. You do not need to format and partition the data disk. You can perform the following steps. For more information, see [Format a data disk of a Linux instance](../reseller.en-US/Quick Start for Entry-Level Users/Step 4. Format a data disk/Format a data disk of a Linux instance.md#).

    1.  We recommend that you back up the /etc/fstab file.
    2.  Write the new partition information to the /etc/fstab file.
    3.  View the new partition information in the /etc/fstab file.
    4.  Run the mount command to mount the partition.
    5.  Run the `df -h` command to check the current disk capacity and utilization.
    After the partition is mounted, you can use the new data disk without restarting the ECS instance.


**More information**  


[../DNA0011860945/EN-US\_TP\_9889.md\#](../reseller.en-US/API Reference/Disk/ReplaceSystemDisk.md#)

