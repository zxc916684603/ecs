# DetachInstanceRamRole {#DetachInstanceRamRole .reference}

Detaches a [RAM role](../../../../intl.en-US/User Guide/Instances/Instance RAM roles/What is the RAM role of an instance.md#) from an instance.

## Request Parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DetachInstanceRamRole.|
|RegionId|String|Yes| Region ID. You can call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#).|
|InstanceIds|String|Yes|Instance ID set. A maximum of 100 instances are supported, in the format of \["instanceId1", "instanceId2",  "instanceId3"…\].|
|RamRoleName|String|No|Instance RAM role name. The name is provided and maintained by *RAM* and can be queried using [ListRoles](../../../../intl.en-US//Role Management Interface/ListRoles.md#). For more information, see the relevant APIs [CreateRole](../../../../intl.en-US//Role Management Interface/CreateRole.md#) and [ListRoles](../../../../intl.en-US//Role Management Interface/ListRoles.md#).|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|TotalCount|Integer|The number of ECS instances from which the instance RAM role is going to be detached.|
|FailCount|Integer|The number of ECS instances from which the instance RAM role failed to be detached.|
|RamRoleName|String|The name of instance RAM role.|
|DetachInstanceRamRoleResults|Array|A set composed of action details about detaching instance RAM role from an ECS instance\([DetachInstanceRamRoleResult](#DetachInstanceRamRoleResult)\).|

 **DetachInstanceRamRoleResult** 

|Name|Type|Description|
|:---|:---|:----------|
|InstanceId|String|The ECS instance from which the instance RAM role is going to be detached.|
|Code|Integer|It indicates whether you have successfully detached the instance RAM role from the ECS instance or not. If `Code=200` returns,  the action is successful, and if the other value returns, the action is unsuccessful. For more information on how to fix the errors, see [Error codes](#ErrorCode).|
|Message|String|Indicates whether you have successfully detached the instance RAM role from the ECS instance or not. If  `Message=Success` returns,  the action is successful, and if the other value returns, the action is unsuccessful. For more information on how to fix the errors, see [Error codes](#ErrorCode).|

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DetachInstanceRamRole
&RegionId=cn-hangzhou
&RamRoleName=RamRoleTest
&InstanceIds=["i-instance1"]
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<DetachInstanceRamRoleResponse>
    <RequestId>E6352369-5C2B-41CD-AB50-471550C8F674</RequestId>
    <DetachInstanceRamRoleResults>
        <DetachInstanceRamRoleResult>
             <InstanceId>i-instance1</InstanceId>
             <Code>200</Code>
             <Message>success</Message>
        </DetachInstanceRamRoleResult>
    </DetachInstanceRamRoleResults>
    <TotalCount>1</TotalCount>
    <FailCount>0</FailCount>
    <RamRoleName>RamRoleTest</RamRoleName>
</DetachInstanceRamRoleResponse>

```

 **JSON format** 

```

    "RequestId": "E6352369-5C2B-41CD-AB50-471550C8F674",
    "DetachInstanceRamRoleResults": {
        "DetachInstanceRamRoleResult": [
            
                "Message": "success",
                "InstanceId": "i-instance1",
                "Code": "200"
            
        
    
    "TotalCount": 1,
    "FailCount": 0,
    "RamRoleName": "RamRoleTest"

```

## Error codes {#ErrorCode .section}

The following error codes are specific to this interface. For more error codes, visit the [API error center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code|Meaning|
|:---------|:------------|:---------------|:------|
|MissingParameter.InstanceIds|The input parameter InstanceIds that is mandatory for processing this request is missing.|400|The required InstanceIds parameter is missing.|
|MissingParameter.RegionId|The input parameter RegionId that is mandatory for processing this request is missing.|400|The required RegionId parameter is missing.|
|InvalidInstanceIds.Malformed|The specified InstanceIds is not valid.|400|The specified InstanceIds is invalid.|
|InvalidNetworkType.MismatchRamRole|Ram role cannot be attached to instances of Classic network type.|403|RAM roles cannot be attached to instances of Classic network type.|
|InvalidUser.PassRoleForbidden|The RAM user does not have the privilege to pass a RAM role.|403|Your RAM user account does not have PassRole permission. For more information, see  [Attach policies to a RAM user](../../../../intl.en-US/Quick Start/Attach policies to a RAM user.md#).|
|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|404|The specified InstanceIds does not exist.|
|InvalidRamRole.NotFound|The specified RamRoleName does not exist.|404|The specified RamRoleName does not exist.|

