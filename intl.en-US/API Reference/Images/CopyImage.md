# CopyImage {#CopyImage .reference}

Copies a custom image from one region to other regions. You can use the destination image to create instances \([RunInstances](intl.en-US/API Reference/Instances/RunInstances.md#)\) or replace system disks \([ReplaceSystemDisk](intl.en-US/API Reference/Disk/ReplaceSystemDisk.md#)\). 

## Description {#section_mv5_ndz_xdb .section}

When you call this interface, consider the following:

-   You can only copy the custom image when it is in the `Available` status.

-   You can only copy the image within your Alibaba Cloud account. Coping a cross-account image is not allowed.

-   You cannot delete an image \([DeleteImage](intl.en-US/API Reference/Images/Deleteimage.md#)\) when copying is in progress. However, you can cancel the copying process \([CancelCopyImage](intl.en-US/API Reference/Images/CancelCopyImage.md#)\).


## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: CopyImage.|
|RegionId|String|Yes|ID of the region to where the source custom image belongs. You can call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|ImageId|String|Yes|ID of the source custom image.|
|DestinationRegionId|String|Yes|ID of the region to where the destination custom image belongs.|
|DestinationImageName|String|No|Name of the destination custom image.-   Can be \[2, 128\] characters in length. Must begin with an uppercase or lowercase English letter, or a Chinese character. Can contain digits, backslashes \(\\\), colons \(:\), underscores \(\_\), or hyphens \(-\).
-   Cannot begin with http:// or https://.

Default value: null.|
|DestinationDescription|String|No|The description of the destination custom image.-   Length is \[0,256\] characters.
-   Cannot begin with http:// or https://.

Can be null. Default value: null.|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|ImageId|String|ID of the destination custom image|

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=CopyImage
&DestinationRegionId=cn-hangzhou
&ImageId=m-281234567
&RegionId=cn-qingdao
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<CopyImageResponse>
    <RequestId>C8B26B44-0189-443E-9816-D951F59623A9</RequestId>
    <ImageId>Img-231234567</ImageId>
</CopyImageResponse>
```

 **JSON format** 

```
{
    "RequestId": "C8B26B44-0189-443E-9816-D951F59623A9",
    "ImageId": "Img-231234567"
}
```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more information, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message |HTTP status code|Meaning|
|:---------|:-------------|:---------------|:------|
|DestinationRegion.NotFound|The destination region not found|400|The RegionId of the specified source custom image \(`DestinationRegionId`\) does not exist.|
|IncorrectImageStatus|The image not available.|400|The status of the specified source custom image \(`ImageId`\) must be `Available`.|
|InvalidDescription.Malformed|The specified description is wrongly formed.|400|The description of the specified destination custom image \(`DestinationDescription`\) is invalid.|
|InvalidImageId.NotFound|The specified ImageId does not exist.|400|The specified source custom image \(`ImageId`\) does not exist.|
|InvalidImageName.Duplicated|The destination image is exist.|400|The name of the destination custom image \(`DestinationImageName`\) is already in use.|
|InvalidImageName.Malformed|The specified destination Image name is wrongly formed.|400|The name of the specified destination custom image \(`DestinationImageName`\) is invalid.|
|InvalidImageName.Malformed|The specified Image name is wrongly formed.|400|The format of `DestinationImageName` is incorrect.|
|SourceRegion.NotFound|The source region not found|400|The `RegionId` of the specified source custom image does not exist.|
|Forbidden|User not authorized to operate on the specified resource.|403|You are not authorized to copy images.|
|IncorrectDestinationRegion|The destination region is not equal the target region.|403|The source region for copying images \(`RegionId`\) must be different from the destination region \(`DestinationRegionId`\).|
|InvalidSnapshot.TooOld|This operation is denied because the specified snapshot is created before 2013-07-15.|403|The specified ImageId \(`ImageId`\) is created on or before July 15, 2013. Please try other images instead.|
|OperationDeined.EncryptedSnapshot|The image contains encrypted snapshots, which do not support copying.|403|The source custom image \(`ImageId`\) contains encrypted snapshots, which do not support copying.|
|OperationDenied.ImageCopying|The specified image is being copied.|403|The specified source custom image \(`ImageId`\) is being copied. Please try again later.|
|QuotaExceed.Image|The Image Quota exceeds.|403|No more images will be copied because you have exceeded your custom image quota.|
|QuotaExceed.Snapshot|The maximum number of snapshots is exceeded.|403|No more images will be copied because you have exceeded your snapshot quota.|
|RegionNotSupportCopy|The region not support copy.|403|The specified region of the destination image \(`DestinationRegionId`\) does not support image copying.|

