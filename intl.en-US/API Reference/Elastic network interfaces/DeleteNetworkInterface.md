# DeleteNetworkInterface {#DeleteNetworkInterface .reference}

Deletes an elastic network interface \(ENI \).

## Description {#section_tyd_kj4_ydb .section}

-   The ENI must be in the `Available` status.
-   If the ENI has been attached to an ECS instance, you must first detach it from the ECS instance \([DetachNetworkInterface](intl.en-US/API Reference/Elastic network interfaces/DetachNetworkInterface.md#)\) and then delete it.
-   After the ENI is removed:
    -   The primary private IP address of the ENI \(`PrimaryIpAddress`\) is automatically released.
    -   The deleted ENI automatically exits from its security group.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DeleteNetworkInterface.|
|RegionId|String|Yes|Region ID. For more information about the region ID list, view the region list by calling the [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#).|
|NetworkInterfaceId|String|Yes|ENI ID.|

## Response parameters {#section_f54_lk5_xdb .section}

All are common response parameters. For more information, see [Common parameters](intl.en-US/API Reference/Call methods/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DeleteNetworkInterface
&RegionId=cn-hangzhou
&NetworkInterfaceId=[networkInterfaceId]
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<DetachNetworkInterface>
    <RequestId>04F0F334-1335-436C-A1D7-6C044FExxxxx</RequestId>
</DetachNetworkInterface>
```

 **JSON format** 

```
{
    "RequestId": "04F0F334-1335-436C-A1D7-6C044FExxxxx",
}
```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more error codes, visit the [API error center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code |Description|
|:---------|:------------|:----------------|:----------|
|Abs.InvalidAccount.NotFound|The Account is not found or AK is expired.|403|The specified Alibaba Cloud account does not exist. Alternatively, your AccessKey expires.|
|Forbidden.NotSupportRAM|This action does not support accessed by RAM mode.|403|Ram users are not allowed to perform this operation.|
|UnsupportedParameter|The parameters is unsupported.|400|The specified parameter does not exist. Alternatively, the specified parameter is not supported.|
|Forbidden.SubUser|The specified action is not available for you.|403|Ram users are not allowed to perform this operation.|
|InvalidOperation.DetachPrimaryEniNotAllowed|Detaching primary ENI from ECS instance is not allowed.|400|You cannot detach the primary network interface from an ECS instance.|
|MissingParameter|The input parameter that is mandatory for processing this request is not supplied.|400|You must specify the required parameter.|
|InvalidOperation.InvalidEniType|The operation is not allowed in the current ENI type.|403|The specified action failed due to the type of the ENI.|

