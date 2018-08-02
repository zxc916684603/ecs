# AttachInstanceRamRole {#AttachInstanceRamRole .reference}

Attaches an [instance RAM role](../../../../intl.en-US/User Guide/Instances/Instance RAM roles/What is the RAM role of an instance.md#) to your ECS instance. You can only assign one RAM role to an instance at any time. If the instance already has a RAM role, an error code returns when you attach another RAM role to the same instance.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: AttachInstanceRamRole.|
|RegionId|String|Yes|Region ID. You can call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|InstanceIds|Array|Yes|Instance ID set. A maximum of 100 instances are supported, in the format of \["instanceId1", "instanceId2",  "instanceId3"…\].|
|RamRoleName|String|Yes|Instance RAM role name. The name is provided and maintained by *RAM*. You can call [ListRoles](../../../../intl.en-US//Role Management Interface/ListRoles.md#) to view the ram role list. For more information, see API [CreateRole](../../../../intl.en-US//Role Management Interface/CreateRole.md#) and [ListRoles](../../../../intl.en-US//Role Management Interface/ListRoles.md#).|

## Response parameters {#ResponseParameter .section}

All are common response parameters. For more information, see [Common parameters](intl.en-US/API Reference/Call methods/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=AttachInstanceRamRole
&RegionId=cn-hangzhou
&RamRoleName=RamRoleTest
&InstanceIds=["i-instance1"]
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<AttachInstanceRamRoleResponse>
    <RequestId>E6352369-5C2B-41CD-AB50-471550C8F674</RequestId>
    <AttachInstanceRamRoleResults>
        <AttachInstanceRamRoleResult>
             <InstanceId>i-instance1</InstanceId>
             <Code>200</Code>
             <Message>success</Message>
        </AttachInstanceRamRoleResult>
    </AttachInstanceRamRoleResults>
    <TotalCount>1</TotalCount>
    <FailCount>0</FailCount>
    <RamRoleName>RamRoleTest</RamRoleName>
</AttachInstanceRamRoleResponse>
```

 **JSON format** 

```
{
    "RequestId": "D9553E4C-6C3A-4D66-AE79-9835AF705639",
    "AttachInstanceRamRoleResults": {
        "AttachInstanceRamRoleResult": [
            {
                "Message": "success",
                "InstanceId": "i-instance1",
                "Code": "200"
            }
        ]
    },
    "TotalCount": 1,
    "FailCount": 0,
    "RamRoleName": "RamRoleTest"
}
```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more information, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message |HTTP status code|Meaning|
|:---------|:-------------|:---------------|:------|
|InvalidInstanceIds.Malformed|The specified InstanceIds is not valid.|400|The specified InstanceIds is invalid.|
|MissingParameter.InstanceIds|The input parameter InstanceIds that is mandatory for processing this request is missing.|400|The required InstanceIds parameter is missing.|
|MissingParameter.RamRoleName|The input parameter RamRoleName that is mandatory for processing this request is missing.|400|The required RamRoleName parameter is missing.|
|MissingParameter.RegionId|The input parameter RegionId that is mandatory for processing this request is missing.|400|The required RegionId parameter is missing.|
|InvalidNetworkType.MismatchRamRole|Ram role cannot be attached to instances of Classic network type.|403|RAM roles cannot be attached to instances of classic network type.|
|InvalidUser.PassRoleForbidden|The RAM user does not have the privilege to pass a role.|403|The RAM user does not have the privilege to pass a role.|
|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|404|The specified InstanceId does not exist.|
|InvalidRamRole.NotFound|The specified RamRoleName does not exist.|404|The specified RamRoleName does not exist.|

