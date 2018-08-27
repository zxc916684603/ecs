# Create and delete an automatic snapshot policy {#concept_smh_y2l_xdb .concept}

An automatic snapshot policy is a set of defined parameters for automatically creating snapshots.

**Note:** 

-   Avoid business peak hours when you set the automatic snapshot creation time and repeated date, because creating a snapshot may slightly impact the performance of the disk.
-   You can create a maximum of 100 automatic snapshot policies in a region.

## Prerequisite {#section_odg_ffl_xdb .section}

If you want to modify an automatic snapshot policy, you must first create an automatic snapshot policy.

## Procedure {#section_pdg_ffl_xdb .section}

To create an automatic snapshot policy, follow these steps:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home).
2.  In the left-side navigation pane, select **Snapshots and Images** \> **Automatic Snapshot Policy**.
3.  On the Create Automatic Snapshot Policy page,
    -   if you want to create a policy, click **Create Policy** at the upper-right corner.
    -   if you want to modify a policy, find the policy that you want to modify, and click **Modify Policy** in the **Actions** column.
4.  In the Create Policy or Modify Policy dialog box, define an automatic snapshot policy:
    -   Define a policy name.
    -   Select a time after **Executed At** to specify the time of day for automatically creating snapshots. There are 24 time points available between 00:00 and 23:00.
    -   **Execution Frequency**: There are seven repetition days available.
    -   Set a period after **Keep Snapshots** to defines the number of days a snapshot can be retained. This parameter can be set between 1−65535 days, or permanently. By default, it is set to 30 days. You can also choose to keep automatic snapshots always.

        **Note:** When the number of snapshots reaches the limit, the system automatically removes the oldest automatic snapshots created. Manually created snapshots are not affected.

5.  Click **OK**.

## Follow-up operations {#section_udg_ffl_xdb .section}

You can [Apply automatic snapshot policies to disks](intl.en-US/User Guide/Snapshots/Apply automatic snapshot policies to disks.md#).

## Related APIs {#section_l1z_5hl_xdb .section}

-   [CreateAutoSnapshotPolicy](../../../../intl.en-US/API Reference/Snapshots/CreateAutoSnapshotPolicy.md#): Creates automatic snapshot policies.
-   [DescribeAutoSnapshotPolicyEx](../../../../intl.en-US/API Reference/Snapshots/DescribeAutoSnapshotPolicyEx.md#): Queries automatic snapshot policies.
-   [ModifyAutoSnapshotPolicyEx](../../../../intl.en-US/API Reference/Snapshots/ModifyAutoSnapshotPolicyEx.md#): Modifies automatic snapshot policies.

