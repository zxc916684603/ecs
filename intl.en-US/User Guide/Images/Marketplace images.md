# Marketplace images {#concept_spg_mct_xdb .concept}

A Marketplace image is equivalent to the installation disk for an Elastic Compute Service \(ECS\) instance. A Marketplace image allows you to quickly obtain a running environment for ECS instances and preinstalled software applications. This allows ECS instances to be used out-of-the-box, reduces costs in the application of ECS instances, and brings considerable convenience. The image can be used to satisfy your specific business needs, including site deployment, application development, and visualized management. Alternatively, you can manually configure the running environment and install software applications.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9711/15409786224649_en-US.png)

## Select a Marketplace image when creating an instance {#section_fhq_yqg_q2b .section}

We recommend that you use a Marketplace image if you are new to working with ECS instances.

1.  Go to the [ECS purchase](https://ecs-buy.aliyun.com/?spm=a2c4g.11186623.2.1.05b1ZM#/prepay) page.
2.  Select and configure your image. For more information, see [Create an Instance](../reseller.en-US/Quick Start for Entry-Level Users/Step 2. Create an instance.md#). Then, on the **Image** configuration page, choose **Marketplace Image** \> **Select from image market \(including operating system\)**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9711/15409786224652_en-US.png)


## Purchase an image from Alibaba Cloud Marketplace and create an instance {#section_ldn_11h_q2b .section}

1.  Go to [Alibaba Cloud Marketplace](https://partners-intl.aliyun.com/marketplace/vodafone/).
2.  Select the image that you need and click **Buy Now**.
3.  You may required to log on to the Alibaba Cloud console before proceeding.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9711/15409786224653_en-US.png)

4.  Select and configure your image. For more information, see [Create an instance](../reseller.en-US/Quick Start for Entry-Level Users/Step 2. Create an instance.md#).

## Change the operating system by using the Marketplace image {#section_gvt_2dt_xdb .section}

If you have purchased ECS instances, use an image to deploy the running environment, or install software applications as follows:

**Note:** If you change the image, the data on the system disk will be lost. Therefore, we recommend that you back up your data before changing your operating system. For more information, see [Create snapshots](reseller.en-US/User Guide/Snapshots/Create snapshots.md#).

1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).
2.  Stop the target instance.
3.  On the Replace System Disk page, select **Marketplace Image** in the **Image Type** setting. For more information, see [Replace the system disk \(non-public image\)](reseller.en-US/User Guide/Cloud disks/Replace the system disk (non-public image).md#). You can then use your required image.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9711/15409786224654_en-US.png)

