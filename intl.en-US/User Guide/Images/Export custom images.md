# Export custom images {#concept_wfq_vdt_xdb .concept}

You can export custom images for on-premise testing or Apsara stack environments.

**Note:** 

-   Exporting custom images is a time-consuming task, so you need to wait patiently. The duration of exporting depends on the size of the image file and the number of export tasks in the queue.
-   The exported images are stored in your [OSS](../../../../reseller.en-US/Product Introduction/What is OSS?.md#) bucket. You are billed for the OSS storage and download traffic. For more information, see OSS [Billing items](../../../../reseller.en-US/Pricing/Billing items.md#).

## Limitations {#section_mcn_12t_xdb .section}

Currently, the image export function has the following limitations:

-   You cannot export the custom images that are created by a system disk snapshot from the [marketplace](reseller.en-US/User Guide/Images/Cloud market Images .md#).
-   You can export the custom images that contain four snapshots of data disks at most, and for a single data disk, the maximum volume must be no greater than 500 GiB.
-   When using exported images to [create an instance by using the wizard](reseller.en-US/User Guide/Instances/Create an instance/Create an instance of the same configuration.md#), you need to confirm that the file device recorded in /etc/fstab corresponds to the exported data disk snapshot information.

## Prerequisites {#section_b41_g2t_xdb .section}

Before exporting a custom image, you need to do the following:

-   Open a ticket to activate the image export feature, and describe the use cases of the exported images in the ticket.
-   Activate OSS and make sure that the region where your custom images are located has an available OSS bucket. For more information, see OSS [Create a bucket](../../../../reseller.en-US/Quick Start/Create a bucket.md#).

## Procedure {#section_wwm_h2t_xdb .section}

To export a custom image in the ECS console, follow these steps:

1.  Log on to the [ECS Console](https://partners-intl.console.aliyun.com/#/ecs).
2.  In the left-side navigation pane, choose **Snapshot & Images** \> **Images**.
3.  Select a region.
4.  Find the custom image you want to export. In the **Action** column, click **Export Image**.
    1.  In the Export Image dialog box, click **Confirm Address** shown in the figure below.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9712/15381893964655_en-US.png)

    2.  In the Cloud Resource Access Authorization window, click **Confirm Authorization Policy** to allow ECS to access your OSS resources.
5.  Return to the ECS Console homepage. In the **Actions** column of the Images page, click **Export Image** again.
6.  In the Export Image dialog box:
    -   Select the OSS bucket in the specified region.
    -   Set the prefix of the object name of the exported image. For example, if you set Demo as the prefix, then the exported image file displayed in the OSS bucket is named Demo-\[automatically generated file name\].
7.  Click **OK** to export the image.
8.  \(Optional\) Cancel the image export task. Before the task is completed, you can go to the [**Manage Tasks**](https://partners-intl.console.aliyun.com/#/ecs/task/region/cn-qingdao) page in the ECS Console, find the relevant task in the specified region and cancel the task.

You can also use the ECS APIs [ExportImage](../../../../reseller.en-US/API Reference/Images/ExportImage.md#) and [CancelTask](../../../../reseller.en-US/API Reference/Others/CancelTask.md#) to perform the above operations.

## Next steps {#section_qlv_v2t_xdb .section}

1.  Log on to the [OSS Console](https://partners-intl.console.aliyun.com/#/oss) to query the export result.

    **Note:** When an exported custom image contains a data disk snapshot, multiple files appear in your OSS. The file name with `system` indicates a system disk shapshot and the file name with `data` indicates a data disk snapshot. A data disk snapshot has an identifier corresponding to the data disk, which is the mount point of the data disk, such as xvdb or xvdc.

2.  After the custom image is exported successful, [download the object](../../../../reseller.en-US/Console User Guide/Manage objects/Download an object.md#) and then download the custom image file. The format of the image file is defaulted to RAW.

