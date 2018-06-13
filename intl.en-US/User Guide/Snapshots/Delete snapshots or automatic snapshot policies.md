# Delete snapshots or automatic snapshot policies {#concept_ch5_2pl_xdb .concept}

When you no longer need a snapshot, or you have reached your snapshot quota, you can delete snapshots to free up space.

**Note:** 

-   Deleting a snapshot is a permanent action and cannot be reversed. Once deletion is completed, the original snapshot cannot be restored.  So proceed with caution.
-   If a snapshot has been used to create a custom image, you must delete the associated image before you can delete the snapshot.

## Delete snapshots {#section_dkx_mpl_xdb .section}

1.  Log on to the [Container Service console](https://ecs.console.aliyun.com/#/home).
2.  Click in the left navigation **Snapshots & Images** \> **Snapshot list** . Select a region.
3.  you want to delete.
4.  Click Delete at the bottom of the window. Click **OK**.

## Delete snapshot policies {#section_ws4_mql_xdb .section}

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  Click in the left navigation **Snapshots & mirrors** \> **Automatic Snapshot Policy** . Then, select a region to view all snapshots in this region.
3.  Find the target automatic snapshot policy, and in the Action column, click **Delete Automatic Snapshot Policy**.
4.  In the dialog box, confirm information and click **OK**.

