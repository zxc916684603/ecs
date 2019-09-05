# Purchase reserved instances {#concept_wvj_gjr_dgb .task}

This topic describes how to purchase reserved instances in the ECS console.

-   Before purchasing reserved instances, make sure that the pay-as-you-go instances you want to match meet requirements to apply reserved instances. For more information, see [Reserved instance overview](reseller.en-US/Instances/Instance purchasing options/Reserved Instances/Reserved instance overview.md#section_iym_jpq_dgb).
-   You cannot manually manage how reserved instances and pay-as-you-go instances are matched. Ensure that you understand the matching rules for reserved instances. For more information, see [Matching rules of RIs](reseller.en-US/Instances/Instance purchasing options/Reserved Instances/Matching rules of Reserved Instances.md#section_pqc_yyq_dgb).

1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs).
2.  In the left-side navigation pane, choose **Instances & Images** \> **Reserved Instances**.
3.  In the top navigation bar, select a region.
4.  Click **Purchase Reserved Instance**.
5.  Configure region-related parameters. 
    1.  Set **Region**.
    2.  Set **Resource Reservation** to Reserved or Not Reserved. 

        **Note:** You can only set Resource Reservation to Reserved for zonal reserved instances. Regional reserved instances can be applied to pay-as-you-go instances in different zones within the same region.

    3.  Set **Zone**.
6.  Configure instance-related parameters. 
    1.  Set **Instance Type**. 

        **Note:** You must select an instance size when you purchase a regional reserved instance. However, the regional reserved instance can match any pay-as-you-go instances of the specified instance family within the specified region regardless of size.

    2.  Set **Operating System Platform**. **Linux** and **Windows** operating systems are available.

        **Note:** A reserved instance only matches pay-as-you-go instances that use the selected operating system type. You cannot change the operating system type of a reserved instance after you purchase it.

        To apply a reserved instance to pay-as-you-go instances created from Bring Your Own License \(BYOL\) images, you must submit a ticket.

    3.  Set **Payment Option**. **All Upfront**, **Partial Upfront**, and **No Upfront** are available. For more information, see [Reserved instance billing](../reseller.en-US/Pricing/Billing of Reserved Instances.md#section_hjx_m5q_dgb).
7.  Configure purchase parameters. 
    1.  Set **Name**.
    2.  Set **Term**. **1 Year** and **3 Years** are available.
    3.  Set **Instance Count**. A reserved instance can match the specified number of pay-as-you-go instances of the specified instance type. For example, if the instance type is ecs.g5.large and Instance Count is set to 3, the reserved instance can match three pay-as-you-go instances of the ecs.g5.large instance type.
8.  Select *ECS Terms of Service* . Click **Purchase**.
9.  In the dialog box that appears, confirm the parameters and click **Create Order**.
10. Confirm the payment information and click **Pay**.

After you purchase a reserved instance, discounts will be applied when the reserved instance matches one or more pay-as-you-go instances. You can also manage reserved instances to cope with configuration changes of pay-as-you-go instances. For more information, see [Manage Reserved Instances](reseller.en-US/Instances/Instance purchasing options/Reserved Instances/Manage Reserved Instances.md#).

