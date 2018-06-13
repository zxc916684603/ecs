# Spot instances {#concept_t3p_gv2_5db .concept}

Spot instances are a type of on-demand instances. They are designed to reduce your ECS costs in some cases. When you create a spot instance, you can set a maximum rate per hour for bidding a specified instance type. When your bid is higher than or equal to the current market price, your instance runs. You can hold a spot instance without interruption for at least one hour. When the market price exceeds your bid or the resource stock is insufficient, the instance is automatically released. The following figure shows the life cycle of a spot instance.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9552/5106_en-US.png)

## Scenarios {#section_fdc_jt5_ydb .section}

Spot instances are ideal for stateless applications, such as scalable Web services and applications for rendering figures, big data analysis, and massively parallel computing. Applications requiring higher level of distribution, scalability, and fault tolerance capability benefit from spot instances with respect to costs and throughput.

You can deploy the following businesses on spot instances:

-   Real-time analysis
-   Big data
-   Geological survey
-   Image coding and media coding
-   Scientific computing
-   Scalable Web sites and Web crawlers
-   Image and media coding
-   Testing

Spot instances are not suitable for stateful applications, such as databases, because it is difficult to store application states if the instance is released because of a failed bid or some other reasons.

## Bidding modes {#section_hdc_jt5_ydb .section}

The spot instance supports a one-time bid request. You can bid for a spot instance only one time in either of the following bidding modes:

