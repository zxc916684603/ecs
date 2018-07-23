# Pay-As-You-Go {#Pay-As-You-Go .concept}

Pay-As-You-Go is a billing method that Alibaba Cloud uses to charge based on the amount of actually used resources. Pay-As-You-Go allows you to activate and release resources at any time and you can purchase resources on demand without buying too many devices. This can reduce the cost for up to 30% to 80% as compared with the traditional host investment.

## Applicable resources {#section_xmc_xbg_c2b .section}

Currently, the Pay-As-You-Go billing method is applicable to the following ECS resources:

-   ECS instances, including CPU configuration and memory capacity
-   Images
-   System disks and/or data disks

If you create an ECS instance of the Pay-As-You-Go billing method, the **Instance Cost** displayed in the bottom of the instance creation page is the total fee of the preceding three types of resources.

Before activating resources of the Pay-As-You-Go billing method, you must know the following:

-   Resource configuration change:

    You can change the instance types, including CPU configuration and memory capacity, after you create an instance. For more information, see [Change configurations of Pay-As-You-Go instances](../../../../intl.en-US/User Guide/Instances/Change configurations/Change configurations of Pay-As-You-Go instances.md#).

-   Billing method change:

    Instances, system disks, and data disks support switching from Pay-As-You-Go to Subscription. For more information about the procedure, see [Switch from Pay-As-You-Go to subscription](intl.en-US/Pricing/Switch from Pay-As-You-Go to subscription.md#).


## Payment methods {#section_igl_wcg_c2b .section}

You can use a credit card or a PayPal account to pay for resources of the Pay-As-You-Go billing method. You must link them to your account. For more information, see [Add a payment method](https://www.alibabacloud.com/help/doc-detail/50517.htm).

**Note:** If you are using PayPal as the payment method after activating a Pay-As-You-Go resource and place an order, Alibaba Cloud preauthorizes on your PayPal account.

## Billing cycle {#section_rbk_ldg_c2b .section}

A Pay-As-You-Go resource is billed by the second after is it created and stops billing after it is released. However, you can enable the [no fees for stopped instances feature](intl.en-US/Pricing/No fees for stopped instances (VPC-Connected).md#) for a VPC instance. After the feature is enabled, a VPC instance is billed by second after it is created, stops billing when it is in the **Stopped** status, and starts billing again when it starts again. Except for instances, this feature does not apply to other ECS resources.

The billing cycle varies depending on the resource types. The minimum charge for the lifecycle of an ECS instance \(from creation to release\) is USD 0.01.

|Item|Instances + Images|System disks|Data disks|
|:---|:-----------------|:-----------|:---------|
|Billing cycle|One second|One second|One second|
|Price unit|USD/hour|USD/\(GiB \* hours\)|USD/\(GiB \* hours\)|

## Settlement cycle {#section_ipb_4x2_zdb .section}

Pay-As-You-Go resources are billed by second, but settled by hour. For settlement, you must know the following information:

-   Payments for resources of the Pay-As-You-Go billing method are settled together with other products under your account that are billed after you use them.

-   Generally, if the cumulative monthly consumption amount of your account is less than 1,000 USD, fees are deducted on the first day of the following month.

-   If you have a quota agreement with Alibaba Cloud, fees are deducted when the cumulative consumption amount of your account exceeds the quota.

|Cumulative consumption amount|Due date \(T\)|Fee deduction day|Description|
|-----------------------------|--------------|-----------------|-----------|
|Cumulative monthly consumption amount less than 1,000 USD.|The first day of the following month.|T, T+7, and T+14| -   In the event of deduction failure on the due date \(T\), fees are deducted again on the day T+7 and the day T+14.
-   If fee deduction fails three times, the instance is out of service on the day T+15. In this case, the instance stops running but data is retained. Billing stops when the instance is out of service.
-   When your instance is out of service, you must **open a ticket to clear the overdue payment**. After the overdue payment is cleared, you must [reactivate the instance](../../../../intl.en-US/User Guide/Instances/Reactivate an instance.md#) before the day T+30. Otherwise, the instance is released automatically.
-   If the overdue payment fails to be cleared before the day T+30, the instance is released and data cannot be recovered.
 |
|Agreed quota|On the day when the quota is exceeded|

-   Example: The following flowchart shows the settlement cycle for a Pay-As-You-Go ECS instance. Assume that the due date is March 1.

    ![](http://docs-aliyun.cn-hangzhou.oss.aliyun-inc.com/assets/pic/40653/intl_en/1501834924317/PayAsYouGo_SettlementCycle.png)


## Instructions of settlement {#section_mwz_qx2_zdb .section}

-   **Settlement period**: Fees are settled based on the actual active duration of the ECS resources.

    -   For ECS instances: The actual active duration is the time during which the ECS instance runs properly, starting from when the ECS instance is activated to when it is released or expires. If the instance is out of service during the active duration due to overdue payment, billing stops until the payment is cleared.
    -   For system disks and/or data disks: The actual active duration is the time during which the disks run properly, starting from when the disks are activated to when they are released.
-   **Release rules**

    -   If payment for an ECS instance is overdue, usage of Pay-As-You-Go cloud disks is restricted, and the cloud disks cannot process I/O read and write requests properly, affecting the normal running of the ECS instance. The impact includes but is not limited to the reduced performance of application read/write, serious time-out of some operations, and power-off or restart failure for some operating system versions.
    -   ECS instances configured with the automatic release time are automatically released at a specified time.
    -   Notification of release: In the event of service expiration or overdue payment, the system notifies you by email.

## Resources status during out of service {#section_rpb_4x2_zdb .section}

If you fail to pay for the Pay-As-You-Go resources fees three times in one settlement period, the instance is out of service on the day T+15. When your instance is out of service, you cannot use the resources normally until you the overdue payment. Once the payment is cleared, you must [reactivate the instance](../../../../intl.en-US/User Guide/Instances/Reactivate an instance.md#) within the specified period. The following table lists the status of the related resources when the instance is out of service.

|Period|ECS instance and image|System disk + data disks|Internet IP address|Snapshots|
|:-----|:---------------------|:-----------------------|:------------------|:--------|
|Within 15 days|Both stop working.|When the instance is out of service\*, the capability of the cloud disks and the local disks is limited. But the data on them is retained.| -   For instances of the Classic network type: The assigned Internet IP address is retained.
-   For VPC instances: If an Internet IP address is assigned, it is retained. If an elastic IP \(EIP\) address is bound to the instance, it is retained.

 |Retained.|
|15 days later|Released automatically. You are notified in advance by emails when the resources will be released.| All cloud disks, including system disks and data disks that are created separately or together with the instance, or that are attached to the instance or not, are released automatically. The data cannot be recovered.

 The local disks are released automatically, and the data on them cannot be recovered.

 If shared block storage is attached to the instance, it is detached automatically, and the data on it is retained.

 | For instances of the Classic network type: The assigned Internet IP address is released.

 For VPC instances: If an Internet IP address is assigned, it is released. If an EIP address is bound to the instance, it is unbound automatically.

 |The automatic snapshots are deleted automatically. The snapshots that are manually created are retained.|

\* When a Pay-As-You-Go instance is **out of service**, the instance is in the **Expired**status, and it stops working because of overdue payment. During the period of out of service, no fees are incurred.

## FAQs {#section_utf_tx2_zdb .section}

**When Pay-As-You-Go ECS instances are out of service or stop running, are the fees incurred?**

An instance stops working and is rendered out-of-service when a payment is overdue. When a Pay-As-You-Go instance is out of service, it is in the **Expired** status, and no fees are incurred.

A stopped instance means an instance that is in the Stopped status and has been stopped by [the action in the ECS console](../../../../intl.en-US/User Guide/Instances/Start or stop an instance.md#) or by using the [StopInstance](../../../../intl.en-US/API Reference/Instances/StopInstance.md#) interface. Billing of a stopped instance varies by the network type of the instance:

-   VPC: You can enable the [No fees for stopped instances](intl.en-US/Pricing/No fees for stopped instances (VPC-Connected).md#) feature. When this feature is enabled, an instance stops billing when it is in the **Stopped** status and starts billing again when it is started. Except for ECS instances, this feature does not apply to other resources.

-   Classic: An instance continues to be billed even after it is in the **Stopped** status.


