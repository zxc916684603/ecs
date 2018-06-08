# Import custom images {#concept_w4x_4ms_xdb .concept}

You can import image files to the ECS environment to create custom images.  You can then use these images to create ECS instances or change system disks.

**Note:** 

When you import a mirror, a snapshot is created, because the snapshot service has already started charging for it. The Snapshot capacity is the size of the imported mirror file, regardless of the System Disk size that was set when the mirror was imported.

## Prerequisite {#section_jn1_5ns_xdb .section}

Before importing a mirror, you should have done the following:

-   For the limits and requirements of importing custom images, See [EN-US\_TP\_9702.md\#](intl.en-US/User Guide/Images/Import images/Notes for importing custom images.md#), [Configure Customized Linux images](intl.en-US/User Guide/Images/Import images/Configure Customized Linux images.md#), and [Convert image file format](intl.en-US/User Guide/Images/Import images/Convert image file format.md#)
-   [../../SP\_21/DNOSS11894847/EN-US\_TP\_4331.md\#](../../intl.en-US/Quick Start/Sign up for OSS.md#).
-   You can only import an image file to a region from OSS in the same region. The image and the OSS must belong to one account.
-   You can use an OSS third-party tool client, OSS API or OSS SDK, to upload the file to a bucket in the same region as the ECS custom image to import.  See [Multipart upload](../../intl.en-US/Developer Guide/Upload files/Multipart upload.md#) to upload an image file that is larger than 5 GiB.

## Procedures {#section_nc3_yns_xdb .section}

1.  Log on to the OSS console, [Get object URL](../../intl.en-US/Console User Guide/Manage objects/Get object URL.md#).
2.  Follow these steps to authorize the ECS service to access your OSS resources:
    1.  Log on to the [ECS console](https://ecs.console.aliyun.com/).
    2.  In the left-side navigation pane, choose **Snapshots and Images** \> **Images**.
    3.  Click **Import Image**.
    4.  On the third items of How to import an image. Click **Confirm Address**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9706/4630_en-US.png)

    5.  Click Confirm Authorization Policy on the Cloud Resource Access Authorization page. Go back to the ECS console.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9706/4631_en-US.png)

3.  In the left-side navigation pane, choose  **Snapshots and Images** \> **Images**.
4.  Click  **Import Image**, 
5.  Enter the following information in the Import Image pop-up window:
    -   **Region of image**: Select the region where you want to deploy the application.
    -   **OSS Object Address**: Copy the object address taken from the OSS console.
    -   **OSS Object Address**: Copy the object address taken from the OSS console. It can be 2 to 128 characters in length. Begins with lower case Latin letters or Chinese characters. Allows numbers, periods \(.\), underscores \(\_\), colons \(:\), and hyphens \(-\).
    -   **Operating System**: Supported OS releases are Windows or Linux. If you want to import a non-standard platform image,  select Linux.
    -   **System Disk size**: The system disk size range is 40 Gib-500 Gib.
    -   **System Architecture**: Choose **x86\_64** for 64 bit operating systems and choose **i386** for 32 bit operating systems and choose.
    -   **System Platform**: The system platform Depends on the **Operating System** you choosed. Avaliable options:
        -   Windows:  Windows Server 2003, Windows Server 2008, and Windows Server 2012.
        -   Linux: Centos, Suse, Ubuntu, Debian, FreeBSD, CoreOS, Aliyun, Customized Linux, and Others Linux. \(Linux only\) [Open a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex) to confirm the selected edition is supported.
        -   If your image OS is a custom edition developed from Linux kernel, [open a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex) to contact us.
    -   **Image Format**: Supports RAW and VHD format. RAW format is recommended. Note that you cannot use qemu-image to create VHD images.
    -   **Image Description**: The description of the image.
    -   \(Optional\) If you want to import an image that contains data disks, choose  **Add Images of Data Disks**, and follow the page prompts to set information. Supported data disk capacity range is 5 GiB-2000 GiB.
    -   After the information is confirmed, click **OK** to create a task to import the image.

**Note:** 

-   It usually takes 1 to 4 hours to import an image. The duration of the task depends on the size of your image file and the amount of concurrent tasks. You can view the task progress in the image list of the import region.
-   We create snapshots for you when importing images, you can check the **Snapshot** list for progress monitoring. Before the import mirror task is complete, the status of the snapshot is displayed as **Failed**. When the task completes, the status is automatically updated **Available**.

You can find and cancel the image import task in the [task manager](https://ecs.console.aliyun.com/#/task/region/).

## Next steps {#section_mhq_zps_xdb .section}

After you import the custom image, you may want to [Create an instance from a custom image](intl.en-US/User Guide/Instances/Create an instance/Create an instance from a custom image.md#).

## See also {#section_pkr_1qs_xdb .section}

-   [Images](../intl.en-US/Product Introduction/Images.md#)
-   [Custom images FAQ](https://www.alibabacloud.com/help/faq-detail/40549.htm)
-   [Export custom images](intl.en-US/User Guide/Images/Export custom images.md#)
-   [Create and import on-premise images by using Packer](intl.en-US/User Guide/Images/Import images/Create and import on-premise images by using Packer.md#)
-   [Use Packer to create a custom image](intl.en-US/User Guide/Images/Create custom image/Use Packer to create a custom image.md#)
-   [Copy custom images](intl.en-US/User Guide/Images/Copy custom images.md#)
-   [Share images](intl.en-US/User Guide/Images/Share images.md#)

