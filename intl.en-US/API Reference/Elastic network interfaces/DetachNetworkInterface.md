# DetachNetworkInterface {#DetachNetworkInterface .reference}

Detaches an ENI from your instance.

## Description {#section_u1n_s34_ydb .section}

-   You cannot detach the primary network interface of an instance.

-   The ENI must be in the **InUse** \(`InUse`\) status.

-   The instance must be in **Running** \(`Running`\) or **Stopped** \(`Stopped`\) status.


## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DetachNetworkInterface|
|RegionId|String|Yes|ID of the region of the ECS instance. For more information, call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|NetworkInterfaceId|String|Yes|ENI ID.|
|InstanceId|String|Yes|Instance ID.|

## Response parameters {#section_f54_lk5_xdb .section}

All are common parameters. For more information, see [Common parameters](intl.en-US/API Reference/Call methods/Common parameters.md#).

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DetachNetworkInterface
&RegionId=cn-hangzhou
&NetworkInterfaceId=[networkInterfaceId]
&InstanceId=AY121018033933eaxxxxx
&<Common Request Parameters>
```

**Response sample** 

**XML format**

```
<DetachNetworkInterfaceResponse>
    <RequestId>04F0F334-1335-436C-A1D7-6C044FExxxxx</RequestId>
</DetachNetworkInterfaceResponse>
```

 **JSON format** 

```
{
    "RequestId": "04F0F334-1335-436C-A1D7-6C044FExxxxx",
}
```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more error codes, visit the [API error center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code|Description|
|:---------|:------------|:---------------|:----------|
|UnsupportedParameter|The parameters is unsupported.|400|The specified parameter does not exist. Alternatively, the specified parameter is not supported.|
|InvalidOperation.InvalidEcsState|The operation is not allowed in the current ECS state.|400|The specified action failed due to the status of the instance.|
|InvalidOperation.DetachPrimaryEniNotAllowed|Detaching primary ENI from ECS instance is not allowed.|400|You cannot detach the primary network interface from an ECS instance.|
|MissingParameter|The input parameter that is mandatory for processing this request is not supplied.|400|You must specify the required parameter.|
|Forbidden.SubUser|The specified action is not available for you.|403|Ram users are not allowed to perform this operation.|
|Abs.InvalidAccount.NotFound|The Account is not found or ak is expired.|403|The specified Alibaba Cloud account does not exist. Alternatively, your AccessKey expires.|
|Forbidden.NotSupportRAM|This action does not support accessed by RAM mode.|403|Ram users are not allowed to perform this operation.|
|EniPerInstanceLimitExceeded|The number of ENI exceeds the limit for the type of instance you are trying to launch.|403|The maximum number of ENI in the specified region is exceeded.|
|InvalidOperation.InvalidEniType|The operation is not allowed in the current ENI type.|403|The specified action failed due to the type of the ENI.|
|InvalidEcsId.NotFound|The specified EcsId is not found.|404|The specified instance Id does not exist.|

