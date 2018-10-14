# Manage custom images {#concept_xmy_cbt_xdb .concept}

After creating custom images, you can delete custom images that are no longer required, or modify the name and description of the custom images to help you organize and identify them.

## Modify the name and description of a custom image {#section_tdr_l33_m2b .section}

To modify the name and description of a custom image, follow these steps:

1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).
2.  In the left-side navigation pane, select **Snapshots and Images** \> **Images**.
3.  Select a region.
4.  Find the custom image to be edited.
5.  Click the ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9709/15394854887167_en-US.png) icon, and enter the image name.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9709/15394854887166_en-US.png)

6.  Click **Modify Description**, and in the dialog box, edit the new **Custom Image Description**.
7.  Click **Save** to complete the description modification.

Alternatively, you can modify the name and description of a custom image by calling the ECS API [ModifyImageAttribute](../../../../reseller.en-US/API Reference/Images/ModifyImageAttribute.md#).

## Delete custom images {#section_w3n_c43_m2b .section}

To delete one or more custom images, follow these steps:

1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).
2.  In the left-side navigation pane, select **Snapshots and Images** \> **Images**.
3.  Select a region.
4.  Select one or more custom images that you want to delete, and then click **Delete**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9709/15394854897168_en-US.png)

5.  In the dialog box that appears, select the method for deleting the custom images:

    -   **Delete**: The custom images are deleted normally.
    -   **Force Delete**: The custom images are deleted forcibly. Check **I confirm to forcibly Delete the selected instances**.

        **Note:** After you forcibly delete the custom images, [cloud disk reinitialization](reseller.en-US/User Guide/Cloud disks/Reinitialize a cloud disk.md#) of the instances that you have created from the images cannot be performed.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9709/15394854897169_en-US.png)

6.  Click **OK** to confirm.

Alternatively, you can delete custom images by calling the ECS API [DeleteImage](../../../../reseller.en-US/API Reference/Images/Deleteimage.md#).

