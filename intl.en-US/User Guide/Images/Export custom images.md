# Export custom images {#concept_wfq_vdt_xdb .concept}

You can export custom images to a local device for test purposes or to offline private stack. This topic describes the limits of the image export function, and provides instructions on how to export images in the ECS console.

**Note:** 

Note that exported images are stored in your OSS bucket, which must be in the same region as the custom images. You are biiled for the data used of for OSS storage and downloading.

## Limits {#section_mcn_12t_xdb .section}

Currently, the image export function has the following constraints and restrictions:

-   The image export function is usable before it is [whitelisted](https://workorder-intl.console.aliyun.com/#/ticket/createIndex).
-   You cannot export the custom images that are created by a system disk snapshot from the marketplace.
-   You can export the custom images that contain four snapshots of data disks at most, and for a single data disk, the maximum volume must be less than 500 GB.
-   The default format of exported image files is RAW.

## Precautions {#section_nkx_d2t_xdb .section}

-   When you export images that contain data disk snapshot, the snapshot and image files are shown in your OSS bucket.
    -   A snapshot of the system disk has a system in the file name.
    -   A snapshot of the data disk has data in the file name. The data disk snapshot will have the identity corresponding to the data disk, which is the mount point of the data disk, such as xvdb or xvdc.
-   When using exported images to [Create an instance of the same configuration](intl.en-US/User Guide/Instances/Create an instance/Create an instance of the same configuration.md#), you need to confirm that the file device recorded in /etc/fstab records corresponds to the exported data disk snapshot information.

## Prerequisites {#section_b41_g2t_xdb .section}

Before exporting a custom image, you need to do the following:

-   [Open a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex) to activate the image export feature. Describe the use cases of the exported images in the ticket.
-   Activate OSS and make sure that the region where your custom images are located has an available OSS bucket.  See [Create a bucket](../../../../intl.en-US/Quick Start/Create a bucket.md#).  to create an OSS bucket.

## Procedure {#section_wwm_h2t_xdb .section}

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  Select a region.
3.  \(Optional\) Authorize the ECS service to access your OSS bucket:
    1.  Choose  **Snapshots & Images** \> **Images**in the left-side navigation pane.
    2.  Find the custom image you want to export. In the **Action** column,  click **Export** Image.
    3.  In the Export Image  dialog box, click **Confirm Address** in Step 3 of the prompt message.
    4.  In the Cloud Resource Access Authorization window, click **Confirm Authorization Policy**. Return to the ECS console homepage.
4.  In the left-side navigation pane, choose **Snapshot & Images** \> **Images**.
5.  Find the custom image you want to export, In the **Action**  column, click **Export Image**.
6.  In the Export Image dialog box:
    -   Select the OSS bucket in the specified region.
    -   Set the prefix of the object name of the exported image. For example, if you set Demo as the prefix, then the exported image file displayed in the OSS bucket is named  Demo-\[automatically generated file name\].
7.  Click **OK** to export the image.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9712/15356106544655_en-US.png)


The duration of exporting depends on the size of the image file and the number of other export tasks in the queue. Be patient. You can go to the [**Manage Tasks**](https://ecs.console.aliyun.com/#/task/region/cn-qingdao) page in the ECS console to query the task progress based on the task ID.  When  the **Task Status** is Task **Completed**, the image is successfully exported.

To cancel the export task, go to the [**Manage Tasks**](https://ecs.console.aliyun.com/#/task/region/cn-qingdao) page and find the task.

## Next step {#section_qlv_v2t_xdb .section}

-   To query the export result, log on to the [OSS console](https://oss.console.aliyun.com/index#/).
-   To download the exported image file, log on to the OSS console [Get object URL](../../../../intl.en-US/Console User Guide/Manage objects/Get object URL.md#) and Get object URL.

