# Manage custom images {#concept_xmy_cbt_xdb .concept}

After creating custom images, you can delete custom images that are no longer required, or modify the name and description of the custom images to help you organize and identify them.

## Modify the name and description of a custom image {#section_tdr_l33_m2b .section}

To modify the name and description of a custom image in the ECS console:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  In the left-side navigation pane, select **Snapshots & Images** \> **Images**.
3.  Select a region.
4.  Locate the ****custom image that needs to be edited.
5.  Tap the ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9709/7167_en-US.png) icon, and enter the image name.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9709/7166_en-US.png)

6.  Click **Modify Image Description**, in the prompted dialog box:
    -   **Image Description**: Edit the new image description.
    -   \(Optional\) **Tag**: Assign tags to the custom image and add your own metadata in the form of tags.
7.  Click **Save** to complete the description modification.

Alternatively, you can modify the name and description of a custom image by calling the ECS API [ModifyImageAttribute](../../../../intl.en-US/API Reference/Images/ModifyImageAttribute.md#).

## Delete custom images {#section_w3n_c43_m2b .section}

To delete one or more custom images in the ECS console:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  In the left-side navigation pane, select **Snapshots & Images** \> **Images**.
3.  Select a region.
4.  Select one or more ****custom images that you want to delete, then click **Delete**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9709/7168_en-US.png)

5.  In the dialog box that appears, select the method for deleting the custom images:

    -   **Delete**: The custom images are deleted normally.
    -   **Force Delete**: The custom images are force deleted, then select **Sure to force Delete** to confirm.

        **Note:** After you force delete the custom images, instances that you have created from the images cannot be [Reinitialize a cloud disk](intl.en-US/User Guide/Cloud disks/Reinitialize a cloud disk.md#).

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9709/7169_en-US.png)

6.  Click **OK** to confirm.

Alternatively, you can delete custom images by calling the ECS API [DeleteImage](../../../../intl.en-US/API Reference/Images/Deleteimage.md#).

