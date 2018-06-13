# ModifyInstanceVncPasswd {#ModifyInstanceVncPasswd .reference}

Change the password of [management terminal](../../../../intl.en-US/User Guide/Connect/Terminal.md) used to connect a specified ECS instance.

## Description {#section_m4j_bst_xdb .section}

-   The password must be six characters in length, and can contain uppercase or lowercase English letters and digits. The password cannot contain special characters.
-   After you change the password:
    -   For an I/O Optimized instances, the new password takes effect immediately.
    -   For a non-I/O Optimized instances, you must [restart the instance](../../../../intl.en-US/User Guide/Instances/Restart an instance.md) in the console or by calling API [RebootInstance](intl.en-US/API Reference/Instances/RebootInstance.md#) to make the change take effect.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface.  Value: ModifyInstanceVncPasswd.|
|RegionId|String|Yes|The region of the ECS instance. You can call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|InstanceId|String|Yes|The ECS instance.|
|VncPassword|String|Yes|The new password of management terminal used to connect the specified ECS instance.|

## Response parameters {#section_u4j_bst_xdb .section}

All parameters are common response parameters. For more information, see [Common parameters](intl.en-US/API Reference/Call methods/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=ModifyInstanceVncPasswd
&DescribeInstanceVncUrl
&InstanceId=AY121018033933eae8689
&VncPassword=123456
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<ModifyInstanceVncPasswdResponse>
    <RequestId>FDB6C963-9CE8-4B7F-BCA3-845F6BD29AFC</RequestId>
</ModifyInstanceVncPasswdResponse>
```

 **JSON format** 

```

  "RequestId": "FDB6C963-9CE8-4B7F-BCA3-845F6BD29AFC", 

```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more information, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message |HTTP status code|Meaning|
|:---------|:-------------|:---------------|:------|
|IncorrectVncPassword.Malformed|The specified parameter VncPassword is not valid.|400|The specified `VncPassword` is invalid, it must be six characters in length, and can only contain uppercase or lowercase English letters and digits.|
|IncorrectInstanceStatus|The current status of the resource does not support this operation.|403|The specified instance must be in the **Running** status.|
|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|404|The specified ECS instance does not exist.|
|InvalidRegionId.NotFound|The specified RegionId does not exist.|404|The specified `RegionId` does not exist.|

