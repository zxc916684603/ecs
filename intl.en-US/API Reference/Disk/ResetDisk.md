# ResetDisk {#ResetDisk .reference}

Rolls back a disk to a specified disk state by using one of its disk snapshots.

## Description {#section_qfp_gty_xdb .section}

When you call this interface, consider the following:

-   The status of the disk must be **In Use** \(`In_Use`\).

-   The status of the ECS instance to which the specified disk is attached must be **Stopped** \(`Stopped`\).

-   The specified `SnapshotId` must be one of the disk \(`DiskId`\) history snapshots.

-   If the specified instance is [locked](reseller.en-US/API Reference/Appendix/API behavior when an instance is locked for security reasons.md#), the `OperationLocks` of the instance cannot be `"LockReason": "security"`.


## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: ResetDisk.|
|DiskId|String|Yes|ID of the specified disk device.|
|Snapshotid|String|Yes|The snapshot ID of the disk that is to be rolled back.|

## Response parameters {#section_yfp_gty_xdb .section}

All are common response parameters. For more information, see [common parameters](reseller.en-US/API Reference/Getting started/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=ResetDisk
&DiskId=d-23jbf2v5m
&SnapshotId=s-snapshot1
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<ResetDiskResponse>
    <RequestId>F3CD6886-D8D0-4FEE-B93E-1B73239673DE</RequestId>
</ResetDiskResponse>
```

 **JSON format** 

```
{
        "RequestId":"F3CD6886-D8D0-4FEE-B93E-1B73239673DE"
}
```

## Error codes {#ErrorCode .section}

|Error code|Error message|HTTP status code|Meaning|
|:---------|:------------|:---------------|:------|
|DiskCategory.OperationNotSupported| The operation is not supported to the specified disk due to its disk category.|400| The category of the specified disk does not support rolling back.|
|IncorrectDiskStatus| The current disk status does not support this operation.|403|The status of the disk must be **In Use** \(`In_Use`\).|
|IncorrectInstanceStatus|The current status of the resource does not support this operation.|403|The status of the ECS instance to which the specified is attached must be **Stopped** \(`Stopped`\).|
|InstanceExpiredOrInArrears| The specified operation is denied as your prepay instance is expired  \(prepay mode\) or in arrears \(afterpay mode\).|403|Your subscription instance has expired. Or your Pay-As-You-Go instance has an overdue payment.|
|InstanceLockedForSecurity|The instance is locked due to security.|403|Your instance has been [locked](reseller.en-US/API Reference/Appendix/API behavior when an instance is locked for security reasons.md#) for security reasons.|
|InvalidAccountStatus.NotEnoughBalance|Your account does not have enough balance.|403| You registered credit card is invalid. Or insufficient balance in your PayPal account.|
|InvalidAccountStatus.SnapshotServiceUnavailable|Snapshot service has not been opened yet.|403|You have not signed up for the snapshot service yet. Please visit the [ECS console](https://partners-intl.console.aliyun.com/#/ecs) to sign up and activate your account.|
|InvalidParameter.Mismatch| The specified snapshot is not created from the specified disk.|403|The specified SnapshotId must be one of the disk history snapshots.|
|InvalidSnapshot.TooOld|The snapshotId is created before 2013-07-15, it cannot be restored since the first time the disk detached.|403| The specified snapshot was created on or before July 15, 2013, and it cannot be used to roll back a disk.|
|InvalidSnapshotId.NotReady|The specified snapshot has not completed yet.|403|The specified snapshot is being created, please try again later.|
|OperationDenied|The specified snapshot does not support ResetDisk.|403|The specified snapshot cannot be used to roll back the disk.|
|InvalidDiskId.NotFound|The specified DiskId does not exist.|404|The specified disk does not exist.|
|InvalidSnapshotId.NotFound|The specified SnapshotId does not exist.|404|The specified disk does not exist.|

