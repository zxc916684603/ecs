# ModifyImageAttribute {#ModifyImageAttribute .reference}

Modifies the name and description of a custom image.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: ModifyImageAttribute.|
|RegionId|String|Yes| RegionId of the custom image. You can call [DescribeRegions](reseller.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|ImageId|String|Yes|The ID of the custom image.|
|ImageName|String|No|This parameter indicates the name of the custom image.-   Can be \[2, 128\] characters in length.
-   Must begin with an uppercase or lowercase English letter. Can contain digits, underscores \(\_\), colons \(:\), or hyphens \(-\).
-   Cannot begin with http:// or https://.

|
|Description|String|No|The Description of a custom image.-   Can be \[0, 256\] characters in length.
-   Cannot begin with http:// or https://.
-   Default value: null.

|

## Response parameters {#section_f54_lk5_xdb .section}

All parameters are common response parameters. For more information, see [Common parameters](reseller.en-US/API Reference/Getting started/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=ModifyImageAttribute
&ImageId=m-281234567
&RegionId=cn-qingdao
&ImageName=testImage123
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<ModifyImageAttributeResponse>
    <RequestId>C8B26B44-0189-443E-9816-D951F59623A9</RequestId>
</ModifyImageAttributeResponse>
```

 **JSON format** 

```
{
    "RequestId": "C8B26B44-0189-443E-9816-D951F59623A9"
}
```

## Error codes {#ErrorCode .section}

|Error code|Error message|HTTP status code|Meaning|
|:---------|:------------|:---------------|:------|
|InvalidDescription.Malformed|The specified description is incorrectly formed.|400|The specified `Description` is invalid.|
|InvalidImageName.Duplicated|The specified Image name has already bean used.|400|The specified `ImageName` already exists.|
|InvalidImageName.Malformed|The specified Image name is incorrectly formed.|400|The specified `ImageName` is invalid.|
|MissingParameter|The input parameter “RegionId” that is required for processing this request is not supplied.|400|You must specify the `RegionId` parameter.|
|InvalidImageId.NotFound|The specified ImageId does not exist.|403|The specified ImageId does not exist.|
|InvalidRegionId.NotFound|The specified region does not exist.|404|The specified `RegionId` does not exist.|

