# Delete automatic snapshots when releasing disks {#concept_c45_jml_xdb .concept}

The automatic snapshots of cloud disks are not released along with the cloud by default. However, you can change the disk property so that automatic snapshots are released when you:

-   [Change the system disk \(custom image\)](intl.en-US/User Guide/Cloud disks/Change the system disk (custom image).md#): The previous system disks are released. If an automatic snapshot has been set up to release with the cloud disks, the automatic snapshots of the previous system disks are automatically deleted.
-   [Detach a cloud disk](intl.en-US/User Guide/Cloud disks/Detach a cloud disk.md#).

## Procedure {#section_upq_ynl_xdb .section}

Follow these steps:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  Select a region.
3.  In the left-side navigation pane, click **Block Storage** \> **Disks** .
4.  Select the disk that you want to configure, and in the **Actions** column, click **More** \> **Modify Attributes**.
5.  In the **Modify Disk Type** dialog box, select **Delete Automatic Snapshots while Releasing Disk**, and then click **OK**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9690/15353593774573_en-US.png)


## Related API {#section_wgl_bpl_xdb .section}

[ModifyDiskAttribute](../../../../intl.en-US/API Reference/Disk/ModifyDiskAttribute.md#)

