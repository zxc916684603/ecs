# Create snapshots {#concept_eps_gbl_xdb .concept}

You can create instance snapshots to save the system state from a certain point in time for data backup or to create images.

**Note:** 

-   Starting in March 28, 2017, the snapshot service starts charging fees. For more information on Snapshot charges, see the snapshot commercialization FAQ.
-   Avoid business peaks. Creating snapshots of a disk may reduce disk performance.
-   The instance must in the **Running** or **Stopped** status.
-   Manually created snapshots, unlike automatic snapshots, will be retained until they are manually deleted. unlike automatic snapshots, will be retained until they are [manually deleted](intl.en-US/User Guide/Snapshots/Delete snapshots or automatic snapshot policies.md#).
-   During snapshot creation, operation performed on the disk does not affect the data intergrety in the snapshot. Because the snapshot backs up the data from the moment you create the snapshot, instead of creating data for the entire time period of the snapshot process.

## Procedures {#section_pdn_xdl_xdb .section}

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  Select a region. In the left-side navigation pane, click Instances, and click **Manage**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9687/4545_en-US.png)

3.  In the left-side navigation pane, click  **Instance Disks**.  And click **Create Snapshot** for the target disk. You can select only one disk at a time, either system disk or data disk.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9687/4530_en-US.png)

4.  Enter the name for the snapshot, click, **OK**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9687/4550_en-US.png)

5.  To view the snapshots, go to left-side navigation pane and click **Instance Snapshots**. You can see the progress and status of the snapshot.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9687/4552_en-US.png)


## Time required for each snapshot creation may vary because of the {#section_gvs_ydl_xdb .section}

-   disk volume.
-   Creation of the first snapshot will take relatively longer than subsequent snapshots due to the first snapshot being a full snapshot.
-   However, depending on the amount of changed data since previous snapshots, the length of time for each snapshot creation varies.

