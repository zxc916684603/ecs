# Partition and format data disks larger than 2 TiB {#concept_i15_qpc_ydb .concept}

This topic describes how to partition and format data disks larger than 2 TiB in different operating systems.

## Precautions {#section_xmm_psc_ydb .section}

-   The time required for creating a snapshot of a data disk is proportional to the volume of data on the data disk. The larger the volume of data, the longer time it takes to create a snapshot.
-   Alibaba Cloud Block Storage supports Master Boot Record \(MBR\) and GUID Partition Table \(GPT\) partition formats. MBR is applicable to data disks no larger than 2 TiB, and allows you to create up to four primary partitions. To partition a data disk larger than 2 TiB, use the GPT format.

    **Note:** Conversion between MBR and GPT may cause data loss. If the resulting disk size when you [create a disk by using a snapshot](reseller.en-US/Block Storage/Block storage/Create a cloud disk/Create a cloud disk by using a snapshot.md#) or [resize a disk](reseller.en-US/Block Storage/Block storage/Resize cloud disks/Resize cloud disks offline.md#) exceeds 2 TiB, we recommend that you first check whether the disk uses the MBR partition format. If the MBR partition format is used and you want to retain disk data on your instance, we recommend that you create another data disk and attach it to the instance. Then format a GPT partition and copy the data from the MBR partition to the GPT partition.

-   For data disks larger than 2 TiB, use the following partition tools, partition formats, and file systems.

    |Operating system|Partition tool|Partition format|File system|
    |:---------------|:-------------|----------------|:----------|
    |Windows|**Disk Management**|GPT|NTFS|
    |Linux|parted|GPT|Ext4 or XFS|


## Prerequisites {#section_9qr_8k6_joa .section}

1.  The data disk has been attached to your instance. For more information, see [Attach a cloud disk](reseller.en-US/Block Storage/Block storage/Attach a cloud disk.md#).
2.  You have established a remote connection to the ECS instance. For more information about how to remotely connect to an ECS instance, see [Overview](../../../../reseller.en-US/Instances/Connect to instances/Overview.md#).

## Partition and format a data disk on a Windows instance {#section_enm_psc_ydb .section}

The section describes how to partition and format a data disk larger than 2 TiB on a Windows instance running the Windows Server 2008 R2 64-bit operating system.

1.  On the taskbar, click **Server Manager**.
2.  In the left-side navigation pane of **Server Manager**, choose **Storage** \> **Disk Management**.
3.  Find the disk to be partitioned and formatted. This example uses **Disk 4**. The disk is in the **Offline** state.
4.  Right-click the space next to **Disk 4**, and click **Online**.

    After it comes online, **Disk 4** enters the **Not Initialized** state.

5.  Right-click the space next to **Disk 4**, and choose **Initialize Disk** from the shortcut menu.
6.  In the Initialize Disk dialog box, select **Disk 4** and select **GPT** as the disk partition method.
7.  In the Disk Management window, right-click the **Unallocated** section of **Disk 4**, and then choose **New Simple Volume** from the shortcut menu to create a 4 TiB volume in the NTFS format.
8.  In the New Simple Volume Wizard window, click **Next**, and follow these steps:
    1.  Specify Volume Size: Specify the size of the simple volume to create. If you want to create only one primary partition, use the default value. Click **Next**. You can also divide **Disk 4** into multiple partitions.

        **Note:** Theoretically, the maximum NTFS volume is the maximum volume of NTFS containing 2 64 -1 clusters. However, in Windows XP Pro, the maximum volume of NTFS is 2 32 -1 clusters. For example, NTFS can support a volume up to 256 TiB when the cluster size is 64 KiB. If the cluster size is 4 KiB, then the maximum volume is 16 TiB. NTFS selects the size of a cluster automatically based on the disk capacity.

    2.  Assign Drive Letter or Path: Select a drive letter. This example uses G. Click **Next**.
    3.  Format Partition: Select the formatting settings including file system, allocation unit size, and volume label, and then select **Perform a quick format** and **Enable file and folder compression** as needed. In this example, **Perform a quick format** is selected. Click **Next**.
    4.  After the new simple volume is created, click **Finish** to close the New Simple Volume Wizard window.

After the partition is formatted, the status of **Disk 4** in the **Disk Management** window is shown in the following figure.

## Convert the partition format of a data disk on a Windows instance {#Windows2012Snapshot .section}

**Note:** Converting between partition formats may cause data loss. Ensure that you have backed up the data on the disk before you convert to a different partition format.

This section describes how to convert the partition format on a 3 TiB data disk on a Window instance running the Windows Server 2012 R2 64-bit operating system.

1.  On the Windows Server desktop, right-click the **Start** icon, and select **Disk Management**.
2.  Find the disk to be partitioned and formatted. This example uses **Disk 2**.
3.  Right-click a simple volume, and then choose **Delete Volume** from the shortcut menu.
4.  Right-click the space next to Disk 2, and then choose **Convert to GPT Disk** from the shortcut menu.
5.  In the Disk Management window, right-click the **Unallocated** section of Disk 2, and then choose **New Simple Volume** from the shortcut menu to create a 3 TiB volume in the NTFS format.
6.  In the New Simple Volume Wizard window, click **Next** and follow these steps:
    1.  Specify Volume Size: Specify the size of the simple volume to create. If you want to create only one primary partition, use the default value. Click **Next**. You can also divide **Disk 2** into multiple partitions.

        **Note:** Theoretically, the maximum NTFS volume is the maximum volume of NTFS containing 2 64 -1 clusters. However, in Windows XP Pro, the maximum volume of NTFS is 2 32 -1 clusters. For example, NTFS can support a volume up to 256 TiB when the cluster size is 64 KiB. If the cluster size is 4 KiB, then the maximum volume is 16 TiB. NTFS selects the size of a cluster automatically based on the disk capacity.

    2.  Assign Drive Letter or Path: Select a drive letter. This example uses F. Click **Next**.
    3.  Format Partition: Select the formatting settings including file system, allocation unit size, and volume label, and then select **Perform a quick format** and **Enable file and folder compression** as needed. In this example, **Perform a quick format** is selected. Click **Next**.
    4.  After a new simple volume is created, click **Finish** to close the New Simple Volume Wizard window.

After the partition is formatted, the status of **Disk 2** in the **Disk Management** window is shown in the following figure.

## Partition and format a data disk on a Linux instance {#section_a4m_psc_ydb .section}

This section describes how to use the parted and e2fsprogs tools to partition and format a data disk larger than 2 TiB on a Linux instance running the CentOS 7.4 64-bit operating system. In the example, the data disk to be processed is a newly-created 3 TiB empty disk and its device name is /dev/vdd.

Prerequisites

The parted and e2fsprogs tools have been installed on your Linux instance.

``` {#codeblock_pf9_w04_1py}
[root@ecshost~ ]# yum install -y parted
[root@ecshost~ ]# yum install -y e2fsprogs
```

Procedure

To partition and format a data disk larger than 2 TiB and mount the file system, follow these steps:

1.  Run the `fdisk -l` command to check whether the data disk exists. The expected command output is as follows. If different information is returned, the data disk is not mounted to the instance.

    ``` {#codeblock_ixp_09f_9dk}
    [root@ecshost~ ]# fdisk -l
    Disk /dev/vdd: 3221.2 GB, 3221225472000 bytes, 6291456000 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    ```

2.  Run the `parted /dev/vdd` command to start partitioning.
    1.  Run the `mklabel gpt` command to convert the partition format from MBR to GPT.
    2.  Run the `mkpart primary 1 100%` command to create a primary partition, and specify the starting and ending sectors for the partition.
    3.  Run the `align-check optimal 1` command to check the partition alignment.

        **Note:** If `1 not aligned` is returned, the partition is not aligned. We recommend that you run the following commands and use the formula `(<optimal_io_size>+<alignment_offset>)/<physical_block_size>` to obtain the starting sector number to align partitions for optimal performance. For example, if the starting sector number is 1024, you can then run the `mkpart primary 1024s 100%` command to create a new primary partition.

        ``` {#codeblock_dlr_tyt_4no}
        [root@ecshost~ ]# cat /sys/block/vdd/queue/optimal_io_size
        [root@ecshost~ ]# cat /sys/block/vdd/queue/minimum_io_size
        [root@ecshost~ ]# cat /sys/block/vdd/alignment_offset
        [root@ecshost~ ]# cat /sys/block/vdd/queue/physical_block_size
        ```

    4.  Run the `print` command to view the partition table.

        ``` {#codeblock_0wj_f29_cgx}
        (parted) mklabel gpt
        (parted) mkpart primary 1 100%
        (parted) align-check optimal 1
        1 aligned
        (parted) print
        Model: Virtio Block Device (virtblk)
        Disk /dev/vdd: 3221GB
        Sector size (logical/physical): 512B/512B
        Partition Table: gpt
        Disk Flags:
        Number Start End Size File system Name Flags
        1 17.4kB 3221GB 3221GB primary
        ```

    5.  Run the `quit` command to exit the parted tool.
3.  Run the `partprobe` command to make the system re-read the partition table.
4.  Run one of the following commands to create a file system for the /dev/vdd1 partition.

    -   Create an Ext4 file system.

        ``` {#codeblock_363_794_ar1}
        [root@ecshost~ ]# mkfs -t ext4 /dev/vdd1
        ```

    -   Create an XFS file system.

        ``` {#codeblock_rlk_0l8_c3d}
        [root@ecshost~ ]# mkfs -t xfs /dev/vdd1
        ```

    **Note:** 

    -   If the capacity of the data disk is 16 TiB, you must format it by using the correct version of e2fsprogs. For more information, see [Appendix 1: Update e2fsprogs on a Linux instance](#).
    -   If you want to disable the lazy init function of an Ext4 file system to avoid its impact on data disk I/O performance, see [Appendix 2: Disable the lazy init function on a Linux instance](#).
5.  Run the `mkdir /test` command to create a mount point named /test.
6.  Run the `mount /dev/vdd1 /test` command to mount partition /dev/vdd1 to mount point /test.
7.  Run the `df -h` command to view the current disk space and usage.

    If the command output shows information about the newly created file system, the mount operation was successful, and the new file system can be used.

    ``` {#codeblock_7rw_7dq_6ww}
    [root@ecshost~ ]# df -h
    Filesystem Size Used Avail Use% Mounted on
    /dev/vda1 40G 6.4G 31G 18% /
    devtmpfs 487M 0 487M 0% /dev
    tmpfs 497M 0 497M 0% /dev/shm
    tmpfs 497M 364K 496M 1% /run
    tmpfs 497M 0 497M 0% /sys/fs/cgroup
    tmpfs 100M 0 100M 0% /run/user/0
    /dev/vdd1 2.9T 89M 2.8T 1% /test
    ```

8.  \(Optional\) Write new partition information to /etc/fstab to enable automatic partition mounting when the instance is started.
    1.  \(Optional\) Run the `cp /etc/fstab /etc/fstab.bak` command to back up etc/fstab.
    2.  Run the `echo /dev/vdd1 /test ext4 defaults 0 0 >> /etc/fstab` command to write new partition information to /etc/fstab.
    3.  Run the `cat /etc/fstab` command to check /etc/fstab information.

        If the new partition information appears in the command output, the write operation was successful.


You have now partitioned and formatted a 3 TiB data disk.

## Appendix 1: Update e2fsprogs on a Linux instance {#e2fsprogs .section}

If the disk capacity is 16 TiB, you must use e2fsprogs 1.42 or later to format its partitions to an Ext4 file system. If e2fsprogs of a version earlier than 1.42 is used, the following error occurs:

``` {#codeblock_igb_omy_lmt}
mkfs.ext4: Size of device /dev/vdd too big to be expressed in 32 bits using a blocksize of 4096.            
```

To install a later version of e2fsprogs, such as 1.42.8, follow these steps:

1.  Run the `rpm -qa | grep e2fsprogs` command to check the current e2fsprogs version.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9672/15674013864439_en-US.png)

    If the version is earlier than 1.42, perform the following steps to update the software.

2.  Run the following command to download e2fsprogs 1.42.8. You can go to [e2fsprogs](https://www.kernel.org/pub/linux/kernel/people/tytso/e2fsprogs/v1.42.8/?spm=a2c4g.11186623.2.14.Pb5baW) to obtain the latest software package.

    ``` {#codeblock_d0d_ybl_03d}
    wget https://www.kernel.org/pub/linux/kernel/people/tytso/e2fsprogs/v1.42.8/e2fsprogs-1.42.8.tar.gz
    ```

3.  Run the following commands to compile the tool of a later version.

    ``` {#codeblock_qlx_myn_6xc}
    tar xvzf e2fsprogs-1.42.8.tar.gz
    cd e2fsprogs-1.42.8
    ./configure
    make
    make install
    ```

4.  Run the following command to check whether e2fsprogs is updated.

    ``` {#codeblock_8nw_en4_ptq}
    rpm -qa | grep e2fsprogs
    ```


## Appendix 2: Disable the lazy init function on a Linux instance {#LazyInit .section}

The lazy init function of an Ext4 file system is enabled by default. While this function is enabled, the instance will initiate a thread to continuously initialize the metadata of the Ext4 file system. Therefore, right after you partition and format a data disk, the test of disk IOPS performance will be affected, resulting in a lower IOPS.

If you need to test the data disk performance immediately after partitioning and formatting the disk, run the following command to disable the lazy init function when you initialize the file system.

``` {#codeblock_hhi_98n_m3m}
mke2fs -O 64bit,has_journal,extents,huge_file,flex_bg,uninit_bg,dir_nlink,extra_isize -E lazy_itable_init=0,lazy_journal_init=0   /dev/vdd1
```

**Note:** If the lazy init function is disabled, it may take a longer time to initialize the file system. For example, it may take 10 to 30 minutes to initialize the file system of a 32 TiB data disk. Enable or disable the lazy init function based on your needs.

