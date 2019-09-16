# Create a file system on a raw data disk {#task_1797291 .task}

This topic uses an ECS instance running the Ubuntu operating system to show how to create a file system on a raw data disk. You can skip the steps to create a new partition, such as /dev/vdb1 or /dev/vdb2, and directly create a file system if no partition is required. This method is only applicable to ECS instances running a Linux operating system.

A cloud disk has been created and attached to an ECS instance. For more information, see [Create a Pay-As-You-Go cloud disk](reseller.en-US/Block Storage/Block storage/Create a cloud disk/Create a Pay-As-You-Go cloud disk.md#) and [Attach a cloud disk](reseller.en-US/Block Storage/Block storage/Attach a cloud disk.md#).

1.  Remotely connect to an ECS instance as a root user. For more information, see [Overview](../reseller.en-US/Instances/Connect to instances/Overview.md#).
2.  Run the following command to view the name of the attached cloud disk. 

    ``` {#codeblock_qds_oex_0m3}
    fdisk -l 
    ```

    If the following output is displayed, it indicates that the ECS instance has two cloud disks: /dev/vda as the system disk and /dev/vdb as a data disk.

    ![fdisk](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/1423208/156861803256567_en-US.png)

3.  Create a file system for the /dev/vdb data disk. Example: 
    -   Create an ext4 file system

        ``` {#codeblock_vhu_336_589}
        mkfs.ext4 /dev/vdb
        ```

    -   Create an ext3 file system

        ``` {#codeblock_5e0_mhr_j52}
        mkfs.ext3 /dev/vdb
        ```

    -   Create an xfs file system

        ``` {#codeblock_hpv_m7l_ezh}
        mkfs.xfs /dev/vdb
        ```

    -   Create a btrfs file system

        ``` {#codeblock_zqb_qbm_fbe}
        mkfs.btrfs /dev/vdb
        ```

4.  Create a mount directory, such as /media/vdb. If this step is omitted, you can also attach the disk to an existing directory.

    ``` {#codeblock_g3q_sw2_6rh}
    mkdir /media/vdb
    ```

5.  Attach the disk to the mount directory. 

    ``` {#codeblock_c9k_s28_j0g}
    mount /dev/vdb /media/vdb
    ```

6.  Run the df command to view the data disk information. 

    The mount directory information of the disk is displayed, indicating that the operation was successful.

    ``` {#codeblock_h2v_feq_0xt .lanuage-shell}
    [root@ecshost ~]# df -h
    Filesystem Size Used Avail Use% Mounted on
    udev 3.9G 0 3.9G 0% /dev
    tmpfs 798M 2.9M 795M 1% /run
    /dev/vda1 40G 3.2G 35G 9% /
    tmpfs 3.9G 0 3.9G 0% /dev/shm
    tmpfs 5.0M 0 5.0G 0% /run/lock
    tmpfs 3.9G 0 3.9G 0% /sys/fs/cgroup
    tmpfs 798M 0 798M 0% /run/user/0
    /dev/vdb 98G 61M 93G 1% /media/vdb
    ```


**More information**  


[Format a data disk for a Windows instance](../reseller.en-US/Quick Start for Entry-Level Users/Step 4. Format a data disk/Format a data disk for a Windows instance.md#)

[Format a data disk of a Linux instance](../reseller.en-US/Quick Start for Entry-Level Users/Step 4. Format a data disk/Format a data disk of a Linux instance.md#)

