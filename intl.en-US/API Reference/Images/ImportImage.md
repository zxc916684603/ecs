# ImportImage {#ImportImage .reference}

Imports an on-premises image to Alibaba Cloud ECS.

## Description {#section_zj2_5wy_xdb .section}

You can use the imported image to create instances \([RunInstances](intl.en-US/API Reference/Instances/RunInstances.md#)\) or replace the system disk of an instance \([ReplaceSystemDisk](intl.en-US/API Reference/Disk/ReplaceSystemDisk.md#)\). When you call this interface, consider the following:

-   You must [upload the image file to OSS](../../../../intl.en-US/Quick Start/Upload an object.md#) beforehand.
-   You can only import an image file to a region from OSS in the same region. The image and OSS must belong to one account.
-   The n in `DiskDeviceMapping.n` indicates the disk type. When n is set to 1, it represents a system disk. When n is set to \[2, 17\], it represents a data disk.
-   You cannot delete an image that is being imported. However, you can cancel the image import task \([CancelTask](intl.en-US/API Reference/Others/CancelTask.md#)\).
-   To use [RAM](../../../../intl.en-US/Product Introduction/What is RAM.md#) to allow ECS to access OSS for your Alibaba Cloud account, follow these steps:
    1.  Create a role with a name `AliyunECSImageImportDefaultRole` \(**image import fails if a different name is used**\), and see the following code snippet to set its role policy.

        ```
        {
        "Statement": [
        {
        "Action": "sts:AssumeRole",
        "Effect": "Allow",
        "Principal": {
         "Service": [
           "ecs.aliyuncs.com"
         ]
        }
        }
        ],
        "Version": "1"
        }
        ```

    2.  Attach the default permission policy `AliyunECSImageImportRolePolicy` to AliyunECSImageImportDefaultRole. You can also create a custom policy with the following permissions:

        ```
        {
        "Version": "1",
        "Statement": [
        {
        "Action": [
         "oss:GetObject",
         "oss:GetBucketLocation"
        ],
        "Resource": "*",
        "Effect": "Allow"
        }
        ]
        }
        ```


## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: ImportImage.|
|RegionId|String|Yes|The region ID. You can call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|ImageName|String|No|The image name.-   Can be \[2, 128\] characters in length. Must start with an uppercase or lowercase English letter, or a Chinese character. Can contain digits, colons \(:\), underscores \(\_\), or hyphen \(-\).
-   The image name is displayed in the ECS console.
-   Cannot start with http:// or https://.

|
|Description|String|No|The image description.-   Can be null, but the image description is optional and but must not exceed 256 characters.
-   Cannot start with http:// or https://.

|
|Architecture|String|No|The system architecture. Optional values:-   i386
-   x86\_64

Default value: x86\_64.|
|OSType|String|No|The type of operating system platform. Optional values:-   Windows
-   Linux

Default value: Linux.|
|Platform|String|No|The operating system release edition. Optional values:-   CentOS
-   Ubuntu
-   SUSE
-   OpenSUSE
-   Debian
-   CoreOS
-   Aliyun
-   Windows Server 2003
-   Windows Server 2008
-   Windows Server 2012
-   Others Linux
-   Customized Linux

Default value: Others Linux.|
|DiskDeviceMapping.n.Format|String|No|The image format. Optional values:-   RAW
-   VHD
-   qcow2

After an image is imported, the image format is automatically checked and scanned. The result obtained from this process is used as the default value of this parameter.|
|DiskDeviceMapping.n.OSSBucket|String|Yes|The OSS bucket where an image file is stored.|
|DiskDeviceMapping.n.OSSObject|String|Yes|The name \(key\) of the OSS object with an image file.|
|DiskDeviceMapping.n.DiskImageSize|String|No|The size of a custom image. The space of the disk must be larger than or equal to the actual used space of disks. Value range:-   When n is set to 1: \[5, 500\] GiB.
-   When n is set to \[2, 16\]: \[5, 1000\] GiB.

When you import an image, the system auto scans and checks the size of the image, and the checking result is used as a default value of this parameter.|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|RegionId|String|The region ID.|
|ImageId|String|The image ID.|
|ImportTaskId|String|The ID of an image import task.|

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=ImportImage
&RegionId=cn-hangzhou
&DiskDeviceMapping.1.OSSBucket=ecsimageos
&DiskDeviceMapping.1.OSSObject=CentOS_5.4_32.raw
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<ImportImageResponse>
    <RequestId>C8B26B44-0189-443E-9816-D951F59623A9</RequestId>
    <ImageId>Img-231234567</ImageId>
    <ImportTaskId>123-345-2332-22323</ImportTaskId>
</ImportImageResponse>
```

 **JSON format** 

```
{
    "RequestId": "C8B26B44-0189-443E-9816-D951F59623A9",
    "ImageId": "Img-231234567"，
    "ImportTaskId":"123-345-2332-22323"
}
```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more information, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code|Meaning|
|:---------|:------------|:---------------|:------|
|Forbbiden|User not authorized to operate on the specified resource|400|You cannot import the image now.[Open a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex) to enable the image import feature.

|
|IncorrectImageStatus|The specified image is not available.|400|The status of the specified image is incorrect.|
|InvalidArchitecture.Malformed|The specified Architecture is wrongly formed.|400|The specified `Architecture` is invalid.|
|InvalidDescription.Malformed|The specified destination image description is wrongly formed.|400|The specified target image `Description` is invalid.|
|InvalidFormat.Malformed|The specified Image format is wrongly formed.|400|The specified image file format is invalid.|
|InvalidImageName.Duplicated|The destination image is exist.|400|The value of the specified ImageName already exists.|
|InvalidImageName.Malformed|The specified destination Image name is wrongly formed.|400|The specified `ImageName` is invalid.|
|InvalidImageSize|The specified “DiskDeviceMapping.n.DiskImageSize” should be not less than system device size.|400|The value of the specified `DiskDeviceMapping.n.DiskImageSize` must be larger than or equal to the actual used space of disks.|
|InvalidOSType.Malformed|The specified OSType is wrongly formed.|400|The specified `OSType` is invalid.|
|InvalidPlatform.Malformed|The specified Platform is wrongly formed.|400|The specified `Platform` is invalid.|
|MissingParameter|An input parameter “RegionId” that is mandatory for processing the request is not supplied.|400|You must specify the parameter `RegionId`.|
|MissingParameter|An input parameter “DiskDeviceMapping.n.OSSBucket” that is mandatory for processing the request is not supplied.|400|You must specify the parameter `OSSBucket`.|
|MissingParameter|An input parameter “DiskDeviceMapping.n.OSSObject” that is mandatory for processing the request is not supplied.|400|You must specify the parameter `OSSObject`.|
|RegionId.NotFound|The specified region is not found.|400|The `RegionId` of the specified image does not exist.|
|ImageIsImporting|The specified Image is importing.|403|The specified image is being copied. Please try again later.|
|InvalidRegion.NotSupport|The specified region does not support image import or export.|403|The specified region currently does not support image import.|
|QuotaExceed.Image|The Image Quota exceeds.|403|You have exceeded the custom images import limit. No more images can be imported.|
|QuotaExceed.Snapshot|The maximum number of snapshots is exceeded.|403|You have exceeded the snapshot import limit. No more images can be imported.|

