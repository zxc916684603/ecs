# Images {#concept_qql_3zb_wdb .concept}

An image is a running environment template for ECS instances. It generally includes an operating system and preinstalled software. You can use an image to create an ECS instance or change the system disk of an ECS instance. It works as a file copy that includes data from one more multiple disks. These disks can be a single system disk, or the combination of the system disk and data disks.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9572/15416586395238_en-US.png)

## Image types {#section_nyg_r5w_ydb .section}

ECS provides a diverse types of images for you to easily access image resources.

|Type|Description |Source|
|:---|:-----------|:-----|
|Public image|Public images officially provided by Alibaba Cloud support nearly all main Windows and Linux versions. These images are of high stability and are licensed. You can customize your application environment based on a public image.|Officially provided by Alibaba Cloud|
|Custom image|Custom images created based on your existing physical server, virtual machine, or cloud host. These images are flexible to meet your personalized needs.| -   You can create it based on an existing instance.
-   You can also import one from the on-premises environment into the corresponding region.

 |
|Cloud Marketplace|Provided by third-party service providers \(ISV, independent software\) Vendor\). The image of the Marketplace includes not only the operating system required for the application, but also the configuration environment. It saves you complicated deployment process and deploy the environment with one-click.| Alibaba Cloud Marketplace

 |
|Shared image|Shared by other Alibaba Cloud users.|A custom image shared by other Alibaba Cloud users.|

## Public images {#PublicImage .section}

Alibaba Cloud provides authorized and certificated public images, which cover nearly all the trending and popular platforms. Note that the available public images are different when you select different instances. For the built-in service contained in the various public image releases, please go to the official website of the operating system provider for reference. The following images are offered by Alibaba Cloud ECS for public use:

|Platform|Version of public images|
|:-------|:-----------------------|
|Windows Server| -   Windows Server 2008 R2 Enterprise Edition 64 bit Chinese Edition
-   Windows Server 2008 R2 Enterprise Edition 64 bit English Edition
-   Windows Server 2012 R2 Data Center Edition 64 bit Chinese Edition
-   Windows Server 2012 R2 Data Center Edition 64 bit English Edition
-   Windows Server 2016 R2 Data Center Edition 64 bit Chinese Edition
-   Windows Server 2016 R2 Data Center Edition 64 bit English Edition
-   Windows Server Version 1709 Data Center Edition 64 bit Chinese Edition
-   Windows Server Version 1709 Data Center Edition 64 bit English Edition

 |
|CentOS| -   CentOS 6.8 64bit
-   CentOS 6.8 32bit
-   CentOS 6.9 64bit
-   CentOS 7.2 64bit
-   CentOS 7.3 64bit
-   CentOS 7.4 64bit
-   CentOS 7.5 64bit

 |
|Ubuntu| -   Ubuntu 14.04 64bit
-   Ubuntu 14.04 32bit
-   Ubuntu 16.04 64bit
-   Ubuntu 16.04 32bit

 |
|Debian| -   Debian 8.9 64bit
-   Debian 9.2 64bit
-   Debian 9.5 64bit

 |
|Red Hat| -   Red Hat Enterprise Linux 7.5 64bit
-   Red Hat Enterprise Linux 7.4 64bit
-   Red Hat Enterprise Linux 6.9 64bit

 |
|SUSE Linux| -   SUSE Linux Enterprise Server 11 SP4 64bit
-   SUSE Linux Enterprise Server 12 SP4 64bit

 |
|OpenSUSE|OpenSUSE 42.3 64bit|
|Aliyun Linux|Aliyun Linux 17.1 64bit|
|CoreOS|CoreOS 1465.8.0 64bit|
|FreeBSD|FreeBSD 11.1 64bit|

## Image format {#section_tyg_r5w_ydb .section}

Currently, ECS supports VHD, qcow2, and RAW. You must convert other formats before using them in ECS.

## Billing details {#section_uyg_r5w_ydb .section}

Billing details of the images are as follows:

|Type|Description|
|:---|:----------|
|Public image| Only Windows Server and Red Hat Enterprise Linux public images involve billing calculation, which are included in the bill when an instance is created. The public Windows Sever images or Red Hat Enterprise Linux images are provided with certificated license and authorized support from Microsoft or Red Hat, you do have to purchase additional license.

-   Red Hat Enterprise Linux: Billing is related to the instance type.
-   Windows Server: Free of charge in Alibaba Cloud regions that are in mainland China. For international regions, public Windows Server images are charging services.

 Other public images are free of charge to use.

 |
|Custom image|Free. Potential costs include:-   If you use a snapshot to create a custom image:

    -   If the image used by the system disk snapshot comes from the Marketplace, the following cost may incur: the fees for the image, and the fees for snapshot capacity.
    -   If the image used by the system disk snapshot does not come from the Marketplace, the following cost may incur: the fees for snapshot capacity.
Currently, snapshot is commercialized.

-   If you use an instance to create a custom image, and the image is from the Marketplace, comply to the billing policies from the ISV.

|
|Alibaba Cloud Marketplace|Subject to ISV policies.|
|Shared image|If the origin of the shared image is from the Marketplace, it is subject to the ISV policies.|

For more information, see [Pricing overview](../../../../reseller.en-US/Pricing/Pricing overview.md#).

## Limits {#section_zyg_r5w_ydb .section}

Custom images, marketplace images, and shared images vary depending on the region. For more information about regions and zones, see General Reference [Regions and zones](https://partners-intl.aliyun.com/help/doc-detail/40654.htm).

## Related operations {#section_u2t_hvw_ydb .section}

**Console operations**

-   You can [create instances by using existing images](../../../../reseller.en-US/User Guide/Instances/Create an instance/Create an instance from a custom image.md#).

-   You can change the system disk in any of the following ways:
    -   [By using a public image](../../../../reseller.en-US/User Guide/Cloud disks/Replace the system disk (public image).md#).

    -   [By using other images other than public ones](../../../../reseller.en-US/User Guide/Cloud disks/Replace the system disk (non-public image).md#).

-   You can obtain custom images in the following ways:
    -   [By creating a custom image by using a snapshot](../../../../reseller.en-US/User Guide/Images/Create custom image/Create a custom image by using a snapshot.md#).

    -   [By creating a custom image by using a an instance](../../../../reseller.en-US/User Guide/Images/Create custom image/Create a custom image by using an instance.md#).

    -   [By importing a custom image](../../../../reseller.en-US/User Guide/Images/Import images/Notes for importing images.md#).

-   After creating custom images, you can perform the following operations:
    -   [Copy your custom images to other regions](../../../../reseller.en-US/User Guide/Images/Copy images.md#).

    -   [Share your custom images with other Alibaba Cloud users](../../../../reseller.en-US/User Guide/Images/Share images.md#).

    -   [Export custom images](../../../../reseller.en-US/User Guide/Images/Export custom images.md#) to local testing environments or your private cloud environments.


**API operations**

You can view the [APIs about images](../../../../reseller.en-US/API Reference/API overview.md#section_image_t2h_vdb) in the Developer Guide.

