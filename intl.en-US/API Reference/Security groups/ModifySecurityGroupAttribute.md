# ModifySecurityGroupAttribute {#ModifySecurityGroupAttribute .reference}

Modifies the attribute of the specified security group, including the security group name and description.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: ModifySecurityGroupAttribute.|
|RegionId|String|Yes| The region ID. For more information, call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|SecurityGroupId|String|Yes| The ID of the security group.|
|SecurityGroupName|String|No| The security group name.-   Can contain \[2, 128\] characters in length. Must begin with an English letter. Can contain digits, periods \(.\), underscores \(\_\), and hyphens \(-\).
-   The security group name is displayed in the console.
-   Cannot begin with http:// or https://.

|
|Description|String|No| The description of the security group.-   Can contain \[2, 256\] characters in length.
-   Cannot begin with http:// or https://.
-   Cannot be a null string, otherwise, the `Description` is ignored in the request.

|

## Response parameters {#section_f54_lk5_xdb .section}

All are common response parameters. For more information, see [Common parameters](intl.en-US/API Reference/Call methods/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=ModifySecurityGroupAttribute
&SecurityGroupId=sg-F876FF7BA
&RegionId=cn-hangzhou
&SecurityGroupName=NewName
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<ModifySecurityGroupAttributeResponse>
     <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
</ModifySecurityGroupAttributeResponse>
```

 **JSON format** 

```
{
    "RequestId":"CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
}
```

## Error codes {#ErrorCode .section}

The following error codes are restricted to this interface. For more error codes, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code|Meaning|
|:---------|:------------|:---------------|:------|
|InvalidSecurityGroupDiscription.Malformed|Specified security group description is not valid.|400|The specified `Description` is invalid.|
|InvalidSecurityGroupName.Malformed|Specified security group name is not valid.|400|The specified `SecurityGroupName` is invalid.|
|InvalidSecurityGroupId.NotFound|The specified SecurityGroupId does not exist.|404|The specified `SecurityGroupId` is invalid.|

