# Share images {#concept_e1j_jgm_xdb .concept}

You can share your custom images with other users. Through the ECS console or ECS API, you can query images shared by other accounts with your own account, and select images shared by other accounts to create ECS instances. and replace system disk.

Before sharing an image, make sure that no confidential data is accessible on the disks to be shared.

**Note:** 

The integrity or security of images is not guaranteed. Make sure that you use only images shared by trusted accounts. Before using shared images to create ECS instances, log on to the ECS instances to which the shared images belong and verify that the images are secure and complete.

## Precautions {#section_v3m_rgm_xdb .section}

**Limits**

-   One image can be shared with a maximum of 50 accounts.
-   Shared images do not count towards your image quota.
-   Shared images can only be used to create instances in the same region as the source image.
-   Only image owners can share images with other accounts.

**Impact of deleting shared images**

-   You can delete a custom image even you have shared it with other accounts. Before deleting the shared image, however, you must unassociate it from other accounts.
-   If you delete an account that has shared a custom image, the users who are using the shared image can no longer find the image through the ECS console or ECS API, or use the image to create ECS instances and replace system disks.
-   Deleting shared custom images may cause system disk re-initialization to fail for ECS instances created from these images.

You can share your custom images with other users. Through the ECS console or ECS API, you can query images shared by other accounts with your own account, and select images shared by other accounts to create ECS instances and replace system disk..

## Procedure {#section_tsh_dhm_xdb .section}

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/). In the left-side navigation pane, click Images. Select a region. Select the Custom Image you want to share. Click **Share Image**.

    ![](images/4609_en-US.png)

2.  In the displayed dialog box, select the Account Type and enter the account ID you want to share the image with. To obtain the account ID, logg on to Security Settings

    ![](images/4610_en-US.png)

3.  of the Alibaba Cloud console and click**Account Management** \> **Security Settings** \> **Account ID**.

    ![](images/4611_en-US.jpg)

4.  View accounts using your shared images.

    ![](images/4612_en-US.jpg)


## Creating ECs instances using shared mirrors {#section_d22_5hm_xdb .section}

**Note:** 

The integrity or security of images is not guaranteed. Make sure that you use only images shared by trusted accounts. If you delete an account that has shared a custom image, the users who are using the shared image can no longer find the image through the ECS console or ECS API, or use the image to create ECS instances.

![](images/4616_en-US.jpg)

## Cancel the sharing of an image {#section_hq5_33m_xdb .section}

You can cancel the sharing of an image to specific accounts at any time. After you cancel the sharing, the user is unable to query and use the image.

**Note:** 

Any instances using the image, including instances of other accounts using the shared image, will not be able to reinitialize the system disk.

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  Select a region.
3.  In the left-side navigation pane, click **Images**. Select the
4.  image you want to cancel sharing. The image type must be Custom Image. Click **Share Image**.
5.  A list of the accounts using the selected image is displayed.  Click **Unshare** next to the account with which you want to stop sharing the image.

## View the shared images {#section_l5k_q3m_xdb .section}

You can view which accounts are using your shared images. To view accounts using your shared images, perform the following:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  Select a region.
3.  In the left-side navigation pane, click **Images**. You can see the list of images.
4.  Click Images, you can see the list of images.
5.  select image you want to vie. The image type must be **Custom Image**. Click Click **Share Image**.
6.  A list of the accounts using the selected image is displayed.

## View the shared images you are using {#section_wcq_v3m_xdb .section}

You can view a list of the shared images from other accounts that you are using. To view a list of the shared images you are using, perform the following:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  Select a region.
3.  In the image type dropdown, select the **Image Type**. as **Shared Image**, A list of the shared images you are using will be displayed.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9700/4618_en-US.png)


