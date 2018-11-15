# ReInitDisk {#ReInitDisk .reference}

Initializes a cloud disk to the initial state.

## Description {#section_rff_nsy_xdb .section}

When you call this interface, consider the following.

-   The status of the disk must be **In Use** \(`In_use`\) and the status of corresponding instance to which the disk is attached must be **Stopped** \(`Stopped`\).

-   After you create an instance, if you have not activated it yet, you cannot initialize its attached disk.

-   A system disk will be initialized to the initial state of the image. If the source image used to create the disk is deleted, initialization fails.

-   A independently created data disk will be initialized to the empty disk state.

-   A data disk that is created by using a snapshot will be initialized to the snapshot state. If the source image used to create the disk is deleted, initialization fails and an error is returned.


## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: ReInitDisk.|
|DiskId|String|Yes|The ID of the disk device.|
|SecurityEnhancementStrategy|String|No|Whether to activate the security enhancement feature and install network security software or not. Optional values:-   Active: Enable the security enhancement feature and install free network security software. Only applicable to the Alibaba Cloud public images.
-   Deactive: Disable the security enhancement feature and no network security software installation. Applicable to all kinds of images.

|

## Response parameters {#section_zff_nsy_xdb .section}

All are common response parameters. For more information, see [Common parameters](intl.en-US/API Reference/Call methods/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=ReInitDisk
&DiskId=d-23jbf2v5m
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<ReInitDiskResponse>
    <RequestId>F3CD6886-D8D0-4FEE-B93E-1B73239673DE</RequestId>
</ReInitDiskResponse>
```

 **JSON format** 

```

    "RequestId":"F3CD6886-D8D0-4FEE-B93E-1B73239673DE"

```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more information, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code|Meaning|
|:---------|:------------|:---------------|:------|
|DiskCategory.OperationNotSupported|The operation is not supported to the specified disk due to its disk category.|400|The operation is denied due the category of the disk.|
|DiskCreatingSnapshot|The operation is denied due to a snapshot of the specified disk is not completed yet.|403|A snapshot is being created for the specified disk, please try again later.|
|IncorrectDiskStatus|The current disk status does not support this operation.|403|The status of the specified disk must be  **In Use** \(`In_use`\).|
|IncorrectInstanceStatus|The current status of the resource does not support this operation.|403|The status of the specified instance must be **Stopped** \(`Stopped`\).|
|InstanceExpiredOrInArrears|The specified operation is denied as your prepay instance is expired \(prepay mode\) or in arrears \(afterpay mode\).|403|The instance to which the specified disk is attached is halted and has an outstanding payment.|
|InstanceLockedForSecurity|The instance is locked due to security.|403|The specified disk has been [locked](intl.en-US/API Reference/Appendix/API behavior when an instance is locked for security reasons.md#) for the sake of security.|
|InvalidSnapshot.TooOld|The disk is created from a snapshotId made before 2013-07-15, it cannot be re-initiated the specified disk any more since the detached first time.|403|The specified disk was created on or before July 15, 2013, and you cannot initialize the disk consequently.|
|InvalidSourceSnapshot|The snapshot which is used to create the specified disk has been deleted.|403|The snapshot by which the specified disk is created has been deleted, and you cannot initialize the disk consequently.|
|OperationDenied|The snapshot which is used to create the specified disk has been deleted.|403|The snapshot by which the specified disk is created has been deleted, and you cannot initialize the disk consequently.|
|SharedImageDeleted|The specified image by others shared is deleted.|403|The shared image by which the specified disk is created has been deleted, and you cannot initialize the disk consequently.|
|InvalidDiskId.NotFound|The specified disk does not exist.|404|The specified disk does not exist.|

