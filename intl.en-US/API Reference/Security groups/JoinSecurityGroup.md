# JoinSecurityGroup {#JoinSecurityGroup .reference}

Adds an instance to a specified security group.

## Description {#section_xnq_ms1_ydb .section}

When you call this interface, consider the following:

-   Before joining a security group, the instance must be in the **Stopped** \(`Stopped`\) or **Running** \(`Running`\) status.

-   Each instance can join a maximum of five security groups.

-   Each security group can manage up to 1000 instances.

-   Your instance and security group must be in the same Alibaba Cloud region.

-   The network type of your instance and security group must be the same. And if their network type is [Virtual Private Cloud \(VPC\)](../../../../intl.en-US/VPC product introduction/What is VPC.md#), the security group and the instance must belong to the same VPC.


## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: JoinSecurityGroup.|
|InstanceId|String|Yes|The instance ID. You can call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain all your instance IDs.|
|SecurityGroupId|String|Yes|The security group ID. You can call [DescribeSecurityGroups](intl.en-US/API Reference/Security groups/DescribeSecurityGroups.md#) to obtain all your security group IDs.|

## Response parameters {#section_f54_lk5_xdb .section}

All parameters are common response parameters. For more information, see [Common parameters](intl.en-US/API Reference/Call methods/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=JoinSecurityGroup
&InstanceId= i-instance1
&SecurityGroupId=F876FF7BA984
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<JoinSecurityGroupResponse>
    <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
</JoinSecurityGroupResponse>
```

 **JSON format** 

```
{
    "RequestId": "473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E"
}
```

## Error codes {#ErrorCode .section}

The following error codes are specific to this interface. For more error codes, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code|Meaning|
|:---------|:------------|:---------------|:------|
|InvalidInstanceId.Mismatch|Specified instance and security group are not in the same VPC.|400|The security group and the instance must belong to the same VPC.|
|InstanceSecurityGroupLimitExceeded|Exceeding the allowed amount of security groups that an instance can be in.|400|An instance can join a maximum of 5 security groups.|
|MissingParameter|The input parameter “InstanceId” that is mandatory for processing this request is not supplied.|400|You must specify the `InstanceId` parameter.|
|MissingParameter|The input parameter “SecurityGroupId” that is mandatory for processing this request is not supplied.|400|You must specify the `SecurityGroupId` parameter.|
|IncorrectInstanceStatus|The current status of the resource does not support this operation.|403|Before joining a security group, the instance must be in the **Stopped** \(`Stopped`\) or **Running** \(`Running`\) status.|
|InstanceLockedForSecurity|The specified operation is denied as your instance is locked for security reasons.|403|Your request is denied as the specified instance is [locked](intl.en-US/API Reference/Appendix/API behavior when an instance is locked for security reasons.md#) for security reasons.|
|SecurityGroupInstanceLimitExceeded|The maximum number of instances in a security group is exceeded.|403|Each security group can manage up to 1000 instances.|
|InvalidInstanceId.AlreadyExists|The specified instance already exists in the specified security group.|403|The specified instance has joined the specified security group.|
|OperationDenied|The specified operation is denied as your instance is locked for security reasons.|403|Your request is denied as the specified instance is [locked](intl.en-US/API Reference/Appendix/API behavior when an instance is locked for security reasons.md#) for security reasons.|
|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|404|The specified `InstanceId` does not exist.|
|InvalidSecurityGroupId.NotFound|The specified SecurityGroupId does not exist.|404|The specified `SecurityGroupId` does not exist.|

