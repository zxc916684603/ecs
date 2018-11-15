# LeaveSecurityGroup {#LeaveSecurityGroup .reference}

Removes an instance from a specified security group.

## Description {#section_zp1_jt1_ydb .section}

When you call this interface, consider the following:

-   To remove an instance from the security group, it must be in the **Stopped** \(`Stopped`\) or **Running** \(`Running`\) status.

-   Each instance must belong to at least one security group. If the instance only belongs to one security group and you try to remove it from this group, the `LeaveSecurityGroup` request fails.


## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action |String|Yes|The name of this interface. Value: LeaveSecurityGroup.|
|InstanceId|String|Yes|The specified instance ID.|
|SecurityGroupId|String|Yes|The security group ID.|

## Response parameters {#section_f54_lk5_xdb .section}

All parameters are common response parameters. For more information, see [Common parameters](intl.en-US/API Reference/Call methods/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=LeaveSecurityGroup
&InstanceId=i-instance1
&SecurityGroupId=F876FF7BA984
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<LeaveSecurityGroupResponse>
    <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
</LeaveSecurityGroupResponse>
```

 **JSON format** 

```
{
    "RequestId": "473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E"
}
```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more information, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message |HTTP status code |Meaning|
|:---------|:-------------|:----------------|:------|
|IncorrectInstanceStatus|The current status of the resource does not support this operation.|403|Before being removed from a security group, the instance must be in the **Stopped** \(`Stopped`\) or **Running** \(`Running`\) status.|
|InstanceLastSecurityGroup|The specified security group is the last security group for the instance.|403|Each instance must belong to at least one security group.|
|InstanceLockedForSecurity|The specified operation is denied as your instance is locked for security reasons.|403|The specified instance is [locked](intl.en-US/API Reference/Appendix/API behavior when an instance is locked for security reasons.md#), and the `OperationLocks` of the instance cannot be `"LockReason" : "security"`.|
|InstanceNotInSecurityGroup|The instance not in the group.|403|The instance is not in the specified security group.|
|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|404|The specified `InstanceId` does not exist.|
|InvalidSecurityGroupId.NotFound|The specified SecurityGroupId does not exist.|404|The specified `SecurityGroupId` does not exist.|

