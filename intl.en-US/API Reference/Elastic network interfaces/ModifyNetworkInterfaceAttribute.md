# ModifyNetworkInterfaceAttribute {#ModifyNetworkInterfaceAttribute .reference}

You can modify the attribute of an ENI \(Elastic Network Interface\) by calling this API. However, you can only modify the attribute of one ENI each time.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: ModifyNetworkInterfaceAttribute.|
|RegionId|String|Yes|ID of the region where the instance belongs. For more information, call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|NetworkInterfaceId|String|Yes|ENI ID.|
|SecurityGroupId.N|String|No|ID of the security group. The new security group replaces the earlier one, and the security group must be in the same VPC as the ENI.|
|NetworkInterfaceName|String|No|ENI name.-   It is a string of \[2, 128\] Chinese or English characters. It must begin with an uppercase/lowercase letter or a Chinese character and can contain numbers, underscores \(\_\), or hyphens \(-\).
-   The ENI name is displayed in the console.
-   Cannot begin with http:// or https://.
-   Can be null. Default value: null.

|
|Description|String|No|The ENI description.-   It is a string of \[2, 256\] English or Chinese characters.
-   It cannot begin with http:// or https://.
-   If this parameter is not specified, it is null by default.

|

## Response parameters {#section_f54_lk5_xdb .section}

All are common response parameters. For more information, see [Common parameters](intl.en-US/API Reference/Call methods/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=ModifyNetworkInterfaceAttribute
&RegionId=cn-hangzhou
&NetworkInterfaceId=[networkInterfaceId]
&<Common Request Parameters>
```

**Response example** 

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

Error codes specific to this interface are as follows. For more error codes, visit [API error center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code|Description|
|:---------|:------------|:---------------|:----------|
|UnsupportedParameter|The parameters is unsupported.|400|The specified parameter does not exist. Alternatively, the specified parameter is not supported.|
|MissingParameter|The input parameter that is mandatory for processing this request is not supplied.|400|You must specify the required parameter.|
|Abs.InvalidAccount.NotFound|The Account is not found or ak is expired.|403|The specified Alibaba Cloud account does not exist. Alternatively, your AccessKey expires.|
|Forbidden.NotSupportRAM|This action does not support accessed by RAM mode.|403|RAM users are not allowed to access the resource.|
|Forbidden.SubUser|The specified action is not available for you.|403|RAM users are not allowed to access the resource.|
|InvalidOperation.AvailabilityZoneMismatch|The VPC VSwitch of the specified ENI and ECS instance are not in the same availability zone.|403|The specified VPC VSwitch ID, ENI and instance ID are not in the same availability zone.|
|InvalidOperation.VpcMismatch|The VPC of the specified ENI and security group are not in the same VPC.|403|The specified ENI and security group ID are not in the same VPC.|
|SecurityGroupInstanceLimitExceed|The maximum number of instances in a security group is exceeded.|403|The maximum number of instances in the specified security group is exceeded.|
|InvalidSecurityGroupId.NotVpc|The specified SecurityGroupId not in VPC.|403|The specified security group ID is not in a VPC.|
|InvalidOperation.InvalidEniType|The operation is not allowed in the current ENI type.|403|The specified action failed due to the type of the ENI.|
|InvalidVSwitchId.NotFound|The specified VSwitchId is not found.|404|The specified VSwitch ID does not exist.|
|InvalidSecurityGroupId.NotFound|The specified SecurityGroupId is not found.|404|The specified security group ID does not exist.|

