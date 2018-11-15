# ModifyInstanceAutoRenewAttribute {#ModifyInstanceAutoRenewAttribute .reference}

Sets the auto renewal attribute of an instance. 

## Description {#section_hjb_cg5_xdb .section}

-   Fee deduction for auto renewal starts at 08:00:00 \(UTC +08:00\) on the ninth day before the expiry date.

-   If fee deduction fails, it attempts to charge the fees at 08:00:00 \(UTC +08:00\) every day before the expiry date. If the payment attempts keep failing until the expiry date, the instance is released and gets out-of-service. You must make sure that you have not set any credit limit on your credit card.


## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: ModifyInstanceAutoRenewAttribute.|
|RegionId|String|Yes.|Region ID of an instance. You can call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|InstanceId|String|Yes.|Instance ID. A maximum of 100 instances billed by subscription can be set in batches. Multiple instance IDs are separated with commas \(,\).|
|Duration|Integer|No|Auto renewal duration of an instance, in the unit of month. Optional values: 1 | 12.|
|AutoRenew|Boolean|No|Auto renewal or not. Optional values:-   True: Auto renewal enabled
-   False: Auto renewal disabled

Default value: False.|
|RenewalStatus|String|No|Whether to renew an ECS instance automatically or not, and the `RenewalStatus` parameter has a priority over the `AutoRenew` parameter.  If no value is specified for the `RenewalStatus` parameter, the `AutoRenew` parameter prevails by default. Optional values:-   AutoRenewal: Enable auto renewal.
-   Normal: Disable auto renewal.
-   NotRenewal: No renewal any longer. After you specify this value, Alibaba Cloud stop sending notification of instance expiry, and only gives a brief reminder on the third day before the instance expiry. In this case, if you want to renew your instance, you can change the renewal status of your instance before a manual renewal or set it to auto renewal mode.

|

## Response parameters {#section_rjb_cg5_xdb .section}

The response parameters are all common response parameters. For more information, see [Common parameters](intl.en-US/API Reference/Call methods/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=ModifyInstanceAutoRenewAttribute
&RegionId=cn-hangzhou
&InstanceId=i-instance1,i-instance2
&Duration=2
&AutoRenew=True
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<ModifyInstanceAutoRenewAttributeResponse>
    <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
</ModifyInstanceAutoRenewAttributeResponse>
```

 **JSON format** 

```

    "RequestId": "04F0F334-1335-436C-A1D7-6C044FE73368"

```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more information, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message |HTTP status code|Meaning|
|:---------|:-------------|:---------------|:------|
|ChargeTypeViolation|Pay-As-You-Go instances do not support this operation.|403|Pay-As-You-Go instances do not support this operation.|
|IncorrectInstanceStatus|The current status of the resource does not support this operation.|403|This operation is not supported because the instance is expired.|
|InvalidParameter.Duration|The auto renewal duration should be one of the following values: 1|2|3|6|12.|403|The specified auto renewal duration must be 1 month or 12 months.|
|InvalidParameter.InvalidInstanceId|The specified instanceId is not valid.|403|The specified `InstanceId` is invalid.|
|InvalidParameter.ToManyInstanceIds|No more than 100 InstanceIds can be specified.|403|The number of the specified `InstanceId` cannot exceed 100.|
|MissingParameter.InstanceId|InstanceId should not be null.|403|`InstanceId` is required.|

