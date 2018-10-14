# ModifySecurityGroupPolicy {#reference_fps_ngn_ydb .reference}

Modifies the intranet communication policy of a security group.

## Description {#section_m51_pgn_ydb .section}

When you call this interface, consider the following:

-   If the `InnerAccessPolicy` property of a security group is set to `Accept`, all the instances in the security group can always communicate with each other. The `Accept` policy has a high priority and other manual modification is ignored.

-   If the `InnerAccessPolicy` property of a security group is set to `Drop`, all the instances in the security group is blocked from communication. However, you can add rules by calling the [AuthorizeSecurityGroup](reseller.en-US/API Reference/Security groups/AuthorizeSecurityGroup.md#) to enable the intranet communication among several instances.

-   You can query the intranet communication status of a security group by calling the [DescribeSecurityGroupAttribute](reseller.en-US/API Reference/Security groups/DescribeSecurityGroupAttribute.md#).


## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: ModifySecurityGroupPolicy.|
|SecurityGroupId|String|Yes|ID of a security group.|
|RegionId|String|Yes|ID of the region to where a specified security group belongs. For more information, call [DescribeRegions](reseller.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|InnerAccessPolicy|String|Yes|The intranet communication status of a security group. Optional values:-   Accept: All the instances in the specified security group can communicate with each other.
-   Drop: The intranet communication in the specified security group is blocked.

The values are case insensitive.|

## Response parameters {#section_f54_lk5_xdb .section}

All are common response parameters. For more information, see [Common parameters](reseller.en-US/API Reference/Getting started/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=ModifySecurityGroupPolicy
&RegionId=cn-hangzhou
&SecurityGroupId=sg-1133aa
&InnerAccessPolicy=Drop
&<Common Request Parameters>
```

**Response example** 

**XML format** 

```
<ModifySecurityGroupPolicyResponse>
    <RequestId>CEF72CEB-54B6-4AE8-B225-F876xxxxxxxx</RequestId>
</ModifySecurityGroupPolicyResponse>
```

 **JSON format** 

```
{
    "RequestId": "CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
}
```

## Error codes {#ErrorCode .section}

|Error code|Error message|HTTP status code|Meaning|
|:---------|:------------|:---------------|:------|
|InvalidPolicy.Malformed|The InnerAccessPolicy is invalid. Only Accept and Drop are supported.|400|You must specify the `InnerAccessPolicy`. Or the specified parameter is invalid.|
|InvalidSecurityGroupId.Malformed|The SecurityGroupId is invalid. Only letters, numbers and underscores are supported. Maximum length is 100 characters.|400|You must specify the `SecurityGroupId`. Or the specified parameter is invalid.|
|InvalidRegionId.NotFound|The RegionId provided does not exist.|404|The specified `RegionId` does not exist.|

