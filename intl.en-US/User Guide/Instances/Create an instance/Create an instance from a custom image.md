# Create an instance from a custom image {#task_w5v_sgv_xdb .task}

If you want to create an ECS instance that has the same operating system, software applications, and data as an existing instance, you can create a custom image and use it to create an ECS instance.

-   If the image and the instance are in the same region, create a custom image by using one of the following methods:
    -   [Import an image](intl.en-US/User Guide/Images/Import images/Notes for importing images.md#)
    -   [Create a custom image by using an instance](intl.en-US/User Guide/Images/Create custom image/Create a custom image by using an instance.md#)
    -   [Create a custom image by using a snapshot](intl.en-US/User Guide/Images/Create custom image/Create a custom image by using a snapshot.md#)
-   If the custom image and the instance are in different regions, copy the custom image to the target region. For more information, see [copy custom images](intl.en-US/User Guide/Images/Copy images.md#).
-   If the image to be used is owned by another account, it must be shared with you. For more information, see [share images](intl.en-US/User Guide/Images/Share images.md#).

1.   Log on to the [ECS console](https://ecs.console.aliyun.com/#/home). 
2.   In the left-side navigation pane, click **Instances**. You can also click **Images** to find the target image, and then click **Create Instance** in the **Actions** column.
3.   In the upper-right corner of the Instances page, click **Create Instance**. 
4.  Follow the instructions in [Create an instance by using the wizard](intl.en-US/User Guide/Instances/Create an instance/Create an instance by using the wizard.md#). When creating an ECS instance, note the following: 
    -   Region: Select the region where the image is located.
    -   Image: Select **Custom Image** or **Shared Image**, and then select an image from the drop-down list.

        **Note:** If the selected custom image contains more than one data disk snapshot, an equal number of cloud disks are automatically created to function as data disks. By default, the size of each data disk is equal to that of the source snapshot. You can only increase the size of a data disk. You cannot decrease it.

5.  Confirm the order. 

