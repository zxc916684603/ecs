# Pricing overview {#concept_isb_scd_5db .concept}

## Pricing {#section_lzm_rq2_zdb .section}

For the price information, see the Pricing page.

## Chargeable resources {#section_zpf_wr2_zdb .section}

The price of an ECS instance depends on the following resources:

-   Instance types, images, and cloud disks: The price of these resources vary according to the billing method you select. For more information, see [Billing method comparison](reseller.en-US/Pricing/Billing method comparison.md#).

    -   Instance types: The instance type determines the number of vCPU cores and the size of memory.

    -   Images:

        -   Public images: Charges apply only for Windows OS images and Red Hat images. Linux or Unix-like OS images are free of charge.
        -   Marketplace images: The price is determined by the image supplier.
        -   Shared images or custom images: If they are created by using marketplace images, the price is determined by the image provider.
    -   Cloud disks: Disks created together with an ECS instance have the same billing method as the ECS instance. Disks created separately are billed according to the [Pay-As-You-Go](reseller.en-US/Pricing/Pay-As-You-Go.md#) billing method. For a Pay-As-You-Go cloud disk, after an ECS instance is created, you can [change the instance billing method from Pay-As-You-Go to Subscription](reseller.en-US/Pricing/Limits.md#) in the ECS console. Alternatively, you can [upgrade the Pay-As-You-Go instance configurations](../../../../reseller.en-US/User Guide/Instances/Change configurations/Upgrade configurations of Subscription instances.md#) to change the billing method.

-   Public network bandwidth: If a public IP address is assigned to your ECS instance when you create or upgrade it, you must pay for public network bandwidth. For more information, see [Billing of network bandwidth](reseller.en-US/Pricing/Billing of network bandwidth.md#).

    **Note:** VPC-Connected ECS instances can access the Internet by binding an EIP address to them. For more information, see [Billing of EIP](https://partners-intl.aliyun.com/help/doc-detail/27767.htm).

-   Snapshots: Snapshots are free of charge.


