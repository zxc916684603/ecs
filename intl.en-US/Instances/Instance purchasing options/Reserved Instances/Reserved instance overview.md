# Reserved instance overview {#concept_tc4_zhq_dgb .concept}

A reserved instance is a discount coupon that can be applied automatically to one or more pay-as-you-go instances that belong to your account, excluding preemptible instances. A reserved instance also can be used to reserve instance resources. A combination of reserved instances and pay-as-you-go instances is more flexible and cost effective than subscription instances.

## Comparison between reserved instances, pay-as-you-go instances and subscription instances {#section_qv2_nlq_dgb .section}

The following table lists differences between reserved instances, pay-as-you-go instances and subscription instances.

|Item|Reserved instance|Pay-as-you-go instance|Subscription instance|
|----|-----------------|----------------------|---------------------|
|Form|A discount coupon.|An instance using the [Pay-As-You-Go](../../../../reseller.en-US/Pricing/Pay-As-You-Go.md#) billing method, equivalent to a virtual machine.|An instance using the [Subscription](../../../../reseller.en-US/Pricing/Subscription.md#) billing method, equivalent to a virtual machine.|
|Purpose|Reserved instances cannot be used independently. They must match pay-as-you-go instances to generate a discount.|Pay-as-you-go instances can be managed independently. They can be used as simple Web servers, or used in combination with other Alibaba Cloud services to deliver powerful solutions.|Subscription instances can be managed independently. They can be used as simple Web servers, or used in combination with other Alibaba Cloud services to deliver powerful solutions.|

## Payment options, terms, and instance count {#section_mrf_33q_dgb .section}

When purchasing a reserved instance, you can specify the payment option, term, and count based on your budget.

-   Three payment options are available:

    All Upfront, Partial Upfront, and No Upfront. For more information, see [Reserved instance billing](../../../../reseller.en-US/Pricing/Billing of Reserved Instances.md#).

    **Note:** Whether you can use the No Upfront payment option depends on your ECS instance resource usage.

-   Reserved instances come in the following terms:

    1 year and 3 years.

    **Note:** After a reserved instance expires, the corresponding pay-as-you-go instances still run normally, but they will be billed without a discount.

-   Instance count:

    The number of pay-as-you-go instances that a reserved instance can match at the same time.


## Reserved instance attributes {#section_b3l_w3q_dgb .section}

A reserved instance has specific attributes that allow it to automatically match corresponding pay-as-you-go instances. You can also split a reserved instance, merge multiple reserved instances, or change the scope of a reserved instance to better match pay-as-you-go instances. These attributes include:

-   Operating system: Reserved instances can match pay-as-you-go instances running the Linux and Windows operating systems.

    **Note:** Windows reserved instances can be used to pay for image bills of pay-as-you-go instances.

-   Instance type: the type of a reserved instance, which includes the instance family and instance size. A reserved instance can match pay-as-you-go instances of the same type.
-   Scope: the matching scope of a reserved instance. In terms of matching scope, reserved instances are classified into regional reserved instances and zonal reserved instances.

    **Note:** We recommend that you purchase both zonal and regional reserved instances. Choose zonal reserved instances when you are very sure about in which zones you want to use them. Otherwise, choose regional reserved instances to meet uncertain requirements.

-   Computing power: the maximum computing resources that a reserved instance can match. The computing power is determined jointly by the instance type and instance count.

## Limits {#section_iym_jpq_dgb .section}

Reserved instances have the following limits:

-   Maximum number of reserved instances

    -   Maximum number of regional reserved instances: Each account can have up to 20 regional reserved instances in all regions.
    -   Maximum number of zonal reserved instances: Each account can have up to 20 zonal reserved instances in each zone.
    For example, you can purchase 10 regional reserved instances in China \(Hangzhou\) and 10 regional reserved instances China \(Qingdao\), but the total number of regional reserved instances cannot exceed 20. You can purchase 20 zonal reserved instances in Zone B of China \(Hangzhou\) and 20 zonal reserved instances Zone H of China \(Hangzhou\). If you need more reserved instances, you can submit a ticket.

-   Instance categories

    Reserved instances can only match pay-as-you-go instances, excluding [preemptible instances](../../../../reseller.en-US/Instances/Instance purchasing options/Preemptible instances/Preemptible instances.md#).

-   Instance families

    Reserved instances support the following instance families: sn1ne, sn2ne, se1ne, ic5, c5, g5, r5, c6, g6, r6, i2, i2g, hfc5, hfg5, and t5. [Burstable instances \(t5\)](../../../../reseller.en-US/Instances/Instance type families/Burstable performance instances/Overview.md#) can only match zonal reserved instances. They cannot match regional reserved instances. Reserved instances that match burstable instances cannot be merged, split, or have their matching scope changed.


## Billing {#section_icr_mpc_dhb .section}

For more information, see [Reserved instance billing](../../../../reseller.en-US/Pricing/Billing of Reserved Instances.md#).

## Related topics {#section_aj4_hc2_ggb .section}

For more information about matching rules of reserved instances, see [Matching rules of reserved instances](../../../../reseller.en-US/Instances/Instance purchasing options/Reserved Instances/Matching rules of Reserved Instances.md#).

For more information about how to purchase reserved instances, see [Purchase reserved instances](reseller.en-US/Instances/Instance purchasing options/Reserved Instances/Purchase reserved instances.md#).

For more information about how to manage reserved instances, see [Manage reserved instances](reseller.en-US/Instances/Instance purchasing options/Reserved Instances/Manage Reserved Instances.md#).

For more information about how to call an API operation to purchase reserved instances, see [PurchaseReservedInstancesOffering](reseller.en-US/API Reference/Reserved Instances/PurchaseReservedInstancesOffering.md#).

For more information about how to call an API operation to query reserved instances, see [DescribeReservedInstances](reseller.en-US/API Reference/Reserved Instances/DescribeReservedInstances.md#).

For more information about how to call an API operation to manage reserved instances, see [ModifyReservedInstances](reseller.en-US/API Reference/Reserved Instances/ModifyReservedInstances.md#).

For more information about reserved instance FAQ, see [Instance FAQ](reseller.en-US/Instances/Instance FAQ.md#).

