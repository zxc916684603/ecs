# Create a custom image by using a snapshot {#concept_gpg_t5l_xdb .concept}

Custom images help you run ECS instances effectively by allowing you to create multiple ECS instances with identical OS and environment data to meet scaling requirements.

Custom images are based on ECS disk snapshots. You can set up identical or different configurations for ECS instances that are created from images.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9696/15331921384584_en-US.png)

You can use a snapshot to create a custom image, including the operating system and data environment of the snapshot in the image. You can then use the custom mirror to create multiple instances with the same operating system and data environment, replicating instances easily.

You can also use an instance to create a image. See [Create a custom image by using an instance](intl.en-US/User Guide/Images/Create custom image/Create a custom image by using an instance.md#).

To enhance the security of creating custom imags from snapshots, operation, [Security suggestions for Alibaba Cloud custom images](https://www.alibabacloud.com/help/zh/faq-detail/54903.htm?spm=a2c63.q38357.a3.3.3a4b61feRLos9d).

**Note:** 

-   Custom images cannot be used across regions.
-   You can change the operating system of an instance created from a custom image. The custom image can still to be used after the operating system is changed. See [Change the system disk \(custom image\)](intl.en-US/User Guide/Cloud disks/Change the system disk (custom image).md#).
-   You can upgrade the instance created from a custom image, including upgrading the CPU, memory, bandwidth, and disks.
-   Custom images are independent from billing methods. Both Subscription and Pay-As-You-Go billing methods work. Custom images created from Subscription instances can used for creating Pay-As-You-Go instances. The opposite is also true.
-   If the ECS used for creating a custom image expires, or the data is erased \(that is, the system disk used for the snapshot expires or is released\), the custom image and the ECS instances created from the custom image are not affected. However, auto snapshots are cleared when an ECS instance is released.

## Considerations for Linux instances {#section_tx3_vvl_xdb .section}

-   Do not load data disk information in the /etc/fstab file. Otherwise, instances created using this image cannot start.
-   We recommend that before taking a snapshot and creating an image, umount all data disks, and then create a snapshot to create a custom image. Otherwise, ECS instances that are created based on this custom image may not start.
-   Do not upgrade the kernel or operating system version.
-   Do not change the system disk partition. The system disk only support a single root partition.
-   Check the availabe space of the the system disk to make sure that the system disk is not full.
-   Do not modify critical system files such as /sbin, /bin and /lib etc.
-   Do not modify the default logon user name root.

## Procedure {#section_p1r_rwl_xdb .section}

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  Select a region.
3.  In the left-hand navigation pane, click  **Instances**.
4.  Find the target instance, click the instance ID, or in the **Actions** column, click **Manage**.

    ![](images/4587_en-US.png)

5.  In the left-hand navigation pane, click **Snapshots**. Find the target system disk, in the **Actions** column, click **Create Custom Image**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9696/15331921384589_en-US.png)

    The snapshot must be created from Data disks cannot be used to create custom images. 

    You can also use **Snapshots** \> **Snapshot list**and select a snapshot created from a system disk to **create a custom image**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9696/15331921384593_en-US.png)

6.  In the pop-up Create a custom image dialog box, do the following:
    -   Confirm the snapshot ID.
    -   Specify the name and description of the custom image.
    -   Optional. Click **Add Data Disk Snapshot** to select multiple snapshots of data disks for the image. Click **Add** to add a data disk.

        **Note:** 

        Remove sensitive data from the data disk before creating a custom image to avoid the risk of data security.

        If the snapshot disk capacity is left blank, an empty disk is created with the default capacity of 5 GiB.

        If you select available snapshots, the disk size is the same as the size of these snapshots. 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9696/15331921384594_en-US.png)

7.  Click **Create**. The custom image is successfully created. In the left-side navigation pane, select  **Snapshots & Images \> Images** to view images you have created.

## FAQ for images of Linux instances {#section_jwm_ryl_xdb .section}

**How to `umount` a disk and delete disk table data?**

If /dev/hda5 is attached to /mnt/hda5, run any of the following three commands to detach the file system:

```
umount/dev/hda5
umount/mnt/hda5
umount/dev/hda5/mnt/hda5
```

`/Etc/fstab` is an important configuration file in Linux. It contains file system details and storage devices attached at startup. If you do not want to mount a specified partition when starting the VM, delete the corresponding lines from /etc/fstab. For example, you can delete the following statement to disconnect xvdb1 upon startup: `/dev/xvdb1 /leejd ext4 defaults 0 0`

**How to determine whether a data disk is detached and a custom image can be created?**

You must make sure that the auto attach data disk statement line has been deleted from the fstab file.

Use the mount command to view information on all mounted devices. Make sure that the execution results do not contain the information of the data disk partition.

**Relevant configuration files**

Before creating an image, make sure that the key configuration files from the following table have not been modified. Otherwise, the new instance is unable to start.

|Configuration File|Purpose|Risks if changed|
|:-----------------|:------|:---------------|
|/etc/issue\*, /etc/\*-release, /etc/\*\_version|For system release and version|Modifying /etc/issue\* makes the system release version unidentifiable, and cause instance creation failure.|
|/boot/grub/menu.lst, /boot/grub/grub.conf|For system startup|Modifying /boot/grub/menu.lst results in kernel loading failure, and the system is unable to start.|
|/etc/fstab|For mounting partitions during startup.|Modifying it causes partition mounting failure, and the system is unable to start.|
|/etc/shadow|For storing system passwords.|If this file is set to read-only, the password file cannot be edited, and instance creation fails.|
|/etc/selinux/config|For system security policies|Modifying /etc/selinux/config and enabling SELinux results in start failure.|

