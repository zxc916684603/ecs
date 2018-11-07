# ModifyInstanceChargeType {#ModifyInstanceChargeType .reference}

Changes the billing method for one or more instances. You can use this interface to change the billing method between Pay-As-You-Go and Subscription. Additionally, you can change all Pay-As-You-Go cloud disks that are mounted to an instance to Subscription ones.

## Description {#Description .section}

When you call this interface, consider the following:

-   You can change the billing method only when the target instance is in the **Running** \(indicated by `Running`\) or **Stopped** \(indicated by `Stopped`\) state and the balance of your payment method is sufficient.

-   By default, the system uses the latest billing method to automatically charge fees. Make sure that your account balance is sufficient. Otherwise, the system regards your order as an exception, and you have to cancel this order. If your account balance is insufficient, set `AutoPay` to `false`. The system then generates a normal unpaid order for the outstanding payment. You can log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs) to pay for this order.

**From Subscription to Pay-As-You-Go**

-   Alibaba Cloud users who reach a certain credit level can change the billing method from Subscription to Pay-As-You-Go.

-   After you change the billing method from Subscription to Pay-As-You-Go, the new billing method will be effective throughout the whole instance life cycle, and you will receive a refund of the instance price difference. The refund will be returned to your original payment channel, but the used vouchers will not be returned.

-   **Refund rule**: You can only freely use a certain amount of refund within a month, and the refund that is not used within the current month will not be accumulated to the next month. After you have used up the refund amount for this month, you can only change the billing method when the next month arrives. The refund amount consumed for a billing method change is calculated by either of the following formulas: **Number of vCPUs x \(Number of remaining days within the instance's life cycle excluding the day when the billing method is changed x 24 + Number of remaining hours on the day when the billing method is changed\) or Number of vCPUs x \(Number of remaining days within the instance's life cycle including the day when the billing method is changed x 24 - Number of elapsed hours on the day when the billing method is changed\)**. The following figure illustrates the refund consuming rule by taking the network-enhanced instance type ecs.sn1ne.xlarge \(with 4 vCPUs\) for example.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9878/154157764212954_en-US.png)


**From Pay-As-You-Go to Subscription**

-   You can change all Pay-As-You-Go data disks that are mounted to an instance to Subscription ones.

-   This interface cannot be called if the release time has been set for a Pay-As-You-Go instance.


## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|Name of this interface. Value: ModifyInstanceChargeType|
|RegionId|String|Yes|ID of the region where the instance is located.For more information, call [DescribeRegions](../reseller.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|InstanceIds|String|Yes|Instance ID. The parameter value is a JSON array composed of multiple instance IDs in the \["s-xxxxxxxxx", "s-yyyyyyyyy", … "s-zzzzzzzzz"\] format. A maximum of 20 IDs are allowed, and the IDs must be separated by commas \(`,`\).|
|Period|Integer|No|Instance life cycle|
|PeriodUnit|String|No|Unit of the instance life cycle. Value range: year, month, week, and dayCurrently, only `Year`, `Week`, and `Month` are supported.

|
|IncludeDataDisks|Boolean|No|Whether to change all Pay-As-You-Go data disks that are mounted to the instance to Subscription ones. The default value is true.|
|InstanceChargeType|String|No|Target billing method. Value range:-   PrePaid \(default value\): Subscription, indicating the billing method change from Pay-As-You-Go to Subscription
-   PostPaid: Pay-As-You-Go, indicating the billing method change from Subscription to Pay-As-You-Go

|
|AutoPay|Boolean|No|Whether to allow automatic payment. Value range:-   true \(default value\): Automatic payment is allowed. Make sure that the balance of your payment method is sufficient. If the balance is insufficient, an abnormal order will be generated, which can only be voided.
-   false: An order is generated with no fee charged. If the balance of your payment method is insufficient, a normal unpaid order will be generated. In this case, you can log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs) to pay for the order.

|
|DryRun|Boolean|No|Whether the system performs a permission check only.-   true: Sends a permission check request, without performing actual API action. An enabled DryRun checks whether your AccessKey is valid, the authorization status of a RAM user, and whether the required parameters are set. If you do not have the required permissions, a related error response is returned. Otherwise, it is `DryRunOperation`.
-   False: Sends a normal request, returns the 2XX HTTP status code after the check and queries the resource status directly.

Default value: false.

|
|ClientToken|String|No|Guarantees the idempotence of the request.  The value is generated by a client and must be globally unique. Only ASCII characters are allowed. It can contain a maximum of 64 ASCII characters. For more information, see [How to ensure idempotence](../reseller.en-US/API Reference/Appendix/How to ensure idempotence.md#).

|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|OrderId|Long|ID of a generated order|

## Examples { .section}

**Request example**

```
https://ecs.aliyuncs.com/?Action=ModifyInstanceChargeType
&RegionId=cn-hangzhou
&InstanceIds=["i-xxxxx1","i-xxxxx2"]
&Period=1
&PeriodUnit=Month
&AutoPay=false
&IncludeAllDisks=true
&ClientToken=xxxxxxxxxxxxxx
&<Common Request Parameters>
```

**Response example**

**XML format**

```
<ModifyInstanceConfigurationResponse>
    <RequestId>04F0F334-1335-436C-A1D7-6C044FExxxxx</RequestId>
    <OrderId>10111111111xxxxx</OrderId>
</ModifyInstanceConfigurationResponse>
```

**JSON format**

```
{
    "RequestId": "04F0F334-1335-436C-A1D7-6C044FExxxxx",
    "OrderId": 1011111111111111,
}
```

## Error codes {#ErrorCode .section}

|Error code|Error message|HTTP status code|Description|
|:---------|:------------|:---------------|:----------|
|ExpiredInstance|Expired instances exist in your request list.|400|An overdue instance exists in the instance list.|
|InstancesIdQuotaExceed|The maximum number of Instances is exceeded.|400|A maximum of 20 instances can be specified at a time.|
|InvalidInstance.UnpaidOrder|The specified instance has unpaid order.|400|There are still unpaid orders under this instance.|
|InvalidClientToken.ValueNotSupported|The ClientToken provided is invalid.|400|The value of `ClientToken` is invalid. Only ASCII characters are allowed.|
|InvalidParameter.InstanceIds|The specified InstanceIds are invalid.|400|The specified `InstanceIds` is invalid.|
|InvalidStatus.ValueNotSupported|The instance cannot be modified in the specified status.|400|The instance must be **running** \(indicated by `Running`\) or **stopped** \(indicated by `Stopped`\).|
|ReleaseTimeHaveBeenSet|The specified instance has been set released time.|400|Your request involves an instance whose release time has been set.|
|Throttling|You have made too many requests within a short time; your request is denied due to request throttling.|400|Your operations are too frequent. Please try again later.|
|InvalidPeriod.ExceededDedidactedHost|Instance expired date can't exceed dedicated host expired date.|400|The instance life cycle cannot be longer than the dedicated host life cycle.|
|InvalidAccountStatus.NotEnoughBalance|Your account does not have enough balance.|403|The balance of your payment method is insufficient|
|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|404|The specified instance does not exist.|
|InternalError|The request processing has failed due to some unknown error, exception or failure.| 500|There is an internal error.|

