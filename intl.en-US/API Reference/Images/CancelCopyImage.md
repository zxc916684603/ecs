# CancelCopyImage {#CancelCopyImage .reference}

Cancels a pending image copy \(CopyImage\) operation.

## Description {#section_qxx_22z_xdb .section}

When you call this interface, consider the following:

-   After you cancel the task, the destination image created in the target region is deleted, and the source image remains unchanged.

-   If the image copy process is completed, the action CancelCopyImage fails and an error returns.


## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: CancelCopyImage.|
|RegionId|String|Yes|ID of the region to where the source image belongs. You can call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|ImageId|String|Yes|ID of the source image that is being copied.|

## Response parameters {#section_wxx_22z_xdb .section}

All parameters are common response parameters. For more information, see [Common parameters](intl.en-US/API Reference/Call methods/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=CancelCopyImage
&RegionId=cn-hangzhou
&ImageId=img-2012-12-01-1300
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<CancelCopyImageResponse>
    <RequestId>C8B26B44-0189-443E-9816-D951F59623A9</RequestId>
</CancelCopyImageResponse>
```

 **JSON format** 

```

    "RequestId": "C8B26B44-0189-443E-9816-D951F59623A9"

```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more information, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message |HTTP status code|Meaning|
|:---------|:-------------|:---------------|:------|
|ImageCreatedNotFromCopy|The specified image is not the target image of a copy action.|400|The specified `ImageId` has no image copy task. Please try other images instead.|
|IncorrectImageStatus|The image has completed copy.|400|This action fails because the image copy task of the specified `ImageId` is already complete.|
|IncorrectImageStatus|The image is copied finished.|400|This action fails because the image copy task of the specified ImageId is already complete.|
|IncorrectImageStatus|The specified snapshot is not coping.|400|The status of the specified ImageId is incorrect.|
|IncorrectImageStatus|The specified image is not coping.|400|The status of the specified ImageId is incorrect.|
|IncorrectImageStatus|The Image copy has been failed.|400|The status of the specified ImageId is incorrect.|
|InvalidImageId.NotFound|The specified ImageId does not exist.|404|The specified ImageId does not exist.|
|InvalidRegionId.NotFound|The specified region does not exist.|404|The specified `RegionId` does not exist.|

