# DeleteSnapshot {#DeleteSnapshot .reference}

 Deletes a specified snapshot. Deletes a specified snapshot. If you want to cancel a snapshot creating task, you can call this interface. 

## Description {#section_j3f_mxz_xdb .section}

When you call this interface, consider the following:

-   If the specified SnapshotId does not exist, the request is ignored.

-   You cannot delete the snapshot if it has been used to create a custom image \(CreateImage\).  However, you can delete the appropriate custom image \([DeleteImage](intl.en-US/API Reference/Images/Deleteimage.md#)\) before you try the DeleteSnapshot action again.


## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DeleteSnapshot|
|SnapshotId|String|Yes|The snapshot ID.|

## Return parameters {#section_o3f_mxz_xdb .section}

All are common parameters. See [Common parameters](intl.en-US/API Reference/Call methods/Common parameters.md#commonResponseParameters).

## Example { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DeleteSnapshot
&SnapshotId=s-923FE2BF0
&<Common request parameters>
```

**Response sample** 

**XML format**

```
<DeleteSnapshotResponse>
     <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
</DeleteSnapshotResponse>
```

 **JSON format** 

```
{
    "RequestId": " CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
}
```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more error codes, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code|Note|
|:---------|:------------|:---------------|:---|
|MissingParameter|The input parameter SnapshotId that is mandatory for processing this request is not supplied.|400|You must specify the required parameter `SnapshotId`.|
|SnapshotCreatedDisk|The snapshot has been used to create disk\(s\).|403|The specified snapshot has already been used to create a disk.|
|SnapshotCreatedImage|The snapshot has been used to create user defined image\(s\).|403|The specified snapshot has been used to create a custom image. You need to first delete the custom mirrors that have been created.|

