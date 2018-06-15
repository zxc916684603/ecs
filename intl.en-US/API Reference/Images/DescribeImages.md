# DescribeImages {#DescribeImages .reference}

Queries your available image.

## Description {#section_jgn_1fz_xdb .section}

When you call this interface, consider the following:

-   The displayed image resource list contains your custom images, public images provided by Alibaba Cloud, available images from the marketplace, and shared images from the other Alibaba Cloud users.

-   You can query images by pages. The result consists of the total number of available image resources and all the image resources on the current page. By default, 10 images are displayed per page.


## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DescribeImages.|
|RegionId|String|Yes|ID of the region to which an instance belongs. You can call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|ImageId|String|No|The image ID. You can specify multiple image IDs and separate these IDs with commas \(`,`\).|
|Status|String|No|The image status. Optional values:-   Creating: The image is being created.
-   Available: Available images.
-   UnAvailable: Unavailable images.
-   CreateFailed: Failed images.

Default value: Available supports obtaining multiple values. These values are separated with commas \(`,`\) .|
|SnapshotId|String|No|The ID of the snapshot used to create the image.|
|ImageName|String|No|The name of the image.|
|ImageOwnerAlias|String|No|The alias of the image owner. Optional value:-   system: Public images provided by Alibaba Cloud.
-   self: Your custom images.
-   others: Your images that are shared from other Alibaba Cloud users.
-   marketplace: Images provided by [marketplace vendors](https://market.aliyun.com/)[marketplace vendors](https://marketplace.alibabacloud.com/). You need to pay attention to the charging details of the cloud market image.

Default value: null. Null indicates that results of `system`, `self` and `others` are returned.|
|Usage|String|No|Queries whether the specified image is running on ECS instance or not. Optional values:-   instance: The image is running in an ECS instance.
-   none: The image is not in use.

|
|Tag.n.Key|String|No|The key of a tag. The value range of `n` is \[1, 5\]. If you query the images according to tags, the value of Tag.n.Key cannot be a null string.|
|Tag.n.Value|String|No|The value of a tag. The value range of `n` is \[1, 5\]. If you query the images according to tags, the value of Tag.n.Value can be a null string.|
|PageNumber|Integer|No|Page number of the instance status list. Start value: 1.Default value: 1.

|
|PageSize|Integer|No|Sets the number of lines per page for queries per page. Maximum value: 50.Default value: 10.

|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|RegionId|String|The region ID of the image.|
|TotalCount|Integer|The number of items on the list.|
|PageNumber|Integer|The current page.|
|PageSize|Integer|The number of items on the current page.|
| Images|Array|A collection composed of image information [ImageType](intl.en-US/API Reference/Data type/ImageType.md#) .|

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DescribeImages
&RegionId=cn-hangzhou
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<DescribeImagesResponse>
    <Images>
        <Image>
            <Architecture>i386</Architecture>
            <CreationTime>2014-07-22T09:53:44Z</CreationTime>
            <Description></Description>
            <DiskDeviceMappings>
                <DiskDeviceMapping>
                    <Device>/dev/xvda</Device>
                    <Size>20</Size>
                    <SnapshotId></SnapshotId>
                </DiskDeviceMapping>
            </DiskDeviceMappings>
            <ImageId>suse11sp3_64_20G_aliaegis_20150428.vhd</ImageId>            
            <ImageName>suse11sp3_64_20G_aliaegis_20150428.vhd</ImageName>
            <ImageOwnerAlias>system</ImageOwnerAlias>
            <ImageVersion>1.0</ImageVersion>
            <IsCopied>false</IsCopied>
            <IsSubscribed>false</IsSubscribed>
            <OSName>SUSE Linux Enterprise Server 11 SP3 64位</OSName>
            <ProductCode></ProductCode>
            <OSType>linux</OSType>
            <Platform>SUSE</Platform>
            <Progress>100</Progress>
            <Size>20</Size>
            <Status>Available</Status>
            <Usage>instance</Usage>
        </Image>
    </Images>
    <PageNumber>1</PageNumber>
    <PageSize>2</PageSize>
    <RegionId>cn-hangzhou</RegionId>
    <TotalCount>24</TotalCount>
    <RequestId>7871BB26-3002-4950-B2E6-98D333077EA5</RequestId>
</DescribeImagesResponse>
```

 **JSON format** 

```

  "Images": {
    "Image": [
      
        "Architecture": "x86_64",
        "CreationTime": "2015-05-06T09:01:32Z",
        "DiskDeviceMappings": {
          "DiskDeviceMapping": [
            
              "Device": "/dev/xvda",
              "Size": "20"
            
          
        
        "ImageId": "suse11sp3_64_20G_aliaegis_20150428.vhd",
        "ImageName": "suse11sp3_64_20G_aliaegis_20150428.vhd",
        "ImageOwnerAlias": "system",
        "ImageVersion": "1",
        "IsCopied": false,
        "IsSubscribed": false,
        "OSName": "SUSE Linux Enterprise Server 11 SP3 64bit",
        "OSType": "linux",
        "Platform": "SUSE",
        Progress: 100 ",
        "Size": 20,
        "Status": "Available",
        "Usage": "instance"
      
    
  
  "PageNumber": 1,
  "PageSize": 1,
  "RegionId": "cn-hangzhou",
  "RequestId": "49CBCED4-C9B9-4851-BEB5-8FB5E5169E30",
  "TotalCount": 24

```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more information, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message |HTTP status code |Meaning|
|:---------|:-------------|:----------------|:------|
|Invalidimageowneralias. valuenotsupported|The specified ImageOwnerAlias value is not supported.|400|Invalid `ImageOwnerAlias` value.|
|Invalidtag. Mismatch|The specified Tag.n.Key and Tag.n.Value are not match.|400|The key \(`Tag.n.Key`\) and value \(`Tag.n.Value`\) of the tag must be key-value matched.|
|InvalidTagCount|The specified tags are beyond the permitted range.|400|You can specify a maximum of five tags.|
|InvalidUsage|The specifed Usage is not valid|404|The specified `Usage` parameter is invalid.|

