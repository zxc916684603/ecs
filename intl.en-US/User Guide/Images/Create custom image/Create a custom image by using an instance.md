# Create a custom image by using an instance {#concept_ech_5bm_xdb .concept}

You can create a custom image using an ECS instance, namely, you fully copy all its disks and pack them into an image.

During this process, snapshots are automatically created for all disks of the instance, including the system disk and data disks. All the created snapshots compose a new custom image. See the following picture.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9697/4599_en-US.png)

In addition, you can create a custom image based on the snapshot. See [Create a custom mirror using a snapshot](intl.en-US/User Guide/Images/Create custom image/Create a custom mirror using a snapshot.md#).

## Prerequisites {#section_yw3_zbm_xdb .section}

-   To prevent the data privacy breach, make sure you delete all the confidential data in the ECS instance before creating a custom image.
-   During creation, do not change the status of the instance. Do not stop, start, or restart the instance.
-   If your custom image contains the data on the data disk, new data disk along with the ECS instance are created together. The data on the data disk duplicates the data disk snapshot in your custom image according to the mount device.
-   You can export custom images that contain data of data disks.
-   You cannot use a custom image which contains the data on the data disk to replace the system disk.

## Procedure {#section_ojf_2cm_xdb .section}

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/).
2.  At the top of the Instance list page, select the region where the target instance is located.
3.  Click **Instances** on the left-side navigation pane.
4.  Find the required instance. Choose  **More** \> ** Create Custom Image**.
5.  Enter the name and description.
6.  Click **create**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9697/4601_en-US.png)


The image is available after all snapshots of all disks have been created. Please be patient.

## Follow-up operation {#section_rwd_lcm_xdb .section}

After creating the custom image, you may want to [Create an instance from a custom image](intl.en-US/User Guide/Instances/Create an instance/Create an instance from a custom image.md#).

