# DescribeInstanceRamRole {#DescribeInstanceRamRole .reference}

Query information related to the [instance RAM role](../../../../intl.en-US/User Guide/Instances/Instance RAM roles/What is the RAM role of an instance.md#).

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DescribeInstanceRamRole|
|InstanceIds|String|Yes|Instance ID set. A maximum of 100 instances are supported, in the format of \["instanceId1", "instanceId2",  "instanceId3"…\].|
|RamRoleName|String|No|Queries all the ECS instances to which the specified RAM role is attached. You can use *RAM* API [ListRoles](../../../../intl.en-US//Role Management Interface/ListRoles.md#) to query your available instance RAM role.|

## Return parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|InstanceRamRoleSets|Array|Information set of Instance RAM role \([InstanceRamRoleSetType](intl.en-US/API Reference/Data type/InstanceRamRoleSetType.md#)\)|

## Example { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DescribeInstanceRamRole
&RegionId=cn-hangzhou
&InstanceIds=["i-instance1"]
&<Common request parameters>

```

**Response sample** 

**XML format**

```
<DescribeInstanceRamRoleResponse>
    <RequestId>8F4CAE3F-7892-4662-83A5-2C2FFD639553</RequestId>
    <InstanceRamRoleSets>
        <InstanceRamRoleSet>
             <InstanceId>i-instance1</InstanceId>
              <RamRoleName>RamRoleTest</RamRoleName>
        </InstanceRamRoleSet>
    </InstanceRamRoleSets>
    <TotalCount>1</TotalCount>
</DescribeInstanceRamRoleResponse>
```

 **JSON format** 

```
{
    "RequestId": "8F4CAE3F-7892-4662-83A5-2C2FFD639553",
    "InstanceRamRoleSets": {
        "InstanceRamRoleSet": [
            {
                "InstanceId": "i-instance1",
                "RamRoleName": "RamRoleTest"
            }
        ]
    },
    "TotalCount": 1
}
```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more error codes, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code|Note|
|:---------|:------------|:---------------|:---|
|InvalidInstanceIds.Malformed|The specified InstanceIds is not valid.|400|The specified `InstanceIds` are not valid.|
|InvalidNetworkType.MismatchRamRole|The Ram role cannot be attached to instances of Classic network type.|403|RAM roles cannot be attached to `InstanceIds` of Classic network type. Ram role cannot be attached to instances of Classic network.|
|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|404|The specified InstanceIds does not exist.|
|InvalidRamRole.NotFound|The specified RamRoleName does not exist.|404|The specified `RamRoleName` does not exist.|

