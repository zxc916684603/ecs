# ModifyPrepayInstanceSpec {#ModifyPrepayInstanceSpec .reference}

Changes the instance type of Subscription instances.

## Description {#section_pvl_dj5_xdb .section}

When using this operation, consider the following:

-   The specified instance must be in the **Stopped** \(`Stopped`\) status.
-   The specified instance cannot have outstanding payment.
-   Before changing the [subscribed](../reseller.en-US/Pricing/Subscription.md#) instance type, you can use the [DescribeResourcesModification](reseller.en-US/API Reference/Regions/DescribeResourcesModification.md#) API to query the instance types you can change to.
-   After downgrading the instance type, the new instance type applies to the entire lifecycle of the instance. After an instance is downgraded, you are refunded the price difference for the instance to the payment method you used. If you used coupons, they are not refunded.
-   An instance that was successfully operated upon once cannot be operated upon again within five minutes.
-   An instance cannot be downgraded more than three times.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The operation that you want to perform. Value: ModifyPrepayInstanceSpec.|
|InstanceId|String|Yes|Instance ID.|
|RegionId|String|Yes|The region ID.For more information, call [DescribeRegions](../reseller.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|InstanceType|String|Yes|The instance type to change to. For more information, see [Instance Type Family](../reseller.en-US/Product Introduction/Instance type families.md#), or call [DescribeInstanceTypes](reseller.en-US/API Reference/Instances/DescribeInstanceTypes.md#) to obtain the latest type list.|
|OperatorType|String|No|Operation type. Optional values:-   upgrade: Upgrades the instance type.
-   downgrade: Downgrades the instance type.

Default: Upgrade.

Make sure that your registered credit card is valid or enough balance in your PayPal account when you set `OperatorType` to `upgrade`.

|
|AutoPay|Boolean|No|Whether or not automatic payment is enabled. Optional values:-   true: Automatic payment. Make sure that your registered credit card is valid or enough balance in your PayPal account. If the balance is not sufficient, an exception order is generated, which can only be voided.
-   false: Generates orders, but does not deduct the funds. If your registered credit card is invalid or has credit limit set, a normal unpaid order is generated. You can log on to the ECS console to settle this order.By default, the system uses the latest billing method to automatically charge fees. Make sure that your account balance is sufficient. Otherwise, the system regards your order as an exception, and you have to cancel this order. If your account balance is insufficient, set `AutoPay` to `false`. The system then generates a normal unpaid order for the outstanding payment. You can log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs) to pay for this order.

Default: true.When the parameter `OperatorType` is set to `downgrade`, the `AutoPay` parameter is ignored.

|
|SystemDisk.Category|String|No|The new category of system disk. This parameter is only used for upgrades from [phased-out instance types](https://partners-intl.aliyun.com/help/faq-detail/55263.htm), to [instance type families available for sale](../reseller.en-US/Product Introduction/Instance type families.md#) and from non-I/O optimized instance types to I/O optimized instance types. Optional values:-   cloud\_efficiency: Ultra cloud disk.
-   cloud\_ssd: SSD cloud disk.

|
|MigrateAcrossZone|Boolean|No|Specifies whether to upgrade the instance among different clusters or not.Default: false.

When the `MigrateAcrossZone` is set to `True` and you change the instance type according to the returned information, you must make sure that:

-   For classic network-connected instances:
    -   If you upgrade the [phased-out instance types](https://partners-intl.aliyun.com/help/faq-detail/55263.htm), non-I/O optimized instances to I/O optimized instances, the instance-related intranet IP address, disk device names and license key of the instance may change. For Linux instances, Basic Cloud Disks \(`cloud`\) will be recognized as `xvda` or `xvdb`, while Ultra Cloud Disks \(`cloud_efficiency`\) and SSD Cloud Disks \(`cloud_ssd`\) as `vda` or `vdb`.
    -   If your classic network instances are available in the [instance type families](../reseller.en-US/Product Introduction/Instance type families.md#), the private IP of the instances may change.
-   For VPC-Connected instances:

If you upgrade the [phased-out instance types](https://partners-intl.aliyun.com/help/faq-detail/55263.htm), non-I/O optimized instances to I/O optimized instances, the disk device names and license key of the ECS may change. For Linux instances, Basic Cloud Disks \(`cloud`\) will be recognized as `xvda` or `xvdb`, while Ultra Cloud Disks \(`cloud_efficiency`\) and SSD Cloud Disks \(`cloud_ssd`\) as `vda` or `vdb`.


|
|ClientToken|String|No| Guarantees the idempotence of the request.  The value is generated by a client and must be globally unique. Only ASCII characters are allowed. It can contain a maximum of 64 ASCII characters. For more information, see [How to ensure idempotence](../reseller.en-US/API Reference/Appendix/How to ensure idempotence.md#).

 |

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|OrderId|Long|Order ID.|

## Examples { .section}

**Request example**

```
https://ecs.aliyuncs.com/?Action=ModifyPrepayInstanceSpec
&RegionId=cn-hangzhou
&InstanceId=i-xxxxx1
&InstanceType=ecs.s1.large
&AutoPay=true
&OperatorType=upgrade
&ClientToken=xxxxxxxxxxxxxx
&<Common Request Parameters>
```

**Response example**

**XML format**

```
<ModifyPrepayInstanceSpecResponse>
    <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
    <OrderId>1011111111111111</OrderId>
</ModifyPrepayInstanceSpecResponse>
```

**JSON format**

```
{
    "RequestId": "04F0F334-1335-436C-A1D7-6C044FE73368",
    "OrderId": 1011111111111111,
}
```

## Error codes {#ErrorCode .section}

|Error code|Error message|HTTP status code|Description|
|:---------|:------------|:---------------|:----------|
|Account.Arrearage|Your account has an outstanding payment.|400|Overdue payment exists in your account.|
|IdempotenceParamNotMatch|Request uses a client token in a previous request but is not identical to that request.|400|The parameters of the requests that use the same `ClientToken` do not match.|
|InvalidBillingMethod.ValueNotSupported|The operation is not permitted due to an invalid billing method of the instance.|400|The instance billing method is invalid.|
|InvalidClientToken.ValueNotSupported|The ClientToken provided is invalid.|400|The value of `ClientToken` is invalid. Only ASCII characters are allowed.|
|InvalidInstance.UnpaidOrder|The specified Instance has unpaid order.|400|The current instance has outstanding orders.|
|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|400|The specified instance ID does not exist.|
|InvalidInstanceId.Released|The specified Instance has been released.|400|The specified instance has been released.|
|InvalidInstanceType.ValueNotSupported|The specified InstanceType is not supported.|400|The specified `InstanceType` is invalid or does not exist.|
|InvalidInstanceType.ValueUnauthorized|The specified InstanceType is not authorized.|400|The specified `InstanceType` is unauthorized.|
|MissingParameter.InstanceIdNotSupported|The InstanceId should not be null.|400|The `InstanceId` is required.|
|MissingParameter.RegionId|The RegionId should not be null.|400|The `RegionId` is required.|
|OrderCreationFailed|Order creation failed, please check your params and try it again later.|400|Failed to create the order because of the parameters setting.|
|Throttling|You have made too many requests within a short time; your request is denied due to request throttling.|400|You have made too many frequent requests in a short time.|
|ImageNotSupportInstanceType|The specified image does not support the specified InstanceType.|403|The specified image does not support this instance type.|
|InvalidAccountStatus.NotEnoughBalance|Your account does not have enough balance.|403|Your registered credit card is invalid or has credit limit set.|
|InvalidBillingMethod|The specified billing method is invalid.|403|The specified billing method does not exist.|
|InvalidUser.PassRoleForbidden|The RAM user does not have privilege to pass a role.|403|Your RAM user does not have the `PassRole` permission. Contact the owner of the primary account to [grant](../reseller.en-US/Quick Start/Attach policies to a RAM user.md#) the PassRole permission.|
|BillingMethodNotFound|The account has not chosen any billing method.|404|No payment method was selected for your account.|
|InvalidRegionId.NotFound|The specified RegionId does not exist.|404|The specified `RegionId` does not exist.|
|InternalError|The request processing has failed due to some unknown error, exception or failure.|500|Internal error.|

