# Share images {#concept_e1j_jgm_xdb .concept}

After creating a custom image, you can share it with other Alibaba Cloud users. Shared images help new users adapt to ECS faster as they can quickly create ECS instances and set up business environments based on your custom images. Moreover, shared images do not consume the image quota of those who share an image.

## Attention {#section_v3m_rgm_xdb .section}

You can only share your own custom images, not the images shared by other users. Each custom image can be shared with up to 50 users within the same Alibaba Cloud region. That is, an image cannot be shared across regions.

Before sharing an image, make sure that sensitive data and files have been removed from the image.

**Note:** The integrity or security of shared images is not guaranteed. Make sure that you use only images shared by trusted accounts before using shared images. Besides, you shall bear the risk on your own. After you create an instance based on a shared image, be sure to [connect the instance](reseller.en-US/User Guide/Connect to instances/Overview.md#) to check the integrity and security of the image.

**Impacts of deleting shared images**

If your custom image has been shared with other accounts, you need to remove all the sharing relationships for that image before you can delete the image. After deleting a shared custom image:

-   The users who are using the shared image can no longer find the image through the ECS console or ECS API, nor can they use the image to create ECS instances or replace system disks.
-   ECS instances that are created from the shared image cannot re-initialize their system disks.

## Share an image {#section_g5c_dgn_j2b .section}

To share an image in the ECS console, perform the following steps:

1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).
2.  Select a region.
3.  In the left-side navigation pane, choose **Snapshots and Images** \> **Images**.
4.  Select a **Custom Image**. In the **Actions** column, click **Share Image**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9700/15394855796790_en-US.png)

5.  In the pop-up dialog box, select **Alibaba Cloud Account ID** in the **Account Type** drop-down list. Then, enter the account ID you want to share the image with in the **Account** box. You can refer to [Appendix. How to get the account ID](#HowToFindAccountId) to get the Alibaba Cloud account ID.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9700/15394855796801_en-US.png)

    **Note:** If you want to stop sharing the image with an account, click **Unshare** next to the account. After you cancel the sharing, that account will be unable to query and use the image. If that account has already created an instance by using this shared image, the instance will be unable to [re-initialize the system disk](reseller.en-US/User Guide/Cloud disks/Reinitialize a cloud disk.md#).

6.  \(Optional\) For those with whom you share an image, they can view the shared image in **Snapshots and Images** \> **Images** \> **Share Image** in the same region in the ECS console.

You can also use the ECS APIs [ModifyImageSharePermission](reseller.en-US/API Reference/Images/ModifyImageSharePermission.md#) and [DescribeImageSharePermission](reseller.en-US/API Reference/Images/DescribeImageSharePermission.md#) to share an image.

## Next steps {#section_d22_5hm_xdb .section}

After an image is shared with other users, they can use it to create one or more instances.

1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).
2.  Create one or more instances by referring to [Step 2. Create an instance](../../../../reseller.en-US/Quick Start for Entry-Level Users/Step 2. Create an instance.md#)Create an instance in *Quick Start*. Note that you should select **Shared Image** during the procedure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9700/15394855796802_en-US.png)


They can also use the shared image to [Change the system disk \(custom image\)](reseller.en-US/User Guide/Cloud disks/Change the system disk (custom image).md#) for instances.

## Appendix. How to get the account ID {#HowToFindAccountId .section}

To query your account ID, perform the following steps:

1.  Log on to the ECS console.
2.  Move the cursor onto the upper right user avatar, such as funCustomer\*\*\*\*\*@aliyun.com. From the pop-up account menu, click **Security Settings**.
3.  On the page that appears, find the account ID.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9700/15394855796803_en-US.png)


