# Purchase a reserved instance {#concept_wvj_gjr_dgb .task}

This topic describes how to purchase a reserved instance \(RI\).

-   Before you purchase an RI, make sure that the pay-as-you-go instances that you want to match comply with the RI limits. For more information, see the Limits section of [RI overview](reseller.en-US/Instances/Instance purchasing options/Reserved Instances/RI overview.md#section_iym_jpq_dgb).
-   You cannot manually manage the matching status between RIs and pay-as-you-go instances. Make sure that you understand the matching rules of RIs. For more information, see [Matching rules of Reserved Instances](reseller.en-US/Instances/Instance purchasing options/Reserved Instances/Matching rules of Reserved Instances.md#section_pqc_yyq_dgb).

1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).
2.  In the left-side navigation pane, choose **Instances & Images** \> **Reserved Instances**.
3.  In the top navigation bar, select a region.
4.  Click **Purchase Reserved Instance**.
5.  Set the region-related parameters. 
    1.  Set **Region**.
    2.  Set **Resource Reservation**. 

        **Note:** Only zonal RIs support resource reservation. Regional RIs apply to pay-as-you-go instances of different sizes in different zones within the same region.

    3.  Set **Zone**.
6.  Set the instance-related parameters. 
    1.  Select an **Instance type**. 

        **Note:** You must select an instance size when you purchase a regional RI. The regional RI can match any pay-as-you-go instances of the specified instance family within the specified region regardless of size.

    2.  Set **Operating System Platform**. You can select **Linux** or **Windows**.

        **Note:** The RI only matches pay-as-you-go instances that use the selected type of operation systems. The operating system type of an RI cannot be changed after you purchase it.

        To apply an RI to pay-as-you-go instances that use Bring Your Own License \(BYOL\) images, submit a ticket.

    3.  Set **Payment Option**. You can select **All Upfront**, **Partial Upfront**, or **No Upfront**. For more information, see [Payment options and billing](../reseller.en-US/Pricing/Billing of Reserved Instances.md#section_hjx_m5q_dgb).
7.  Set the purchase parameters. 
    1.  Set **Name**.
    2.  Set **Term**. You can select **1 Years** or **3 Years**.
    3.  Set **Instance Count**. The RI can match the specified number of pay-as-you-go instances of the specified instance type. For example, if the instance type is ecs.g5.large and Instance Count is set to 3, the RI can match three pay-as-you-go instances of instance type ecs.g5.large.
8.  Select *ECS Terms of Service.* Then, click **Purchase**.
9.  In the dialog box that appears, confirm that the parameter settings are correct, and click **Create Order**.
10. Confirm the payment information, and then click **Pay**.

After you purchase an RI, you can immediately apply billing discounts when the RI matches one or more pay-as-you-go instances. You can also manage RIs to meet pay-as-you-go instance changes. For more information, see [Manage Reserved Instances](reseller.en-US/Instances/Instance purchasing options/Reserved Instances/Manage Reserved Instances.md#).

