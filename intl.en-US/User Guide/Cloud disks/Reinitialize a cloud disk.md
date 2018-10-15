# Reinitialize a cloud disk {#concept_stg_xd3_ydb .concept}

When a cloud disk is attached to an ECS instance, you can **reinitialize the disk** to restore the system disk or the data disks to the status when they were created. After a cloud disk is reinitialized:

-   The system disk is restored to the initial status when it was created. For example, if you select a public image to create an ECS instance, after the system disk is reinitialized, the operating system is retained, but all other applications that were installed after the instance creation are deleted.

    **Note:** After you changed the operating system or resized the system disk, it cannot be restored to the status when you created the ECS instance, but only to the status of the new system disk when it was created.

-   The data disk is restored to the initial status when it was created:
    -   An empty disk if it was an empty disk
    -   A disk with only the data of the source snapshot if it was [created from a snapshot](reseller.en-US/User Guide/Cloud disks/Create a cloud disk from a snapshot.md#)
-   If an automatic snapshot policy is applied to a cloud disk, the policy is retained. You do not have to apply the policy to the disk again after reinitialization.
-   If an automatic snapshot policy is applied to a cloud disk, the policy is retained. You do not have to apply the policy to the disk again after reinitialization.
-   After a cloud disk is reinitialized, all the snapshots, both automatically and manually created, are retained. You can use them to [roll back a cloud disk](reseller.en-US/User Guide/Cloud disks/Roll back a cloud disk.md#).

**Warning:** 

-   Your business operations may be interrupted because you have to stop your ECS instance to reinitialize a cloud disk. Therefore, proceed with caution.
-   After a cloud disk is reinitialized, its data is lost. Therefore, back up the data. For example, [create snapshots](reseller.en-US/User Guide/Snapshots/Create snapshots.md#).

## Reinitialize a system disk {#InitSys .section}

**Prerequisites**

If an SSH key pair is used as the authentication method, [create an SSH key pair](reseller.en-US/User Guide/Key pairs/Create an SSH key pair.md#) or [import an SSH key pair](reseller.en-US/User Guide/Key pairs/Import an SSH key pair.md#).

**Procedure**

To reinitialize a system disk, follow these steps:

1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).
2.  Select a region.
3.  In the left-side navigation pane, click **Instances**.
4.  Find an ECS instance, and click the instance ID to go to the Instance Details page.
5.  Click **Stop** to stop the instance.

    **Note:** For a Pay-As-You-Go VPC-Connected ECS instance, if the [No fees for stopped instances \(VPC-Connected\)](../../../../reseller.en-US/Pricing/No fees for stopped instances (VPC-Connected).md#) feature is enabled, in the Notice dialog box, click  **OK**, and then in the Stop dialog box, select **Keep Instance with Fees**。Keep Instance with Fees to stop the instance in the Keep Instance, Fees Apply mode. If you select the  **No Fees for Stopped Instances \(VPC-Connected\)** mode, you may not start the instance successfully after you reinitialize the system disk.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9676/15395951045328_en-US.png)

6.  After the instance is **stopped**, in the left-side navigation pane, click **Instance Disks**.
7.  Find the system disk, and in the **Actions** column, click **Re-initialize Disk**.
8.  In the Reinitialize Disk dialog box, finish the following configuration:
    1.  Authentication method:
        -   For a Windows instance: Specify a logon password. You can either use the old password or specify a new one.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9679/15395951045382_en-US.png)

        -   For a Linux instance: Select **Key Pair** or **Password**as the security setting. If Key Pair is selected, bind a key pair. If Password is selected, specify a logon password.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9679/15395951045383_en-US.png)

    2.  \(Optional\) **Security Enhancement**: Select **Free open**. After the security enhancement feature is enabled, ECS security components are loaded, which provide site backdoor detection, remote logon reminders, violent crack blocking, and other security features.
    3.  \(Optional\) **Instance Startup**: Select **Start instance after successfully resetting the disk**. .
    4.  Click **Confirm Disk Reinitialization**.
9.  For a Linux instance only: If you have attached a data disk to the instance, connect to the instance and [create a mounting point for the partitions of data disks](https://partners-intl.aliyun.com/help/faq-detail/40580.htm), because the mounting points are lost after the system disk is reinitialized.

    **Note:** For a Windows instance, both the system disk and the data disks are ready for use. No additional operations are needed.


After the system disk is reinitialized, you must deploy all applications to restore your business operations.

## Reinitialize a data disk {#InitData .section}

Once reinitialized, a data disk is in different status according to its original status and the operating system of the instance:

-   For a Windows instance: The data disk is ready for use without any additional operations regardless of its original status.
-   For a Linux instance:
    -   If the data disk was an empty disk after it was created: All the data and partitions on the disk are lost. You must partition and format the disk, and mount the partitions again.

        **Note:** If you configured the /etc/fstab file to automatically mount the disk partitions at startup of the instance, you must comment out the lines from the /etc/fstab file before reinitializing a data disk. Otherwise, your instance fails to start up.

    -   If the data disk was created from a snapshot: The data disk is recovered to the status of the source snapshot. You do not have to mount the partitions again, but all the data generated after the disk creation is lost.

In this section, /dev/vdb1 is the example partition and /InitTest is the example mounting point. You can replace them with the actual information.

**Prerequisites**

The data disk to be reinitialized must be attached to an ECS instance. For more information, see [attach a cloud disk](reseller.en-US/User Guide/Cloud disks/Attach a cloud disk.md#).

**Procedure**

To reinitialize a data disk, follow these steps:

1.  For a Linux instance only: If the data disk was an empty disk after it was created, and the mounting configuration was added to the /etc/fstab file, you must comment out the mounting configuration from the /etc/fstab file. Follow these steps:
    1.  [Connect to the Linux instance](reseller.en-US/User Guide/Connect to instances/Overview.md#).
    2.  Run `vim /etc/fstab`.
    3.  Press the `i` key to enter the Insert mode.
    4.  Locate the mounting configuration lines and type \# before the lines. For example:

        ```
        # /dev/vdb1 /InitTest ext3 defaults 0 0
        ```

    5.  Press the `Esc` key to exit the Insert mode, and then run :wq to save and exit.
2.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).
3.  In the left-side navigation pane, click **Instances**.
4.  Select a region.
5.  Find an ECS instance, and click the instance ID to go to the Instance Details page.
6.  Click **Stop** to stop the instance.

    **Note:** For a Pay-As-You-Go VPC-Connected ECS instance, if the [No fees for stopped instances \(VPC-Connected\)](../../../../reseller.en-US/Pricing/No fees for stopped instances (VPC-Connected).md#) feature is enabled, in the  Notice dialog box, click  **OK**, and then in the Stop dialog box, select **Keep Instance with Fees** to stop the instance in the Keep Instance, Fees Apply mode. Otherwise, you may not start the instance successfully after you reinitialize the data disk. If you select the **No Fees for Stopped Instances \(VPC-Connected\)** mode, you may not start the instance successfully after you reinitialize the system disk.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9676/15395951045328_en-US.png)

7.  After the instance is **stopped**, in the left-side navigation pane, click **Instance Disks**.
8.  Find a data disk, and in the **Actions/g\> column, click**Re-initialize Disk/g\>.
9.  In the Reinitialize Disk dialog box, read the notes and click **Confirm Disk Reinitialization**.
10. In the left-side navigation pane, click **Instance Details**.
11. Click **Start** to start the instance to complete the initialization of the data disk.
12. For a Linux instance only: If the data disk was an empty disk after it was created, [format and mount data disks for Linux instances](../../../../reseller.en-US/Quick Start for Entry-Level Users/Step 4. Format a data disk/Format and mount data disks for Linux instances.md#).

After the data disk is reinitialized, you may need to deploy applications to restore your business operations.

## API {#section_yxg_323_ydb .section}

[ReInitDisk](../../../../reseller.en-US/API Reference/Disk/ReInitDisk.md#)

