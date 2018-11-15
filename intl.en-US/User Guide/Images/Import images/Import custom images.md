# Import custom images {#concept_w4x_4ms_xdb .concept}

You can import on-premise image files to the ECS environment for deploying your business. Imported custom images appear in your custom images list under the target region. You can use these images to create ECS instances or change system disks.

**Note:** 

-   Importing custom images is a time consuming task. The duration depends on the size of the image file and the number of concurrent tasks, so you need to wait patiently.
-   When you import an image, a snapshot is automatically generated. You can view the snapshot information on the **Snapshots** page in the ECS Console. Before the import image task is completed, the status of the snapshot is displayed as **Failed**. When the task is completed, the status is automatically updated to **Successful**. The Snapshot capacity is the size of the imported image file, regardless of the System Disk size that was set when the image was imported.

## Prerequisites {#section_jn1_5ns_xdb .section}

Before importing an image, you should have done the following:

-   Learn about the limitations and requirements of importing custom images by referring to [Notes for importing images](reseller.en-US/User Guide/Images/Import images/Notes for importing images.md#), [Customize Linux images](reseller.en-US/User Guide/Images/Import images/Customize Linux images.md#), and [Convert image format](reseller.en-US/User Guide/Images/Import images/Convert image file format.md#).
-   [Sign up for OSS](../../../../../reseller.en-US/Quick Start/Sign up for OSS.md#).
-   \(Optional\) If you are using a RAM sub-account, you need to contact the master account in advance to obtain the permission for the `AliyunECSImageImportDefaultRole` role.

## Procedure {#section_nc3_yns_xdb .section}

To import custom images in the ECS console, perform these steps:

1.  You can use an OSS third-party client, OSS API or OSS SDK to upload the prepared custom image. For how to upload a file larger than 5 GiB, see *OSS* [Multipart upload](../../../../../reseller.en-US/Developer Guide/Upload files/Multipart upload.md#).
2.  Log on to [ECS console](https://partners-intl.console.aliyun.com/#/ecs).
3.  In the left-side navigation pane, choose **Snapshots and Images** \> **Images**.
4.  On the Images page, click **Import Image**.
5.  In the Import Image dialog box, click **Confirm Address** as shown below.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9706/15394815097027_en-US.png)
6.  In the Cloud Resource Access Authorization window, select `AliyunECSImageImportDefaultRole` and `AliyunECSExportDefaultRole`, then click **Confirm Authorization Policy** to allow the ECS service to access your OSS resources.
7.  On the Images page, click **Import Image** again.
8.  In the Import Image dialog box, enter the following information:
    -   **Region of Image**: Select the region where the OSS Bucket of the image file to upload is located.
    -   **OSS Object Address**: Copy the object address of the image file from the OSS console. For more information, see *OSS* [Download an object](../../../../../reseller.en-US/Console User Guide/Manage objects/Download an object.md#).
    -   **Image Name**: Specify the name of the custom image file displayed after it is imported. It can be 2 to 128 characters in length. Beginning with upper/lower case letters or Chinese characters, it allows numbers, periods \(.\), underscores \(\_\), colons \(:\), and hyphens \(-\).
    -   **Operating System**: Select **Windows** or **Linux**, which should be the same as that of your image. If you want to import a non-standard platform image, select Linux.
    -   **System Disk Size**: The system disk size ranges from 40 GiB to 500 GiB.
    -   **System Architecture**: Choose **x86\_64** for 64 bit operating systems and choose **i386** for 32 bit operating systems.
    -   **System Platform**: The options depend on the **Operating System** you chose.
        -   Windows: Windows Server 2003, Windows Server 2008, and Windows Server 2012.
        -   Linux: Centos, SUSE, Ubuntu, Debian, FreeBSD, CoreOS, Aliyun, Customized Linux, and Others Linux \(open a ticket to confirm the selected edition is supported\).
        -   If your image OS is a custom edition developed from Linux kernel, open a ticket to contact us.
    -   **Image Format**: Supports qcow2, RAW, and VHD. Qcow2 or VHD is recommended.
    -   **Image Description**: Fill up the description of the image to facilitate subsequent management.
    -   **Add Images of Data Disks**: Choose this option if you want to import an image that contains data disks. Supported data disk capacity ranges from 5 GiB to 2,000 GiB.
9.  After the information is confirmed, click **OK** to create a task to import the image.
10. \(Optional\) You can view the task progress in the image list of the import region. Before the task is completed, you can find the imported custom image through [Manage Tasks](https://partners-intl.console.aliyun.com/#/ecs/task/region/), then cancel the import task.

You can also use the ECS API [ImportImage](../reseller.en-US/API Reference/Images/ImportImage.md#) to import a custom image.

## Next step {#section_mhq_zps_xdb .section}

[Create an instance from a custom image](reseller.en-US/User Guide/Instances/Create an instance/Create an instance from a custom image.md#)

## References {#section_pkr_1qs_xdb .section}

-   [Custom images FAQ](https://partners-intl.aliyun.com/help/faq-detail/40549.htm)
-   [Create and import on-premise images by using Packer](reseller.en-US/User Guide/Images/Open source tools/Create and import on-premise images by using Packer.md#)

