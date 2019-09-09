# Resize partitions and file systems of Linux system disks {#concept_ocb_htw_dhb .concept}

This topic describes how to use the growpart and resize2fs tools to resize the partitions and extend the file systems of Linux system disks.

## Application scope {#section_u9c_3g5_ljs .section}

The procedures in this topic apply to system disks with the following partition formats and file system formats:

-   Partitions: MBR and GPT
-   File systems: ext\*, XFS, and Btrfs

## Preparations {#section_h25_n5w_dhb .section}

1.  [Create a snapshot](intl.en-US/Snapshots/Use snapshots/Create a snapshot.md#) for data backup, to prevent data loss caused by misoperations.
2.  Use the ECS console or API to [Resize cloud disks offline](intl.en-US/Block Storage/Block storage/Resize cloud disks/Resize cloud disks offline.md#).
3.  Connect to the ECS instance remotely. For more information about connection methods, see [Methods to connect to an ECS instance](../../../../intl.en-US/Instances/Connect to instances/Overview.md#).
4.  Install the growpart or xfsprogs tool based on your operating system.
    -   In CentOS 7 and Aliyun Linux, run the following commands:

        ``` {#codeblock_lnb_89n_iih}
        yum install cloud-utils-growpart
        yum install xfsprogs
        ```

    -   In Ubuntu 14, Ubuntu 16, Ubuntu 18 and Debian 9, run the following commands:

        ``` {#codeblock_x6x_nv9_rlb}
        apt install cloud-guest-utils
        apt install xfsprogs
        ```

    -   In Debian 8, openSUSE 42.3, openSUSE 13.1, and SUSE Linux Enterprise Server 12 SP2, use an upstream version of growpart or xfsprogs.
5.  Check the kernel version of your instance, for example, by running the `uname -a` command.
    -   For kernels 3.6.0 or later, see [Procedure for instances with kernels 3.6.0 or later](#section_gxq_3tw_dhb).
    -   For kernels earlier than 3.6.0, see [Procedure for instances with kernels earlier than 3.6.0](#section_vxq_3tw_dhb). If your instance runs a Linux distribution such as CentOS 6, Debian 7, or SUSE Linux Enterprise Server 11 SP4, the instance must be restarted by using the console or an API operation before resizing can be completed.

## Procedure for instances with kernels 3.6.0 or later {#section_gxq_3tw_dhb .section}

This procedure uses an instance running CentOS 7 to describe how to resize a system disk partition.

1.  Run the `fdisk -l` command to check the size of the disk.

    In this example, the /dev/vda disk size is 100 GiB.

    ``` {#codeblock_2wt_omi_qd8}
    [root@ecshost ~]# fdisk -l
    Disk /dev/vda: 107.4 GB, 107374182400 bytes, 209715200 sectors
    Units = sectors of 1 * 512 = 512 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk label type: dos
    Disk identifier: 0x0008d73a
    
       Device Boot      Start         End      Blocks   Id  System
    /dev/vda1   *        2048    41943039    20970496   83  Linux
    ```

2.  Run the `df -h` command to check the disk partition size.

    In this example, the /dev/vda1 partition size is 20 GiB.

    ``` {#codeblock_ui3_rtz_duk}
    [root@ecshost ~]# df -h
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/vda1        20G  1.5G   18G   8% /
    devtmpfs        7.8G     0  7.8G   0% /dev
    tmpfs           7.8G     0  7.8G   0% /dev/shm
    tmpfs           7.8G  344K  7.8G   1% /run
    tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
    tmpfs           1.6G     0  1.6G   0% /run/user/0
    ```

3.  Run the `growpart<DeviceName\><PartionNumber\>` command to use the growpart tool to resize the specified system disk and partition.

    In this example, the first partition of the system disk is resized.

    ``` {#codeblock_5j1_isw_vt9}
    [root@ecshost ~]# growpart /dev/vda 1
    CHANGED: partition=1 start=2048 old: size=41940992 end=41943040 new: size=209710462,end=209712510
    ```

4.  Run the `resize2fs <PartitionName\>` command to use the resize2fs tool to extend the file system.

    In this example, the file system of the /dev/vda1 partition is extended.

    ``` {#codeblock_ojc_rie_69u}
    [root@ecshost ~]# resize2fs /dev/vda1
    resize2fs 1.42.9 (28-Dec-2013)
    Filesystem at /dev/vda1 is mounted on /; on-line resizing required
    old_desc_blocks = 2, new_desc_blocks = 7
    The filesystem on /dev/vda1 is now 26213807 blocks long.
    ```

    **Note:** If an XFS file system is used, run the `xfs_growfs /dev/vda1` command.

5.  Run the `df -h` command to check the size of the disk partition.

    In this example, the /dev/vda1 partition size is 100 GiB, which means that the partition is resized.

    ``` {#codeblock_dxd_5wk_ijc}
    [root@ecshost ~]# df -h
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/vda1        99G  1.6G   93G   2% /
    devtmpfs        7.8G     0  7.8G   0% /dev
    tmpfs           7.8G     0  7.8G   0% /dev/shm
    tmpfs           7.8G  500K  7.8G   1% /run
    tmpfs           7.8G     0  7.8G   0% /sys/fs/cgroup
    tmpfs           1.6G     0  1.6G   0% /run/user/0
    ```


## Procedure for instances with kernels earlier than 3.6.0 {#section_vxq_3tw_dhb .section}

This procedure uses an instance running CentOS 6 to describe how to resize a system disk partition.

1.  Install the dracut-modules-growroot tool.

    ``` {#codeblock_spo_ed5_l62}
    [root@ecshost ~]# yum install -y dracut-modules-growroot
    ```

    If a package manager other than yum is used, change yum to the corresponding command.

2.  Run the following command to overwrite the existing initramfs file.

    ``` {#codeblock_fez_t5m_qh6}
    [root@ecshost ~]# dracut -f
    ```

3.  Run the `fdisk -l` command to check the current disk size.

    In this example, the /dev/vda disk size is 100 GiB.

    ``` {#codeblock_89d_7qe_lf3}
    [root@ecshost ~]# fdisk -l
    Disk /dev/vda: 107.4 GB, 107374182400 bytes
    255 heads, 63 sectors/track, 13054 cylinders
    Units = cylinders of 16065 * 512 = 8225280 bytes
    Sector size (logical/physical): 512 bytes / 512 bytes
    I/O size (minimum/optimal): 512 bytes / 512 bytes
    Disk identifier: 0x0003a7b4
    
       Device Boot      Start         End      Blocks   Id  System
    /dev/vda1   *           1        2611    20970496   83  Linux
    ```

4.  Run the `df -h` command to check the disk partition size.

    In this example, the /dev/vda1 partition size is 20 GiB.

    ``` {#codeblock_0fw_5w3_4d9}
    [root@ecshost ~]# df -h
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/vda1        20G  1.1G   18G   6% /
    tmpfs           7.8G     0  7.8G   0% /dev/shm
    ```

5.  Run the `growpart<DeviceName\><PartionNumber\>` command to use the growpart tool to resize the specified system disk and partition.

    In this example, the first partition of the system disk is resized.

    ``` {#codeblock_6lb_aln_3fy}
    [root@ecshost ~]# growpart /dev/vda 1
    CHANGED: partition=1 start=2048 old: size=41940992 end=41943040 new: size=209710462,end=209712510
    ```

6.  [Reboot the instance](../../../../intl.en-US/Instances/Manage instances/Restart an instance.md#) in the console or call the [RebootInstance](../../../../intl.en-US/API Reference/Instances/RebootInstance.md#) operation to restart the instance.
7.  Remotely connect to the instance.
8.  Run the `resize2fs <PartitionName\>` command to use the resize2fs tool to extend the file system.

    In this example, the file system of the /dev/vda1 partition is extended.

    ``` {#codeblock_9ma_xwj_r94}
    [root@ecshost ~]# resize2fs /dev/vda1
    resize2fs 1.41.12 (17-May-2010)
    Filesystem at /dev/vda1 is mounted on /; on-line resizing required
    old desc_blocks = 2, new_desc_blocks = 7
    Performing an on-line resize of /dev/vda1 to 26213807 (4k) blocks.
    The filesystem on /dev/vda1 is now 26213807 blocks long.
    ```

    **Note:** If an XFS file system is used, run the `xfs_growfs /dev/vda1` command.

9.  Run the `df -h` command to check the size of the disk partition.

    In this example, the /dev/vda1 partition size is 100 GiB, which means that the partition is resized.

    ``` {#codeblock_x71_1oh_4rb}
    [root@ecshost ~]# df -h
    Filesystem      Size  Used Avail Use% Mounted on
    /dev/vda1        99G  1.1G   93G   2% /
    tmpfs           7.8G     0  7.8G   0% /dev/shm
    ```


## Related operations {#section_gy7_ue1_3tg .section}

[Resize partitions and file systems of Linux data disks](intl.en-US/Block Storage/Block storage/Resize cloud disks/Resize partitions and file systems of Linux data disks.md#)

