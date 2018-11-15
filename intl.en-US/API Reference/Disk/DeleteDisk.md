# DeleteDisk {#DeleteDisk .reference}

Releases aPay-As-You-Go cloud disk when it is no longer in use.

## Description {#section_qfk_mm5_xdb .section}

When you call this interface, consider the following:

-   Your manual snapshot is retained in the console.

-   You can call [ModifyDiskAttribute](intl.en-US/API Reference/Disk/ModifyDiskAttribute.md#) to decide whether the automatic snapshots of your cloud disk is retained or released along with the disk. We recommend that you delete unnecessary snapshots to guarantee an enough snapshot data storage for periodical automatic snapshot policies.

-   When you release a specified cloud disk, the status of the disk must be **Available**.

-   If the specified cloud disk does not exist, your request is ignored.


## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DeleteDisk.|
|DiskId|String|Yes|The ID of the cloud disk to be released.|

## Response parameters {#section_f54_lk5_xdb .section}

All are common response parameters. For more information, see [Common parameters](intl.en-US/API Reference/Call methods/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DeleteDisk
&DiskId=d-23jbf2v5m
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<DeleteDiskResponse>
<RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
</DeleteDiskResponse>
```

 **JSON format** 

```
{
    "RequestId": "CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
}
```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more information, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code|Meaning|
|:---------|:------------|:---------------|:------|
|DiskCreatingSnapshot|The operation is denied due to a snapshot of the specified disk is not completed yet.|403|A snapshot of the specified cloud disk is being created. Please try again later.|
|DiskNotPortable|The specified disk is not a portable disk.|403|The disk cannot be detached.|
|DiskTypeViolation|The specified disk is a system disk and cannot support the operation.|403|The specified cloud disk is a system disk and cannot be released.|
|IncorrectDiskStatus|The current disk status does not support this operation.|403|The status of the cloud disk must be **Available**.|

