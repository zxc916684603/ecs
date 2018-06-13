# Detach a cloud disk {#concept_i1f_kgg_ydb .concept}

When a Pay-As-You-Go cloud disk is attached to an ECS instance as a data disk, you can detach it from the instance and release it.  However, if the disk is used as a system disk, you cannot detach it.

When detaching a cloud disk, consider the following:

-   Only the Pay-As-You-Go cloud disks in the **In Use** status and used as a  **Data Disk** can be detached.
-   You cannot detach a local disk.
-   On a Windows instance, consider the following:
    -   To guarantee the data integrity, we recommend that you stop writing or reading the files on the cloud disk. Otherwise, data may be lost.
    -   Before detaching a cloud disk in the ECS console, you must [connect to the instance](intl.en-US/User Guide/Connect/Connect to a Windows instance.md#) and set it offline in  **Disk Management** .
-   On a Linux instance, consider the following:

    -   Before detaching a cloud disk in the ECS console, you must  [connect to the instance](intl.en-US/User Guide/Connect/Overview.md#) and run `umount` to unmount the partitions.
    -   If you have configured the /etc/fstab file to automatically mount the partitions at the startup of the instance, before detaching it, you must delete the configurations from the /etc/fstab file.  Otherwise, you cannot connect to the instance after the instance is restarted.

The following table shows the options available for you to detach a cloud disk in the ECS console.

|Scenario|Applicable action|
|:-------|:----------------|
|You want to detach one or more cloud disks from one instance.|[\#InstanceCloud](#InstanceCloud)|
|You want to detach one specified cloud disk.|[\#CloudCloud](#CloudCloud)|

## Detach cloud disks on the Instance Disk page. {#InstanceCloud .section}

On the Instance Disk page, you can delete one or more cloud disks that are attached to the instance.

**Prerequisites**

The cloud disks have been [attached to the instance](intl.en-US/User Guide/Cloud disks/Attach a cloud disk.md#) and are in  the **In Use** status

If you are detaching a cloud disk from a Linux instance, and you have configured the /etc/fstab  file to mount the partitions at the startup of the instance, delete the configurations.

**Procedure**

To detach a cloud disk from the Instance Disks page, follow these steps:

1.  Connect to the instance and unmount the partitions. Follow different steps according to the operating system, as shown in the following table.

    |Operating system|Steps|
    |:---------------|:----|
    |Linux|Run `umount [partition]`. For example, `umount /dev/vdb1`.|
    |Windows|Start Disk Management, right-click the disk name \(For example, **Disk 2**\) and then click  **Offline**.![](images/5129_en-US.png)

|

2.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
3.  In the left-side navigation pane, click **Instances**.
4.  Select a region.
5.  Find an instance and click its ID to go to the Instance Details page.
6.  In the left-side navigation pane, click**Instance Disks**.
7.  Find a cloud disk, in the **Actions** column, select  **More** \> **Detach**.

    Only the cloud disks that have the following attributes can be detached:

    -   **Disk Status** must be **In Use**.
    -   **Detachable** must be **Yes**.
    -   **Used As** must be **Data Disk**.
8.  In the dialog box, click **Confirm Detaching**.
9.  Optional. If you want to detach more cloud disks, repeat step 7 and step 8.

When the status of the cloud disk becomes **Available** , the disk is detached.

## Detach a cloud disks on the Disk List page {#CloudCloud .section}

You can detach one specified cloud disk from an ECS instance.

**Prerequisites**

The cloud disk has been  [attached to the instance](intl.en-US/User Guide/Cloud disks/Attach a cloud disk.md#) and are in the  **In Use**status.

If you are detaching a cloud disk from a Linux instance, and you have configured the /etc/fstab file to mount the partitions at the startup of the instance, delete the configurations.

**Procedure**

To detach a cloud disk on the Disk List page, follow these steps:

1.  Connect to the instance and unmount the partitions.  Follow different steps according to the operating system, as shown in the following table.

    |Operating system|Steps|
    |:---------------|:----|
    |Linux|Run `umount [partition]`. For example, `umount /dev/vdb1`.|
    |Windows|Start Disk Management, right-click the disk name \(For example, **Disk 2**\) and then click  **Offline**.![](images/5129_en-US.png)

|

2.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
3.  In the left-side navigation pane, select  **Block Storage** \> **Cloud Disks**.
4.  Select a region.
5.  Find a cloud disk, in the  **Actions** column, select  **More** \> **Detach**.

    Only the cloud disks that have the following attributes can be detached:

    -   **Disk Status** must be **In Use**.
    -   **Detachable** must be **Yes**.
    -   **Used As** must be **Data Disk**.
6.  In the dialog box, click **Confirm Detaching**.

When the status of the cloud disk becomes **Available** , the disk is detached.

## Related APIs {#section_ijl_1qh_ydb .section}

[../../../../dita-oss-bucket/SP\_2/DNA0011860945/EN-US\_TP\_9887.md\#](../../../../intl.en-US/API Reference/Disk/DetachDisk.md#)

## Follow-up operations {#section_jjl_1qh_ydb .section}

If you no longer need the disk, you can [EN-US\_TP\_9685.md\#](intl.en-US/User Guide/Cloud disks/Release a cloud disk.md#).

