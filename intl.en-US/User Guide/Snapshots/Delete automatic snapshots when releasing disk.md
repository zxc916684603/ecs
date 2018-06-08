# Delete automatic snapshots when releasing disk {#concept_c45_jml_xdb .concept}

The automatic snapshots of cloud disks are not released along with the cloud by default. However, you can change the property so that automatic snapshots are released with the following:

-   [Change the system disk \(custom image\)](intl.en-US/User Guide/Cloud disks/Change the system disk (custom image).md#): The previous system disks are releases. If an automatic snapshot has been set up to release with the cloud disks, the automatic snapshots of the previous  system disks are automatically deleted.
-   [Detach a cloud disk](intl.en-US/User Guide/Cloud disks/Detach a cloud disk.md#)

## Procedures {#section_upq_ynl_xdb .section}

To retain auto snapshots when releasing the disk, perform the following:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  Select a region.
3.  In the left-side navigation pane, click **Storage** \> **Cloud Disks** .
4.  Select the disk that you want to configure and click **Actions**  \> **More** \> **Modify Attributes**.
5.  In the  **Modify Disk Attributes** dialog box, select **Delete automatic snapshots when releasing disk**, and then click OK.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9690/4573_en-US.png)


## Related API {#section_wgl_bpl_xdb .section}

[ModifyDiskAttribute](../intl.en-US/API Reference/Disk/ModifyDiskAttribute.md#)

