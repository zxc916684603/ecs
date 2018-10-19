# CreateLaunchTemplateVersion {#CreateLaunchTemplateVersion .reference}

Creates a version based on the specified instance launch template.

## Description {#section_hhw_wvn_12b .section}

You can create up to 30 versions of each instance launch template. Instead of a template modification API, we provide a version iteration API \(CreateLaunchTemplateVersion\) that allows you to modify the parameters in a template by creating a new version. For more information, see CreateLaunchTemplate.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: CreateLaunchTemplateVersion.|
|RegionId|String|Yes|Region ID of an instance. For more information, call [DescribeRegions](../reseller.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|LaunchTemplateId|String|Yes|Instance launch template ID. For more information, call [DescribeLaunchTemplates](reseller.en-US/API Reference/Launch templates/DescribeLaunchTemplates.md#). Either the `LaunchTemplateId` or the `LaunchTemplateName` must be specified to choose a template.|
|LaunchTemplateName|String|Yes|Instance launch template name.|
|VersionDescription|String|No|Description of instance launch template version. It cannot begin with http:// or https://.|
|ImageId|String|No|Image ID.|
|InstanceType|String|No|Instance type. For more information, call [Instance type families](../reseller.en-US/Product Introduction/Instance type families.md#) to obtain the latest instance type list.|
|SecurityGroupId|String|No|The security group ID.|
|NetworkType|String|No|Network type of the instance. Optional values: Classic | VPC.|
|VSwitchId|String|No|When creating a VPC-Connected instance, you must specify its VSwitch ID.|
|InstanceName|String|No|The name of the instance. The name is a string of 2 to 128 characters. It must begin with an English or a Chinese character. It can contain A-Z, a-z, Chinese characters, numbers, periods \(.\), colons \(:\), underscores \(\_\), and hyphens \(-\).|
|Description|String|No|Instance description.|
|InternetMaxBandwidthIn|String|No|The maximum inbound bandwidth from the internet network, measured in Mbit/s. Value range: \[1, 200\]. |
|InternetMaxBandwidthOut|String|No|The maximum outbound bandwidth to the internet network, measured in Mbit/s. Value range: \[0, 100\].|
|HostName|String|No|Instance host name.-   It cannot start or end with a period \(.\) or a hyphen \(-\) and it cannot have two or more consecutive periods \(.\) or hyphens \(-\).
-   For Windows: The host name can be \[2, 15\] characters in length. It can contain A-Z, a-z, numbers, periods \(.\), and hyphens \(-\). It cannot only contain numbers.
-   For other operating systems: The host name can be \[2, 64\] characters in length. It can be segments separated by periods \(.\). It can contain A-Z, a-z, numbers, and hyphens \(-\).

|
|ZoneId|String|No|The zone ID of the instance.|
|SystemDisk.Category|String|No|The category of the system disk. Optional values:-   Cloud: Basic cloud disk.
-   cloud\_efficiency: Ultra cloud disk.
-   cloud\_ssd: SSD Cloud Disks.
-   ephemeral\_ssd: Ephemeral SSD.

|
|SystemDisk.Size|Integer|No|The system disk size, in GiB. Value range: \[20, 500\].|
|SystemDisk.DiskName|String|No|System Disk name. It is a string of 2 to 128 English letters and special characters. It must start with an English letter. It can contain numbers, colons \(:\), periods \(.\), underscores \(\_\), and hyphens \(-\). It cannot start with "http://" or "https://".|
|SystemDisk.Description|String|No|System Disk description. Length: \[2, 256\] characters. It cannot start with "http://" or "https://".|
|DataDisk.n.Category|String|No|The data disk type. Value range of `n`: \[1, 16\]. Optional values:-   Cloud: Basic cloud disk.
-   cloud\_efficiency: Ultra cloud disk.
-   cloud\_ssd: SSD Cloud Disks.
-   ephemeral\_ssd: Ephemeral SSD.

|
|DataDisk.n.Size|Integer|No|The data disk capacity. Value range of `n`: \[1, 16\]. Value range:-   cloud: \[5, 2000\]
-   cloud\_efficiency: \[20, 32768\]
-   cloud\_ssd: \[20, 32768\]
-   ephemeral\_ssd: \[5, 800\]

|
|DataDisk.n.SnapshotId|String|No|The snapshot used to create the data disk. Value range of `n`: \[1, 16\].|
|DataDisk.n.Encrypted|Boolean|No|Whether the data disk is encrypted. Value range of `n`: \[1, 16\].|
|DataDisk.n.DiskName|String|No|The data disk name. Value range of `n`: \[1, 16\].|
|DataDisk.n.Description|String|No|The data disk description. Value range of `n`: \[1, 16\].|
|DataDisk.n.DeleteWithInstance|String|No|Whether the data disk is released with its instance. Value range of `n`: \[1, 16\].|
|IoOptimized|String|No|Whether it is an I/O-optimized instance or not. Optional values:-   none
-   optimized

|
|NetworkInterface.1.PrimaryIpAddress|String|No|The primary private IP address of ENI.|
|NetworkInterface.1.VSwitchId|String|No|The VSwitch ID for ENI. The instance must be in the same zone of the same VPC network as the ENI, but they may belong to different VSwitches.|
|NetworkInterface.1.SecurityGroupId|String|No|The security group ID of ENI. You must specify a security group in the same VPC network.|
|NetworkInterface.1.NetworkInterfaceName|String|No|The name of ENI. The name is a string of 2 to 128 characters. It must begin with an English or a Chinese character. It can contain A-Z, a-z, Chinese characters, numbers, periods \(.\), colons \(:\), underscores \(\_\), and hyphens \(-\).|
|NetworkInterface.1.Description|String|No|The description of ENI. It cannot begin with http:// or https://.|
|InternetChargeType|String|No|Internet bandwidth billing method. Value options: PayByTraffic|
|UserData|String|No|User data of the instance, which is Base64-encoded. Size of the raw data cannot exceed 16 KB.|
|KeyPairName|String|No|The name of the key pair.-   This parameter is valid only for a Linux instance. It is null by default. If a value is set for parameter KeyPairName, the `Password` still takes effect.
-   The user name and password authentication method is disabled if a value is set for parameter KeyPairName for a Linux instance.

|
|RamRoleName|String|No|The RAM role name of the instance. You can use the *RAM* API [ListRoles](../../../../../reseller.en-US/Developer Guide/API reference (RAM)/Role Management Interface/ListRoles.md#) to query instance RAM role names.|
|AutoReleaseTime|String|No|Instance auto release time. The time format follows the [ISO8601](../reseller.en-US/API Reference/Appendix/ISO 8601 Time Format.md#) standard, and the UTC time is used. The format is yyyy-MM-ddTHH:mm:ssZ.|
|SpotStrategy|String|No|The preemption strategy for Pay-As-You-Go \(PostPaid\) instances. This parameter is valid and mandatory only when `InstanceChargeType` is set to `PostPaid`. Optional values:-   NoSpot: Normal Pay-As-You-Go instance.
-   SpotWithPriceLimit: Sets the maximum price for a spot instance.
-   SpotAsPriceGo: The system automatically calculates the price. The maximum value is the Pay-As-You-Go price.

|
|SpotPriceLimit|Float|No|Sets the maximum hourly instance price. Supports up to three decimal places.|
|SecurityEnhancementStrategy|String|No|Whether or not to activate the security enhancement feature and install network security software free of charge. Optional values: Active | Deactive.|
|Tag.n.Key|String |No |This tag applies to instance, disk, security group, or image. The key of a tag of which n is from 1 to 20. Once you use this parameter, it cannot be a null string. It can be up to 64 characters in length. It cannot begin with "aliyun", "acs:", "http://", or "https://".|
|Tag.n.Value|String |No |This tag applies to instance, disk, security group, or image. The value of a tag of which n is a number from 1 to 20. Once you use this parameter, it can be a null string. It can be up to 128 characters in length. It cannot begin with "aliyun", "acs:", "http://", or "https://".|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|LaunchTemplateVersionNumber|Long|The launch instance template version number.|

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=CreateLaunchTemplateVersion
&RegionId=cn-hangzhou
&LaunchTemplateName=lt-name1
&InstanceType=ecs.cm4.6xlarge
&SecurityGroupId=sg-securitygroupid
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<CreateLaunchTemplateVersionResponse>
    <RequestId>04F0F334-1335-436C-A1D7-6C044FExxxxx</RequestId>
    <LaunchTemplateVersionNumber>2</LaunchTemplateVersionNumber>
</CreateLaunchTemplateVersionResponse>
```

**JSON format** 

```
{
    "RequestId": "04F0F334-1335-436C-A1D7-6C044FExxxxx",
    "LaunchTemplateVersionNumber": 2
}
```

## Error codes {#ErrorCode .section}

|Error code|Error messages|HTTP status code |Description|
|:---------|:-------------|:----------------|:----------|
|InvalidLaunchTemplate.NotFound|The specified LaunchTemplateId “\{0\}” LaunchTemplateName “\{1\}” is not found.|400|The specified `LaunchTemplateId` or `LaunchTemplateName` is not found.|
|MissingParameter|The input parameter “\{0\}” that is mandatory for processing this request is not supplied.|400|A required parameter is missing.|
|InvalidParameter|the parameter\(s\) “\{0\}” provided is\(are\) invalid.|400|The specified parameter is invalid.|
|InvalidDescription.Malformed|The specified parameter “VersionDescription” is not valid.|400|The specified `VersionDescription` is invalid.|
|InvalidUserData.SizeExceeded|The specified parameter UserData exceeds the size.|400|The raw `UserData` exceeds 16 KB.|
|InvalidUserData.Base64FormatInvalid|The specified parameter UserData must be base64 encoded.|400|`UserData` must be Base64-encoded.|
|LaunchTemplateVersionLimitExceed|The maximum number of template’s versions is exceeded.|403|You can create up to 30 versions of each instance launch template.|
|InnerServiceFailed|call inner service failed|403|An internal server error.|

