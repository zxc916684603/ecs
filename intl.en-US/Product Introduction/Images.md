# Images {#concept_qql_3zb_wdb .concept}

An image is a running environment template for ECS instances.  It generally includes an operating system and preinstalled software. You can use an image to create an ECS instance or change the system disk of an ECS instance. It works as a file copy that includes data from one more multiple disks.  These disks can be a single system disk, or the combination of the system disk and data disks.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9572/15330040175238_en-US.png)

## Image types {#section_nyg_r5w_ydb .section}

ECS provides a diverse types of images for you to easily access image resources.

|Type|Description |Source|
|:---|:-----------|:-----|
|Public image|Public images officially provided by Alibaba Cloud support nearly all main Windows and Linux versions.  Including:-   Windows Server
-   Centos
-   Ubuntu
-   Debian
-   SuSE Linux
-   Opensuse
-   Aliyun Linux
-   Coreos
-   Freebag

These images are of high stability and are licensed. You can customize your application environment based on a public image.|Officially provided by Alibaba Cloud|
|Custom image|Custom mirrors created based on your existing physical server, virtual machine, or cloud host. These images are flexible to meet your personalized needs.| -   You can create it based on an existing instance.
-   You can also import one from the on-premises environment into the corresponding region.

 |
|Cloud Marketplace|Provided by third-party service providers \(ISV, independent software\) Vendor\). The image of the Marketplace includes not only the operating system required for the application, but also the configuration environment. It saves you complicated deployment process and deploy the environment with one-click.| [Alibaba Cloud Marketplace](https://marketplace.alibabacloud.com/)

 |
|Shared image|Shared by other Alibaba Cloud users.|A  **Custom image** shared by ther Alibaba Cloud users.|

## Image format {#section_tyg_r5w_ydb .section}

Currently, ECS supports VHD, qcow2, and RAW.  You must convert other formats before using them in ECS

## Fees {#section_uyg_r5w_ydb .section}

Details of the images are as follows:

|Type|Fee description|
|:---|:--------------|
|Public image|Free|
|Custom image|Free.  Potential costs include:-   If you use a snapshot to create a custom image:

    -   If the image used by the system disk snapshot comes from the Marketplace, the following cost may incurr: the fees for the image, and the fees for snapshot capacity.
    -   If the image used by the system disk snapshot does not come from the Marketplace, the following cost may incurr: the fees for snapshot capacity.
Current snapshot is commercialized.

-   If you use an instance to create a custom image, and the image is from the Marketplace, comply to the billing poclicies from the ISV.

|
|Alibaba Cloud Marketplace|Subject to ISV policies. |
|Shared image|If the origine of the shared image is from the Marketplace, it is subject to the ISV policies. |

For more information, seeECS Pricing.

## Limits {#section_zyg_r5w_ydb .section}

Except for public images, custom images, Marketplace images, and shared images vary depending on the region. For more information about regions and zones, see General Reference-Regions and zones。

## Related operations {#section_u2t_hvw_ydb .section}

**Console operations**

-   You can create instances by using existing images.
-   You can change the system disk in any of the following ways:
    -   Using a public image
    -   Using other images other than public ones
-   You can obtain custom images in the following ways:
    -   Creating a custom image by using a snapshot
    -   Creating a custom image by using a an instance
    -   Importing a custom image
-   You can copy your custom images to other regions.

-   You can share your custom images with other Alibaba Cloud users.

-   You can export custom images to local testing environments or your private cloud environments.


**API operations**

You can view the .Development Guide for APIs about images.