-   [SpotWithPriceLimit](#SpotWithPriceLimit)
-   [SpotAsPriceGo](#SpotAsPriceGo)

**SpotWithPriceLimit**

In this mode, you must set the highest price you want to pay for a specified instance type.  When using [../../../../dita-oss-bucket/SP\_2/DNA0011860945/EN-US\_TP\_9856.md\#](../../../../intl.en-US/API Reference/Instances/RunInstances.md#) API to create a spot instance, you can bid in this mode.

Currently, the maximum bid of a spot instance is the price of a Pay-As-You-Go instance of the same configuration. When creating a spot instance, you can set a price according to the market price history, business features, and the estimated future price fluctuation. When the market price is lower than or equal to your bid, and the resource stock is sufficient, the instance continues to run. If your estimated quote is accurate, [\#valid](#valid) you can hold the instance even after one hour. Otherwise, your instance gets automatically released at any time.

**SpotAsPriceGo**

By setting `SpotStrategy` to `SpotAsPriceGo`, you can create a spot instance with the SpotAsPriceGo bidding mode, which means you always set the real-time market price as the bidding price until the instance is released because of stock shortage.

## Guaranteed duration {#valid .section}

Once a spot instance is created, it has a guaranteed duration of one hour, namely, the first hour after it is created. During this period, we do not release your instance because of stock shortage, and you can run services on the instance as usual. Beyond the guaranteed duration, we check the market price and stock every five minutes. If the market price at any given point of time is higher than your bid or the instance type stock is insufficient, we will release your spot instance.

## Price and billing {#section_mdc_jt5_ydb .section}

Spot instance price and billing considerations:

-   **Price** 

    The spot instance price applies to the instance type only, including vCPU and memory, but not to system disks, data disks, or network bandwidth. The prices for system disks and data disks are the same as for [../../../../dita-oss-bucket/SP\_2/DNA0011810291/EN-US\_TP\_9586.md\#](../../../../intl.en-US/Pricing/Pay-As-You-Go.md#) instances. The prices for network bandwidth are determined according to bandwidth billing rules of Pay-As-You-Go instances. For specific information, see  [../../../../dita-oss-bucket/SP\_2/DNA0011810291/EN-US\_TP\_9596.md\#](../../../../intl.en-US/Pricing/Billing of network bandwidth.md#).

-   **Billing cycle** 

    Spot instances are billed on an hourly basis during their life cycles. You are billed for the entire hour even if your usage is less than an hour.

-   **Billing duration** 

    Instances are billed according to the actual period of use. The actual period of use is the duration from instance creation to instance release. After an instance is released, it is no longer billed. If you stop the instance by using [../../../../dita-oss-bucket/SP\_2/DNA0011860945/EN-US\_TP\_9859.md\#](../../../../intl.en-US/API Reference/Instances/StopInstance.md#) API or on the [ECS console](../../../../intl.en-US/User Guide/Instances/Start or stop an instance.md#) , and the instance continues to charge.

-   **Market price** 

    During creation of a spot instance, it runs when your bid is higher than the current market price and the relevant demand and supply conditions are satisfied. The final price you pay for your instance type is based on the current market price.


The actual market price of a spot instance varies according to the changes in the demand and supply of a given instance type. Therefore, you can take full advantage of the price fluctuations of spot instances. If you purchase spot instance types at the right time, the computing costs are reduced but your business throughput for this period is increased.

## Quota {#section_l24_3tk_zdb .section}

For more information about the spot instance quota, see [../../../../dita-oss-bucket/SP\_2/DNA0011894323/EN-US\_TP\_9616.md\#](../../../../intl.en-US/User Guide/Limits.md#).

## Create a spot price instance {#section_pdc_jt5_ydb .section}

 You can create a spot instance by using the [../../../../dita-oss-bucket/SP\_2/DNA0011860945/EN-US\_TP\_9856.md\#](../../../../intl.en-US/API Reference/Instances/RunInstances.md#) API.

After a spot instance is created, it can be used exactly as a Pay-As-You-Go instance. You can also use it with other cloud products, such as cloud disks or EIP addresses.

## Stop a spot instance {#section_qdc_jt5_ydb .section}

You can use the [../../../../dita-oss-bucket/SP\_2/DNA0011860945/EN-US\_TP\_9859.md\#](../../../../intl.en-US/API Reference/Instances/StopInstance.md#) API or the  [ECS console](../../../../intl.en-US/User Guide/Instances/Start or stop an instance.md#) to stop a spot instance. The VPC-Connected spot instances support the [../../../../dita-oss-bucket/SP\_2/DNA0011810291/EN-US\_TP\_9595.md\#](../../../../intl.en-US/Pricing/No fees for stopped instances (VPC-Connected).md#) feature.

The network type and the bidding mode of a spot instance determine whether it can start after it is stopped, as displayed in the following table.

|Network type + Bidding mode|Stop instance|Re-start instance|
|:--------------------------|:------------|:----------------|
|VPC + SpotWithPriceLimit|Keep Instance, Fees Apply|During the guaranteed duration, the instance can be started successfully. After the guaranteed duration:-   If your bid is not lower than the market price and the resource stock is sufficient, the instance can be started successfully.
-   If your bid is lower than the market price or the resource stock is insufficient, the instance cannot be started.

|
|Classic + SpotWithPriceLimit|N/A|
|VPC + SpotAsPriceGo|Keep Instance, Fees Apply|During the guaranteed duration, the instance can be started successfully. After the guaranteed duration:-   If the resource stock is sufficient, the instance can be started successfully.
-   If the resource stock is insufficient, the instance cannot be started.

|
|Classic + SpotAsPriceGo|N/A|
|VPC + SpotWithPriceLimit|Stop Instance, No Fees|During the guaranteed duration, the instance can be started successfully only if the resource stock is sufficient.  After the guaranteed duration:-   If your bid is not lower than the market price and the resource stock is sufficient, the instance can be started successfully.
-   If your bid is lower than the market price or the resource stock is insufficient, the instance cannot be started successfully.

|
|VPC + SpotAsPriceGo|Stop Instance, No Fees|During the guaranteed duration, the instance can be started successfully only if the resource stock is sufficient. After the guaranteed duration:-   If the resource stock is sufficient, the instance can be started successfully.
-   If the resource stock is insufficient, the instance cannot be started.

|

## Release a spot instance {#section_xdc_jt5_ydb .section}

When the guaranteed period ends, we automatically release your spot instance because of changes in the market price or short resource stock. Additionally, you can independently [release the instance](../../../../intl.en-US/User Guide/Instances/Release an instance.md#).

When a spot instance is released because of market price or changes in the demand and supply of resources, the instance enters the **Pending Release** status. Then, the instance is released in about five minutes. You can use [../../../../dita-oss-bucket/SP\_2/DNA0011894323/EN-US\_TP\_9661.md\#](../../../../intl.en-US/User Guide/Instances/User-defined data and metadata/Metadata.md#) or the `OperationLocks` information returned by calling the [../../../../dita-oss-bucket/SP\_2/DNA0011860945/EN-US\_TP\_9865.md\#](../../../../intl.en-US/API Reference/Instances/DescribeInstances.md#) API to check if an instance is in the **Pending Release** status.

**Note:** Although you can check if a spot instance is in the **Pending Release** status by using the API and save a small amount of data while the instance is in this status, we recommend that you design your applications so work can be properly resumed if the spot instance is immediately released. When you release the instance manually, you can test whether or not your application functions normally if a spot instance is immediately recovered.

Generally, we release spot instance in the order of bidding price, from low to high. If multiple spot instances have the same bidding price, they are randomly released.

## Best practices {#section_zdc_jt5_ydb .section}

When using a spot instance, consider the following:

-   Set a proper bidding price. In other words, you must quote a competitive price to meet your business budget and hedge against the future market price fluctuations. By using this price, your spot instance can be created. In addition, the price must meet your expectations based on your own business assessment.

-   The image must have all the software configurations that your applications need, assuring that you can run your business immediately after the instance is created. Additionally, you can use [../../../../dita-oss-bucket/SP\_2/DNA0011894323/EN-US\_TP\_9660.md\#](../../../../intl.en-US/User Guide/Instances/User-defined data and metadata/User data.md#) to run commands at startup.

-   Store your business data on storage products that are independent from spot instances, such as cloud disks that are not set to release together with instances, OSS, or RDS.

-   Split your tasks by using grids, Hadoop, queuing-based architecture, or check points, to facilitate store computing results frequently.

-   Use the release notification to monitor the status of a spot instance. You can use [../../../../dita-oss-bucket/SP\_2/DNA0011894323/EN-US\_TP\_9661.md\#](../../../../intl.en-US/User Guide/Instances/User-defined data and metadata/Metadata.md#) to check the instance status every minute. The metadata of an instance is updated five minutes before it is released automatically.

-   Test your applications in advance, to make sure that they can handle events such as accidental release of an instance. To test the applications: Run the applications on a Pay-As-You-Go instance, release the instance, and then check how the applications can handle the release.


For more information, see [FAQ about spot instances](https://www.alibabacloud.com/help/faq-detail/48269.htm).

For more information about using APIs to create spot instances, see [Using APIs to manage spot instances](https://www.alibabacloud.com/help/zh/doc-detail/61259.htm).

