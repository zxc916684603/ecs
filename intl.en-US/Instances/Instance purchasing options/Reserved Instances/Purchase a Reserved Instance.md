# Purchase a Reserved Instance {#concept_wvj_gjr_dgb .concept}

This topic describes how to purchase a Reserved Instance \(RI\).

## Before you begin: {#section_xh1_nwj_ggb .section}

-   Before purchasing an RI, make sure that the Pay-As-You-Go instances to be matched do not exceed the [Limitations](reseller.en-US/Instances/Instance purchasing options/Reserved Instances/Reserved Instances.md#section_iym_jpq_dgb).
-   The matching status between an RI and a Pay-As-You-Go instance cannot be manually managed. We recommend that you read the [Matching rules of RIs](reseller.en-US/Instances/Instance purchasing options/Reserved Instances/Matching rules of Reserved Instances.md#section_pqc_yyq_dgb) to fully understand the matching rule requirements.

## Procedure {#section_rzw_wjr_dgb .section}

1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).
2.  In the left-side navigation pane, click **Reserved Instances**.
3.  On the Reserved Instances page, click **Buy Reserved Instance**.
4.  Set the region-related parameters.
    1.  Select a region.
    2.  Set **Resource Reservation**.

        **Note:** Only zonal RIs support resource reservation. However, regional RIs can apply to Pay-As-You-Go instances of different sizes or in different zones.

5.  Configure the RI.
    1.  Select an **Instance Type**.

        **Note:** You must select an instance size when you purchase a regional RI, but you do not need to specify the instance size for the RI to match Pay-As-You-Go instances.

    2.  Select **Upfront Type**.

        The options are **All Upfront**, **Partial Upfront**, and **No Upfront**. For more information, see [Reserved Instance billing](../reseller.en-US/Pricing/Reserved Instance billing.md#section_hjx_m5q_dgb).

6.  Set the purchase parameters.
    1.  \(Optional\) Enter a **Reserved Instance Name**.
    2.  Enter a **Reserved Instance Term**.

        The options are **1 year** and **3 years**.

    3.  Enter a **Reserved Instance Count**.

        The Reserved Instance can match the specified count of Pay-As-You-Go instances with the specified Instance Type. For example, if the Instance Type is ecs.g5.large and Reserved Instance Count is 3, the Reserved Instance can match 3 Pay-As-You-Go instances with Instance Type as ecs.g5.large.

7.  Read and confirm that you agree to the *ECS Service Level Agreement*, and then click **Buy**.
8.  In the confirmation dialog box, confirm the parameters, and then click **Create Order**.
9.  Confirm the payment information, and then click **Pay**.

## What to do next {#section_mdh_vyj_ggb .section}

After you have successfully purchased an RI, you can immediately benefit from the billing discount when the RI matches one or more Pay-As-You-Go instances. You can also [Manage Reserved Instances](reseller.en-US/Instances/Instance purchasing options/Reserved Instances/Manage Reserved Instances.md#) to quickly adjust to any changes made to your Pay-As-You-Go instances.

