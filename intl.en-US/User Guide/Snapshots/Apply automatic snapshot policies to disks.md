# Apply automatic snapshot policies to disks {#concept_nyv_k3l_xdb .concept}

You can apply an automatic snapshot policy to disks according to your business needs.

Automatic snapshots are named in the format of auto\_yyyymmdd\_1, for example, auto\_20140418\_1.

**Note:** 

-   Creating snapshots may disturb read and write operations on your disk. We recommend that you set the creation time of automatic snapshots to periods when service load is low to reduce effects on your service.
-   Automatic snapshot policies cannot be applied to basic cloud disks when they are not in use.
-   Snapshots that are manually created do not conflict with automatic snapshots. However, if an automatic snapshot is being created on a disk, you must wait for it to finish before manually creating a snapshot.

You can apply an automatic snapshot policy to a disk in two ways:

-   From the Cloud Disks menu: For applying an automatic snapshot policy to a specific disk.
-   From the Snapshots and Images menu: For applying a unified automatic snapshot policy to several or all disks.

## From the Cloud Disks menu {#section_yzf_tkl_xdb .section}

To apply an automatic snapshot policy through the Cloud Disks menu, follow these steps:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  Select a region.
3.  In the left-side navigation pane, click Cloud Disks.
4.  Select the disk for which you want to execute the policy and click Automatic Snapshot Policy.
5.  Enable the automatic snapshot function and select the desired snapshot policy.
6.  Click **OK**.

## From the Snapshots and Images menu {#section_dm4_zkl_xdb .section}

To apply or disable an automatic snapshot policy, follow these steps:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  Select a region. You can see a list of all automatic snapshot policies in the region.
3.  In the left-side navigation pane, select **Snapshots and Images** \> **Automatic Snapshot Policies**. 
4.  Select the automatic snapshot policy you want to apply and click **Apply Policy**.
5.  To enable an automatic snapshot policy, select **Disks without Policy Applied** to view the disks. Find the disk for which you want to enable the policy, and then click **Apply Policy** after it. Alternatively, after selecting multiple disks, click **Apply Policy** at the lower-left corner.

    ![](images/4563_en-US.gif)

6.  To disable the automatic snapshot policy, select the **Disks with Policy Applied** tab to view the disks. Select the disk for which you want to disable the policy, and then click **Disable Policy** after it. Alternatively, after selecting multiple disks, click **Disable Policy** at the lower-left corner.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9689/15353567844568_en-US.png)


