# Manage Reserved Instances {#concept_kc4_cnr_dgb .concept}

This topic describes how to split, merge, and modify the scope of your Reserved Instances \(RIs\). Such actions allow you to continue to benefit from billing discounts when service scenarios require you to change your Pay-As-You-Go instances.

## Before you begin: {#section_b5n_pnr_dgb .section}

To make this topic easier to understand, RIs to be split, merged, or modified are hereinafter referred to as original RIs, while split, merged, or modified RIs are hereinafter referred to as target RIs.

Before you split, merge, or modify RIs, make sure that the following conditions are met:

-   You have successfully purchased original RIs and they are within a valid term.
-   There is no ongoing splitting, merging, or modification request.
-   The RI to be modified only requires its size to be adjusted. The instance type family of an RI cannot be modified.

After you submit a splitting, merging, or modification request:

-   The original RI changes to changing status, which will be automatically refreshed after the request is processed.
-   A request in progress cannot be changed or cancelled. If you want to roll back your changes, you must submit another request.

After an RI is split, merged, or modified:

-   The target RI becomes valid immediately. If it matches one or more new Pay-As-You-Go instances, the billing discount is applied within the same hour.
-   The original RI becomes invalid immediately. The price is updated to 0 USD.
-   If the target RI is a zonal RI, the type of resource reservation is also updated automatically.

If the original RI fails to be split, merged, or modified, it will remain valid.

## Split an RI {#section_zcd_vnr_dgb .section}

You can split an RI into multiple RIs of less computing power. The smaller RIs can then match applicable Pay-As-You-Go instances to better distribute your service traffic.

1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).
2.  In the left-side navigation pane, click **Reserved Instances**.
3.  On the Reserved Instances page, click **Split** in the **Actions** column of the original RI.
4.  On the Split Reserved Instance page, set the name, instance type, and quantity of the target RIs.

    **Note:** The total computing power of the target RIs must be equal to that of the original RI.

5.  Click **OK**.

## Merge RIs {#section_xsk_fpr_dgb .section}

If traffic to your instances increases, you can merge multiple RIs into one RI that has greater computing power to match larger Pay-As-You-Go instances.

**Note:** Before merging RIs, you must verify that the following conditions are met:

-   The expiration date of the original RIs must be the same.
-   The original RIs have been purchased using the same currency.
-   If the original RIs are regional RIs, they must be in the same area. If the original RIs are zonal RIs, they must be in the same zone.

1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).
2.  In the left-side navigation pane, click **Reserved Instances**.
3.  On the Reserved Instances page, click **Merge** in the **Actions** column of the original RI.
4.  On the Merge Reserved Instances page, select the original RIs, and then set the name, instance type, and quantity of the target RI.

    **Note:** The computing power of the target RI must be equal to that of all selected original RIs, and the target RI must be of an existing instance type. For example, two ecs.g5.2xlarge RIs can be merged into one ecs.g5.4xlarge RI, but one ecs.g5.xlarge RI and two ecs.g5.2xlarge RIs cannot be merged into one ecs.g5.5xlarge RI.

5.  Click **OK**.

## Modify the scope of an RI {#section_rrd_ppr_dgb .section}

If your service requirements change, you can modify the scope of your RIs. Specifically, you can modify a regional RI to a zonal RI, modify a zonal RI to a regional RI, or modify the zone of an RI in the same region.

1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).
2.  In the left-side navigation pane, click **Reserved Instances**.
3.  On the Reserved Instances page, click **Modify** in the **Actions** column of the original RI.
4.  On the Modify Reserved Instance Page, modify the parameters as needed.
5.  Click **OK**.

