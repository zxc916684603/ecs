# Billing method comparison {#billingMethod_china .concept}

## Pricing {#section_ssd_kz2_zdb .section}

The price of an ECS instance varies according to the following:

-   Instance type, including the memory capacity and the number of CPU cores.
-   Region: The price for the same instance type varies in different regions.
-   Image: Windows images are more expensive than Linux or UNIX images for the same instance type in the same region because Microsoft charges an additional license fee for Windows images.

For more information, see [Pricing of ECS](https://www.alibabacloud.com/zh/product/ecs#pricing).

## Billing methods {#section_usd_kz2_zdb .section}

Currently, ECS instances support two billing methods:

-   Subscription: A prepaid method that allows you to use an instance only after you make the payment for it. Instance usage is billed on a monthly basis, and the billing unit is US$/month. Subscription is applicable to fixed 24/7 services, such as Web service.

-   Pay-As-You-Go: A postpaid method in which you can pay after using the instance. Instance usage is billed on a minute basis, and the billing unit is US$/hour. The minimum charge for the lifecycle of an ECS instance \(from creation to release\) is 0.01 US$. Pay-As-You-Go is applicable to scenarios with sudden traffic spikes, such as temporary scaling, interim testing, and scientific computing.


The functions and payment methods of an ECS instance vary depending on billing methods.

## Functions {#section_wsd_kz2_zdb .section}

The functions of an ECS instance vary depending on the billing method. The following table lists the differences between the Subscription and Pay-As-You-Go billing methods. You can also change a Pay-As-You-Go instance to a Subscription instance.

|Function|Subscription|Pay-As-You-Go|
|:-------|:-----------|:------------|
|Renew|Supported. You can manually renew, activate auto-renewal, or renew for downgrade for your ECS instance.|Not supported.|
|Release instances at any time|Not supported. The instance will be automatically released if it is not timely renewed after the instance expires. For more information, see Subscription.|Supported. If you do not need an instance any longer, release it Otherwise, the instance is still billed even after it is stopped until it is out of service and automatically released because of overdue payment.|
|Change instance specification|Supported. For more information, see Overview of configuration changes in the User Guide.|Supported. You can change the instance specification.|
|Upgrade bandwidth|Supported. For more information, see Overview of configuration changes in the User Guide.|Supported. For more information, see Overview of configuration changes.|
|Change billing method|Not supported.|Supported. You can switch from Pay-As-You-Go to Subscription.|
|Use prepaid image from the marketplace|Supported.|Not supported.|
|ICP Filing for instances in regions inside mainland China|Supported. An instance of which the use period is no shorter than three months can be used for filing.|Not supported.|
|Use API to create instances|Supported. Paying by credit card or PayPal bound with a credit card is not supported.|Supported.|
|Use Anti-DDoS, CloudMonitor, and SLB for free.|Supported.|Supported.|

## Payment methods {#section_ftd_kz2_zdb .section}

The payment methods of an ECS instance varies depending on different billing methods.

Currently, you can use credit cards, PayPal account, or coupons to pay for instances. Before you purchase an ECS instance, you must add a credit card or PayPal account to your account.

**Note:** 

-   For more information about the adding procedure, see [Configure your account](https://www.alibabacloud.com/help/zh/doc-detail/50517.htm) in the Account Management documentation.
-   Purchase of ECS instances in regions inside mainland China requires real-name registration. For more information about real-name registration, see [Real-name Registration for purchase of China mainland ECS](https://www.alibabacloud.com/help/zh/doc-detail/52595.htm) in the Account Management documentation.

-   The **Subscription** is a prepaid billing method. Therefore, payment by credit card, PayPal account, or coupons is supported. For more information about the billing rules, see Subscription.

    **Note:** To view the billing record for each ECS instance of the Subscription billing method, log on to the ECS Console and go to **Billing Management \>** \> **Bills \>** \> **Subscription** .

-   The **Pay-As-You-Go** billing method allows you to use instances first and pay later. Payment by credit card or coupons is supported. For more information about the billing rules, see Pay-As-You-Go.

    **Note:** To view the billing record for each ECS instance of the Pay-As-You-Go billing method, log on to the ECS Console and go to **Billing Management \>** \> **Bills \>** \> **Pay-As-You-Go** .


