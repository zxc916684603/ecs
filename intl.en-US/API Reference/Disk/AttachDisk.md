# AttachDisk {#AttachDisk .reference}

Attaches a data disk to an instance.

## Description {#section_vgf_j45_xdb .section}

When you call this interface, consider the following:

-   The target instance must be in the **Running** \(`Running`\) or **Stopped** \(`Stopped`\).
-   The target cloud disk must be in the **Available** \(`Available`\) status.
-   The `OperationLocks` of the [locked](../reseller.en-US/API Reference/Appendix/API behavior when an instance is locked for security reasons.md#) instance cannot be `"LockReason" : "security"`.
-   Even if you set the `DeleteWithInstance` to `false` when attaching the cloud disk, once the instance is locked and the `OperationLocks` of the instance indicates `"LockReason": "security"`, when you release the instance, the `DeleteWithInstance` attribute of the cloud disk is ignored and the disk is released along with the instance.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: AttachDisk.|
|InstanceId|String|Yes|The ID of the target instance.|
|DiskId|String|Yes|Indicates the cloud disk ID. The cloud disk \(`DiskId`\) and instance \(`InstanceId`\) must be in the same zone.|
|DeleteWithInstance|Boolean|No|When the instance is released, whether the cloud disk is released along with the instance or retained. Default value: False.|

## Response parameters {#ResponseParameter .section}

All are common response parameters. See [Common response parameters](../reseller.en-US/API Reference/Getting started/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=AttachDisk
&InstanceId=i-23jggx34b
&DiskId=d-23jbf2v5m
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<AttachDiskResponse>
    <RequestId>473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E</RequestId>
</AttachDiskResponse>
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
|IncorrectInstanceStatus|The current status of the resource does not support this operation.|400|The target instance must be in the **Running** \(`Running`\) or **Stopped** \(`Stopped`\) status.|
|InvalidParameter|The input parameter is mandatory for processing thisrequest is empty.|400|The specified DeleteWithInstance is invalid.|
|DiskError|IncorrectDiskStatus.|403|The target disk must be in the **Available** \(`Available`\) status.|
|DiskId.ValueNotSupported|The specified parameter diskid is not supported.|403|The specified DiskId is not supported.|
|DiskInArrears|The specified operation is denied as your disk owing fee.|403|The specified instance has an outstanding payment.|
|DiskNotPortable|The specified disk is not a portable disk.|403|The specified disk cannot be detached.|
|IncorrectDiskStatus|The operation is not supported in this status.|403|The target disk must be in the **Available** \(`Available`\) status.|
|InstanceExpiredOrInArrears|The specified operation is denied as your prepay instance is expired \(prepay mode\) or in arrears \(afterpay mode\).|403|The specified instance has an outstanding payment.|
|InstanceLockedForSecurity|The instance is locked due to security.|403|The instance is locked for security reasons.|
|InvalidDevice.InUse|The specified device has been occupied.|403|The specified disk has already been attached to another instance.|
|ResourcesNotInSameZone|The specified instance and disk are not in the samezone.|403|The specified disk and instance are not in the same zone.|
|InvalidDiskId.NotFound|The specified disk does not exist.|404|The specified cloud disk does not exist.|
|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|404|The specified instance does not exist.|

