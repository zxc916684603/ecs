# Pricing overview {#concept_isb_scd_5db .concept}

## Pricing {#section_lzm_rq2_zdb .section}

For the price information, see the [Pricing](https://www.alibabacloud.com/product/ecs) page.

## Chargeable resources {#section_zpf_wr2_zdb .section}

When you create an ECS instance, the following resources determine its price:

-   Instance types, images, and cloud disks: Their prices vary according to their billing methods, including [Subscription](intl.en-US/Pricing/Subscription.md#) and [Pay-As-You-Go](intl.en-US/Pricing/Pay-As-You-Go.md#). For more information, see [Billing method comparison](intl.en-US/Pricing/Billing method comparison.md#).

    -   Instance types: Including the number of vCPU cores and the size of memory.

    -   Images:

        -   Public images: Only Windows OS images are charged. Linux or Unix-like OS images are free of charge.
        -   Marketplace images: The price is determined by their suppliers.
        -   Shared images or custom images: If they are created by using marketplace images, the price is determined by the image provider.
    -   Cloud disks: The disks created together with an ECS instance have the same billing method with the ECS instance. The separately created disks are billed according to [Pay-As-You-Go](intl.en-US/Pricing/Pay-As-You-Go.md#) billing method. For a Pay-As-You-Go cloud disk, after an ECS instance is created, you can [convert its billing method from Pay-As-You-Go to Subscription](intl.en-US/Pricing/Switch from Pay-As-You-Go to subscription.md#) or [upgrade configurations of a Subscription instance](../../../../intl.en-US/User Guide/Instances/Change configurations/Upgrade configurations of Subscription instances.md#)  to convert its billing method, to synchronize its lifecycle with the instance.

-   Public network bandwidth: If a public IP address is assigned to your ECS instance when you create or upgrade it, you must pay for the public network bandwidth. For more information, see [Billing of network bandwidth](intl.en-US/Pricing/Billing of network bandwidth.md#).

    **Note:** VPC-Connected ECS instances can access Internet by binding an EIP address. For more information, see [Billing of EIP](https://www.alibabacloud.com/help/doc-detail/72142.htm).

-   Snapshot: Currently snapshots are free of charge.


