# Images {#concept_qql_3zb_wdb .concept}

An image is a running environment template for ECS instances. It generally includes an operating system and pre-installed software. An image works as a file copy that includes data from one or more disks. These disks can be a single system disk, or a combination of the system disk and data disks.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9572/15444920525238_en-US.png)

## Image types {#section_nyg_r5w_ydb .section}

ECS provides a range of image types that you can use to easily access image resources.

|Type|Description|Source|
|:---|:----------|:-----|
|Public image|Public images are officially provided by Alibaba Cloud and support nearly all main Windows and Linux versions.|Alibaba Cloud has established partnerships with the operating system vendors. These images are licensed.|
|Custom image|Custom images created based on your existing physical server, virtual machine, or cloud host. These images are flexible to meet your personalized needs.| -   You can create it based on an existing instance.
-   You can also import one from the on-premises environment into the corresponding region.

 |
|Cloud Marketplace image|Provided by third-party service providers, that is, Independent Software Vendors \(ISVs\). Images of the Marketplace include not only the operating system required for the application, but also the configuration environment. They allow you to avoid the complicated deployment process and deploy the environment with one-click.| [Cloud Marketplace](https://marketplace.alibabacloud.com/)

 |
|Shared image|Shared by other Alibaba Cloud users.|Custom images created by other Alibaba Cloud users.|

## Public images {#PublicImage .section}

These images are fully licensed and provide a highly stable execution environment. You can customize your application environment based on a public image. Note that the availability of public images is determined based on your selected instance. For the built-in service contained in the various public image releases, please go to the official website of the operating system provider for reference. The following images are offered by Alibaba Cloud ECS for public use:

|Platform|Version of public images|
|:-------|:-----------------------|
|Windows Server| -   Windows Server 2008 Standard Edition SP2 32bit Chinese Edition
-   Windows Server 2008 R2 Enterprise Edition 64bit Chinese Edition
-   Windows Server 2008 R2 Enterprise Edition 64bit English Edition
-   Windows Server 2012 R2 Data Center Edition 64bit Chinese Edition
-   Windows Server 2012 R2 Data Center Edition 64bit English Edition
-   Windows Server 2016 R2 Data Center Edition 64bit Chinese Edition
-   Windows Server 2016 R2 Data Center Edition 64bit English Edition
-   Windows Server Version 1709 Data Center Edition 64bit Chinese Edition
-   Windows Server Version 1709 Data Center Edition 64bit English Edition

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

## Image formats {#section_tyg_r5w_ydb .section}

Currently, ECS supports VHD, qcow2, and RAW. You must [convert other formats](../intl.en-US/User Guide/Images/Import images/Convert image file format.md#) before using them in ECS.

## Billing details {#section_uyg_r5w_ydb .section}

Billing details of the images are as follows:We recommend that you maintain a sufficient balance in the linked credit card or PayPal account to complete the payment or preauthorization. For more information, see [Pricing overview](../intl.en-US/Pricing/Pricing overview.md#).

|Type|Description|
|:---|:----------|
|Public image| Only Windows Server and Red Hat Enterprise Linux public images incur fees, which are included in the bill when an instance is created. The public Windows Sever images or Red Hat Enterprise Linux images are provided with certified licenses and authorized support from Microsoft or Red Hat, you do not have to purchase additional licenses.

-   Red Hat Enterprise Linux: Billing is related to the instance type.
-   Windows Server: Free of charge in Alibaba Cloud regions that are in Mainland China. For international regions, the use of public Windows Server images incur fees.

 Other public images are available free of charge.

 |
|Custom image| -   If you [create a custom image by using a snapshot](../intl.en-US/User Guide/Images/Create custom image/Create a custom image by using a snapshot.md#):
    -   If the image used by the system disk snapshot is from the Marketplace, costs incurred may include fees for the image, and fees for snapshot capacity.
    -   If the image used by the system disk snapshot is not from the Marketplace, costs incurred may include fees for the snapshot capacity.

**Note:** 

-   If you [use an instance to create a custom image](../intl.en-US/User Guide/Images/Create custom image/Create a custom image by using an instance.md#), and the image of that instance is from the Marketplace, you must adhere to the billing policies of the Marketplace and the ISV.

 |
|Cloud Marketplace image|Subject to ISV policies.|
|Shared image|If the origin of the shared image is the Marketplace, it is subject to the ISV policies.|

## Limitations {#section_zyg_r5w_ydb .section}

The limitations of custom images, Marketplace images, and shared images vary depending on the region. For more information, see [Regions and zones](../../../../../intl.en-US/General Reference/Regions and zones.md#).

## Technical support {#section_ejc_1rz_zfb .section}

For different types of images, we provide the following technical support:

-   Public images
    -   Aliyun Linux images

        Provided by Alibaba Cloud, Aliyun Linux images are custom operating systems for ECS instances. We have undertaken strict testing of these images to ensure their security and stability.

        We provide [technical support](https://workorder-intl.console.aliyun.com/#/ticket/createIndex) for the problems that occur during the use of Aliyun Linux operating systems.

    -   Third-party commercial images and open source images

        Third-party commercial and open source images include images of Windows, Ubuntu, CentOS, Redhat Enterprise Linux, Debian, SUSE Linux, FreeBSD, and CoreOS. They are created and tested strictly by the Alibaba Cloud team to ensure their safety and stability.

        If you experience any problems during use, you can contact their original producers for technical support. At the same time, we provide technical assistance in the investigation of the problems.

-   Cloud Marketplace images

    Marketplace images are provided by vendors authorized by Alibaba Cloud. All of these images are strictly tested by both the vendors and Alibaba Cloud to ensure the safety of their contents.

    If you experience any problems during use, you can contact their vendors for technical support.

-   Custom images

    Custom images include the custom images created from public images and Marketplace images by users and imported custom images.

    If you experience any problems during use, you can contact their original producers for technical support. At the same time, we provide technical assistance in the investigation of the problems.


## Related operations {#section_u2t_hvw_ydb .section}

**Console operations**

-   You can [create instances by using existing images](../intl.en-US/User Guide/Instances/Create an instance/Create an instance from a custom image.md#).
-   You can change the system disk of an ECS instance in any of the following ways:
    -   [By using a public image.](../intl.en-US/User Guide/Cloud disks/Replace the system disk (public image).md#)
    -   [By using other images other than public ones.](../intl.en-US/User Guide/Cloud disks/Replace the system disk (non-public image).md#)
-   You can obtain custom images in the following ways:
    -   [By creating a custom image from a snapshot.](../intl.en-US/User Guide/Images/Create custom image/Create a custom image by using a snapshot.md#)
    -   [By creating a custom image based on an instance.](../intl.en-US/User Guide/Images/Create custom image/Create a custom image by using an instance.md#)
    -   [By importing an on-premises custom image.](../intl.en-US/User Guide/Images/Import images/Notes for importing images.md#)
-   After creating custom images, you can perform the following operations:
    -   [Copy your custom images to other regions.](../intl.en-US/User Guide/Images/Copy images.md#)
    -   [Share your custom images with other Alibaba Cloud users.](../intl.en-US/User Guide/Images/Share images.md#)
    -   [Export custom images to local testing environments or your private cloud environments.](../intl.en-US/User Guide/Images/Export custom images.md#)

**API operations**

For more information, see the [APIs for images](../intl.en-US/API Reference/API overview.md#section_image_t2h_vdb) part in the Developer Guide.

