# DetachDisk {#DetachDisk .reference}

Detaches a cloud disk from a specified instance. The disk category can be basic cloud disk, efficiency cloud disk, and cloud SSD disk.

## Description {#section_udt_fp5_xdb .section}

When you call this interface, consider the following:

-   The `Portable` attribute of the cloud disk must be `True`.
-   The status of the specified cloud disk must be **In Use** \(`In_Use`\).
-   The status of the specified instance must be **Running** \(`Running`\) or **Stopped** \(`Stopped`\).
-   If the specified instance is [locked](reseller.en-US/API Reference/Appendix/API behavior when an instance is locked for security reasons.md#), `OperationLocks` of the instance cannot be `"LockReason" : "security"`.
-   After a cloud disk is detached, the `DeleteWithInstance` attribute of the target cloud disk is automatically set to `false`.

-   The actions are asynchronous tasks, you may wait for a few minutes before the action is completed, and the duration is about one minutes.


## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DetachDisk.|
|InstanceId|String|Yes|The ID of the target ECS instance.|
|DiskId|String|Yes|The ID of the disk.|

## Response parameters {#section_c2t_fp5_xdb .section}

All are common response parameters. For more information, see [common parameters](reseller.en-US/API Reference/Getting started/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DetachDisk
&InstanceId=i-23jggx34b
&DiskId=d-23jbf2v5m
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<DetachDiskResponse>
    <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
</DetachDiskResponse>
```

 **JSON format** 

```
{
        "RequestId": "473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E"
}
```

## Error codes {#ErrorCode .section}

|Error code|Error message|HTTP status code|Meaning|
|:---------|:------------|:---------------|:------|
|MissingParameter|The input parameter InstanceId that is mandatory for processing this request is  not supplied.|400|You must specify a InstanceId.|
|DependencyViolation|The specified disk has not been attached on the specified instance.|403|The specified disk is not attached to the specified instance.|
|DiskNotPortable|The specified disk is not a portable disk.|403|The specified disk cannot be detached.|
|DiskTypeViolation|The specified disk is a system disk and cannot support the operation.|403|You cannot detach a system disk from your instance.|
|IncorrectDiskStatus|The current disk status does not support this operation.|403|The status of the specified cloud disk must be **In Use** \(`In_Use`\).|
|IncorrectInstanceStatus|The current status of the resource does not support this operation.|403|The status of the specified instance must be **Running** \(`Running`\) or **Stopped** \(`Stopped`\).|
|InstanceLockedForSecurity|The instance is locked due to security.|403|The specified instance is [locked](reseller.en-US/API Reference/Appendix/API behavior when an instance is locked for security reasons.md#) for the sake of security.|
|InvalidDiskId.Released|The specified disk has been released.|403|The specified disk has been released.|
|InvalidDiskId.NotFound|The specified DiskId does not exist.|404|The specified disk does not exist.|
|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|404|The specified disk does not exist.|

