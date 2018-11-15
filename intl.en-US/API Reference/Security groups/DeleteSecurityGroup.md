# DeleteSecurityGroup {#DeleteSecurityGroup .reference}

Deletes one of your security groups. Make sure the security group is not authorized by other security groups \([DescribeSecurityGroupReferences](intl.en-US/API Reference/Security groups/DescribeSecurityGroupReferences.md#), and the security group manages no instance. Otherwise, the `DeleteSecurityGroup` action fails.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DeleteSecurityGroup.|
|SecurityGroupId|String|Yes|The security group ID.|
|RegionId|String|Yes|The ID of the region to which the security group belongs. For more information, call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|

## Response parameters {#section_f54_lk5_xdb .section}

All parameters are common response parameters. For more information, see [Common parameters](intl.en-US/API Reference/Call methods/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DeleteSecurityGroup
&RegionId=cn-hangzhou
&SecurityGroupId=sg-F876FF7BA
&<Common Request Parameters>
```

**Response example** 

**XML format** 

```
<DeleteSecurityGroupResponse>
     <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
</DeleteSecurityGroupResponse>
```

 **JSON format** 

```
{
    "RequestId":"CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
}
```

## Error codes {#ErrorCode .section}

The following error codes are specific to this interface. For more error codes, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code|Meaning|
|:---------|:------------|:---------------|:------|
|DependencyViolation|There is still instance\(s\) in the specified security group.|403|The specified security group is managing instances.|
|DependencyViolation|The specified security group has been authorized in another one.|403|The specified security group is authorized by other security groups.|
|InvalidRegionId.NotFound|The specified RegionId does not exist.|404|The specified `RegionId` does not exist.|

