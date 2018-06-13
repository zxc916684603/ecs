# RunInstances {#RunInstances .reference}

Creates a specified number of Pay-As-You-Go instances.

## Description {#section_qpz_vk5_ydb .section}

You can call [DescribeAvailableResource](intl.en-US/API Reference/Others/DescribeAvailableResource.md#) to view the available resources in a specified region.

You must maintain a sufficient balance in your linked credit card or PayPal account to complete the payment or preauthorization. For more information, see [Pay-As-You-Go](../../../../intl.en-US/Pricing/Pay-As-You-Go.md#).

When you call this interface, consider the following:

-   You can create a maximum number of 100 instances each time.

-   You can set the release time for the instances by specifying the parameter `AutoReleaseTime` in your request.

-   You can call [DescribeInstances](intl.en-US/API Reference/Instances/DescribeInstances.md#) to check the status of your instance.

-   Make sure you have created a security group. For more information, see [CreateSecurityGroup](intl.en-US/API Reference/Security groups/CreateSecurityGroup.md#).

-   After a successful request, the instances that are created by you start automatically. An instance is ready to use when it is in the `Running` status.

-   Before creating a VPC-Connected instance, you must [Create a VPC](../../../../intl.en-US/Quick Start/Create a VPC.md#). We can create a default VPC and VSwitch for you if needed.

-   Unlike [CreateInstance](intl.en-US/API Reference/Instances/CreateInstance.md#), instances created by calling the `RunInstances` method have Internet IPs allocated if you set the value of `InternetMaxBandwidthOut` greater than 0.

-   If invalid parameters or stock shortage happens, the RunInstances action fails. For troubleshooting, see [Error codes](#ErrorCode).


## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: RunInstances.|
|RegionId|String|Yes |The region ID. For more information, call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|ZoneId |String|No|The zone ID that is available in the specified region. You can call [DescribeZones](intl.en-US/API Reference/Regions/DescribeZones.md#) to obtain the latest zone list.Default value:

Randomly chosen by Alibaba Cloud ECS.

|
|ImageId|String|Yes|The image ID. You can call [DescribeImages](intl.en-US/API Reference/Regions/DescribeZones.md#) to obtain the available image list.|
|InstanceType|String|Yes|The instance type. For more information about available value, see [Instance type families](../../../../intl.en-US/Product Introduction/Instance type families.md#) or call [DescribeInstanceTypes](intl.en-US/API Reference/Instances/DescribeInstanceTypes.md#) to query the latest instance type list|
|SecurityGroupId|String|Yes|The security group to which the instances belongs. For more information, see DescribeSecurityGroups.|
|InternetChargeType|String|No|The billing method of the network bandwidth. Optional values:-   PayByBandwidth
-   PayByTraffic

Default: PayByTraffic.|
|IoOptimized|String|No |Whether it is an I/O-optimized instance or not. Optional values:-   one
-   optimized

If you set `InstanceType` as one of the [Phased-out instance types](https://www.alibabacloud.com/help/faq-detail/55263.htm), the default value is none.

`InstanceType` the default value is optimized.

|
|SystemDisk.Category|String|No |The category of the system disk. Optional values:-   cloud: Basic Cloud Disk.
-   cloud\_efficiency: Ultra Cloud Disk.
-   cloud\_ssd: SSD Cloud Disk.
-   ephemeral\_ssd: Ephemeral SSD.

If you set `InstanceType` as one of the [phased out instance types](https://www.alibabacloud.com/help/faq-detail/55263.htm) and set the `IoOptimized` to `none`, the default value is cloud.

Otherwise, the default value is cloud\_efficiency.

|
|SystemDisk.Size|String|No|The size of the system disk, measured in GB. Value range: \[20, 500\].It must be equal to or greater than the max\{20, the size of the specified image\}. Default value: max\{40, the size of the specified image\}.

|
|SystemDisk.DiskName|String|No |Name of the system disk.-   The instance name is a string of \[2, 128\] characters in length. It can contain digits, underscores \(\_\), colons \(:\), or hyphens \(-\), and must begin with an English or a Chinese character.
-   It cannot begin with `http://` or `https://`.
-   Default value: null.

|
|SystemDisk.Description|String|No |Description of a system disk.-   It can be \[2, 256\] characters in length.
-   It cannot begin with `http://` or `https://`.
-   Default value: null.

|
|DataDisk.n.Category|String|No |Category of the data disk n. The valid range of `n` is \[1, 16\]. Optional values:-   cloud: Basic Cloud Disk.
-   cloud\_efficiency: Ultra Cloud Disk.
-   cloud\_ssd: SSD Cloud Disk.
-   ephemeral\_ssd: Ephemeral SSD.

Default value: cloud.|
|DataDisk.n.Size|Integer|No |Size of the n data disk in GB. The valid range of `n` is \[1, 16\]. Optional values: -   cloud: \[5, 2000\]
-   cloud\_efficiency: \[20, 32768\]
-   cloud\_ssd: \[20, 32768\]
-   ephemeral\_ssd: \[5, 800\]

The value must be equal to or greater than the specific snapshot.|
|DataDisk.n.SnapshotId|String|No |Snapshot is used to create the data disk. The valid range of `n` is \[1, 16\]. After the `DataDisk.n.SnapshotId` is specified, parameter `DataDisk.n.Size` is ignored, and the size of the new disk is the size of the specified snapshot. If the specified snapshot was created on or before July 15, 2013, your request is denied, and an error InvalidSnapshot.TooOld is returned.|
|DataDisk.n.Encrypted|String|No |Whether the data disk is encrypted or not. The valid range of `n` is \[1, 16\]. Optional values:-   true: Encrypted.
-   false: Not encrypted.

Default: false.|
|DataDisk.n.DiskName|String|No |The data disk name. Value range of `n`: \[ 1,16\].-   It can contain \[2, 128\] characters in length. It can contain digits, underscores \(\_\), colons \(:\), or hyphens \(-\), and must begin with an English or a Chinese character.
-   Cannot begin with http:// or https://.
-   Default value: null.

|
|DataDisk.n.Description|String|No |Description of a data disk. The valid range of `n` is \[1, 16\].-   It can be \[2, 256\] characters in length.
-   Cannot begin with http:// or https://.
-   Default value: null.

|
|DataDisk.n.DeleteWithInstance|Boolean|No |Whether a data disk is released along with the instance or not. The valid range of `n` is \[1, 16\]. Optional values:-   true: The disk is released with the instance.
-   false: The disk is not released with the instance.

Default value: true. This parameter is only valid for an independent cloud disk, and the value of parameter `DataDisk.n.Category` is `cloud`, `cloud_efficiency`, or `cloud_ssd`. If you specify a value to DataDisk.n.DeleteWithInstance for ephemeral\_ssd, an error is returned.|
|HpcClusterId|String|No|The cluster ID to which the instance belongs.|
|VSwitchId|String|No |The virtual switch \(VSwitch\) ID. It must be specified when you create a VPC-Connected instance.|
|InternetMaxBandwidthIn|Integer|No|Maximum inbound bandwidth from the Internet, its unit of measurement is Mbit/s. Value range: \[1, 100\]. Default value: 100.|
|InternetMaxBandwidthOut|Integer|No |Maximum outbound bandwidth from the Internet, its unit of measurement is Mbit/s. Value range:-   \[0, 100\].

Default value: 0.

|
|InstanceName|String|No |Name of an ECS instance.-   It can be \[2, 128\] characters in length. It must begin with an English or a Chinese character. Can contain digits, periods \(.\), colons \(:\), underscores \(\_\), and hyphens \(-\). Cannot begin with http:// or https://.
-   If this parameter is not specified, the default value is the InstanceId of the instance. the default value is the  `InstanceId` of the instance.
-   You cannot start with http: // and https.

|
|HostName|String|No |Host name of the ECS instance.-   It cannot start or end with a period \(.\) or a hyphen \(-\). It cannot have two or more consecutive periods \(.\) or hyphens \(-\).
-   For  **Windows**: The host name can be \[2, 15\] characters in length. Can contain uppercase or lowercase letters, digits, periods \(.\), and hyphens \(-\). Cannot be digits only.
-   For other OSs, such as **Linux**: The host name can be \[2, 128\] characters in length. Can be segments separated by periods \(.\). Can contain uppercase or lowercase letters, digits, and hyphens \(-\).

|
|Description|String|No|Description of an ECS instance.-   It can be \[2, 256\] characters in length.
-   Default value: null.
-   Cannot begin with http:// or https://.

|
|Password|String|No|Password of the ECS instance.-   It can be \[8, 30\] characters in length. Must contain uppercase and lowercase letters, digits, and special characters,
-   such as \( \) \` ~ !  @ \# $ % ^ & \* - + = | \{ \} \[ \] : ; ‘ < \> , . ? /

If you specify a value for parameter `Password`, use HTTPS to call the API to avoid data breach.|
|PasswordInherit|Boolean |No|Whether to use the password pre-configured in the image you select or not. When PasswordInherit is specified, the `Password` must be null. For a secure access, make sure that the selected image has password configured.|
|Amount|String|No|The specified number of instances you want to create. Value range: \[1, 100\]. Default value: 1.|
|AutoReleaseTime|String|No|The automatic release time for the specified instances. The time display uses the [ISO8601](intl.en-US/API Reference/Appendix/ISO 8601 Time Format.md#) standard and in UTC time. The format is YYYY-MM-DDTHH:mm:ssZ.-   If the seconds \(ss\) place is not 00, it is automatically set to start from the current minute \(mm\).
-   It must be at least half an hour later than the current time.
-   It must be less than three years from the current time.

|
|UserData|String|No|The user data of an instance. It must be encoded in Base64 format. The maximum size of the user data is 16 KB.|
|KeyPairName|String|No|Key pair name. This parameter is valid only for a Linux instance.-    **For a Windows ECS instance**, if a value is set for parameter KeyPairName, the Password is still effective. It is null by default.  the `Password` is still effective.
-   The username and password authentication method is disabled if a value is set for parameter KeyPairName for a **Linux instance**.

|
|RamRoleName|String|No|Instance RAM role name. The name is provided and maintained by *RAM* and can be queried using [ListRoles](../../../../intl.en-US//Role Management Interface/ListRoles.md#). For more information, see [CreateRole](../../../../intl.en-US//Role Management Interface/CreateRole.md#) and [ListRoles](../../../../intl.en-US//Role Management Interface/ListRoles.md#).|
|SecurityEnhancementStrategy|String|No|Whether or not to activate the security enhancement feature and install network security software for free of charge. Optional values:-   Active: Enables the security enhancement feature and installs a free network security software. Only applicable to the Alibaba Cloud public images.
-   Deactive: Disables the security enhancement feature and no network security software is installed. Applicable to all kinds of images.

|
|Tag.n.Key|String|No|The key of a tag,  of which n is from 1 to 5. Once you use this parameter, it cannot be a null string. It can be up to 64 characters in length. It cannot begin with aliyun, acs, http://, or https://.|
|Tag.n.Value|String|No|The value of a tag of which n is from 1 to 5. Once you use this parameter, it can be a null string.  It can be up to 128 characters in length and cannot begin with aliyun, acs, http://, or https://.|
|SpotStrategy|String|No|The spot strategy of a spot instance. This parameter is valid and required only when `InstanceChargeType` is set to `PostPaid`. Optional values:-   NoSpot: A regular Pay-As-You-Go instance.
-   SpotWithPriceLimit: A price threshold for a spot instance.
-   SpotAsPriceGo: A price that is based on the highest Pay-As-You-Go instance.

Default value: NoSpot.|
|SpotPriceLimit|Float|No|Sets the hourly price threshold of an instance. Three decimals are allowed at most. It is effective only when parameter `SpotStrategy` is `SpotWithPriceLimit`.|
|ClientToken|String|\\No|Used to guarantee the idempotence of the request. The value is generated by a client. It must be unique among all requests and contains a maximum of 64 ASCII characters. For more information, see [How to ensure idempotence](intl.en-US/API Reference/Appendix/How to ensure idempotence.md#).|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|InstanceIdSets|[InstanceIdSet](#InstanceIdSet)|The list of instance IDs.|

**InstanceIdSet**

|Name|Type|Description|
|:---|:---|:----------|
|InstanceId|String|ID of the ECS instance. It is a unique identifier of the ECS instance.|

## Example { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=RunInstances
&RegionId=cn-hangzhou
&InstanceType=ecs.cm4.6xlarge
&SecurityGroupId=sg-securitygroupid
&Amount=3
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<RunInstancesResponse>
    <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
    <InstanceIdSets>
        <InstanceIdSet>
            <InstanceId>i-instanceid1</InstanceId>
            <InstanceId>i-instanceid2</InstanceId>
            <InstanceId>i-instanceid3</InstanceId>
        </InstanceIdSet>
    </InstanceIdSets>
</RunInstancesResponse>
```

 **JSON format** 

```
{
    "InstanceIdSets": {
        "InstanceIdSet": [
            "i-instanceid1",
            "i-instanceid2",
            "i-instanceid3"
        ]
    },
    "RequestId": "04F0F334-1335-436C-A1D7-6C044FE73368"
}
```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more information, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code |Description|
|:---------|:------------|:----------------|:----------|
|Account.Arrearage|Your account has an outstanding payment.|400|Your account has an overdue payment.|
|EncryptedOption.Conflict|Encryption value of disk and snapshot conflict.|400|Whether or not both the specified data disk and the specified snapshot must be encrypted simultaneously.|
|IncorrectVSwitchStatus|The current status of virtual switch does not support this operation.|400|The status of the specified VSwitch does not support the operation.|
|InstanceDiskCategoryLimitExceed|The specified DataDisk.n.Size beyond the permitted range, or the capacity of snapshot exceeds the size limit of the specified disk category.|400|The specified DataDisk.n.Size exceeds the maximum size of the specified disk category.|
|InstanceDiskNumber.LimitExceed|The total number of specified disk in an instance exceeds.|400|The number of data disks attached to an instance has exceeded 16.|
|InvalidDataDiskSize.ValueNotSupported|The specified DataDisk.n.Size beyond the permitted range, or the capacity of snapshot exceeds the size limit of the specified disk category.|400 |The specified `DataDisk.n.Size` is invalid or exceeds the maximum size of the specified disk category.|
|InvalidDescription.Malformed|The specified parameter Description is not valid.|400|The specified Description is invalid.|
|InvalidDiskCategory.ValueNotSupported|The specified parameter DiskCategory is not valid.|400| The specified DiskCategory is invalid.|
|InvalidDiskDescription.Malformed|The specified parameter SystemDisk.DiskDescription or DataDisk.n.Description is not valid.|400|The specified `SystemDisk.DiskDescription` or `DataDisk.n.Description` is invalid.|
|InvalidDiskName.Malformed|The specified parameter SystemDisk.DiskName or DataDisk.n.DiskName is not valid.|400|The specified `SystemDisk.DiskName` or `DataDisk.n.DiskName` is invalid.|
|InvalidHostName.Malformed|The specified parameter HostName is not valid.|400|The specified `HostName` is invalid.|
|InvalidInstanceName.Malformed|The specified parameter InstanceName is not valid.|400|The specified `InstanceName` is invalid.|
| Invalidinstancetype. valuenotsupported|The specified InstanceType beyond the permitted range.|400|The specified `InstanceType` is invalid or does not exist.|
|InvalidInstanceType.ValueUnauthorized|The specified InstanceType is not authorized.|400|The specified `InstanceType` is not authorized for use.|
|InvalidInternetChargeType.ValueNotSupported|The specified InternetChargeType is not valid.|400|The specified `InternetChargeType` does not exist.|
|InvalidIoOptimizedValue.ValueNotSupported|IoOptimized value not supported.|400|The specified `IoOptimized` is invalid or does not exist.|
|InvalidNetworkType.Mismatch|Specified parameter InternetMaxBandwidthIn or InternetMaxBandwidthOut conflict with instance network type.|400|The specified `InternetMaxBandwidthIn` or `InternetMaxBandwidthOut` does not match the network type of the instance.|
|InvalidNetworkType.Mismatch|Specified parameter InternetChargeType conflict with instance network type.|400|The specified `InternetChargeType` is invalid for the network type of the instance.|
|InvalidParameter|The specified parameter InternetMaxBandwidthOut is not valid.|400|The specified `InternetMaxBandwidthOut` is invalid.|
|InvalidParameter|The specified instance bandwidth is not valid.|400|The specified range of bandwidth is invalid.|
|InvalidParameter|The specified parameter Amount is not valid.|400|The specified `Amount` is invalid.|
|InvalidParameter.Bandwidth|The specified parameter Bandwidth is not valid.|400|The specified bandwidth is invalid.|
|InvalidParameter.Conflict|The specified image does not support the specified instance type.|400|You cannot use the specified image to create an ECS instance of the specified instance type.|
|InvalidParameter.Encrypted.KmsNotEnabled|The encrypted disk need enable KMS.|400|You have not enabled the Key Management Service \(KMS\) service.|
|InvalidParameter.EncryptedIllegal|The value of parameter Encrypted is illegal.|400|The specified `DataDisk.n.Encrypted` is invalid.|
|InvalidParameter.EncryptedNotSupported|Encrypted disk is not support in this region.|400|You cannot encrypt the data disk in the specified region.|
|InvalidParameter.EncryptedNotSupported|Corresponding data disk category does not support encryption.|400|You cannot encrypt the data disk of the specified DataDisk.n.Category.|
|InvalidParameter.Mismatch|Specified security group and virtual switch are not in the same VPC.|400|Both the specified security group and the specified VSwitch must be in the same VPC.|
|InvalidParameter.Mismatch|Specified virtual switch is not in the specified zone.|400|The specified VSwitch is not in the specified zone.|
|InvalidPassword.Malformed|The specified parameter Password is not valid.|400|The specified `Password` is invalid.|
|InvalidPasswordParam.Mismatch|The input password should be null when passwdInherit is true.|400|When `PasswordInherit` is specified, the  `Password` must be null.|
|InvalidSnapshotId.BasedSnapshotTooOld|The specified snapshot is created before 2013-07-15.|400|The specified DataDisk.n.SnapshotId must be created after July 15, 2013.|
|InvalidSpotAliUid|The specified UID is not authorized to use SPOT instance.|400|You are not authorized to purchase a spot instance.|
|InvalidSpotAuthorized|The specified Spot param is unauthorized.|400|You cannot create a spot instance.|
|InvalidSpotPrepaid|The specified Spot type is not support PrePay Instance.|400|Only the billing method Pay-As-You-Go is applicable for creating spot instances.|
|InvalidSpotPriceLimit|The specified SpotPriceLimitis not valid.|400|The parameter `SpotPriceLimit` is invalid.|
|InvalidSpotPriceLimit.LowerThanPublicPrice|The specified parameter spotPriceLimit can’t be lower than current public price.|400|The specified `spotPriceLimit` must be equal to or greater than the official price of the specified instance.|
|InvalidSpotStrategy|The specified SpotStrategy is not valid.|400|The parameter `SpotStrategy` is invalid.|
|InvalidSystemDiskCategory.ValueNotSupported|The specified parameter SystemDisk.Category is not valid.|400|The specified `SystemDisk.Category` is invalid.|
|InvalidUserData.NotSupported|The specified parameter UserData only support the vpc and IoOptimized Instance.|400|You can only specify `UserData` for I/O optimized VPC-Connected instances.|
|InvalidUserData.SizeExceeded|The specified parameter UserData exceeds the size.|400|The size of the `UserData` before the Base64 encoding has exceeded 16 KB.|
|InvalidHpcClusterId.NotFound|The specified HpcClusterId is not found.|400|The specified `HpcClusterId` does not exist.|
|InvalidHpcClusterId.Creating|The specified HpcClusterId is creating.|400|The specified `HpcClusterId` is being created. Please try again later.|
|InvalidHpcClusterId.Unnecessary|The specified HpcClusterId is unnecessary.|400|You can specify the only for some `InstanceType`.|
|InvalidVSwitchId.Necessary|The HpcClusterId is necessary.|400|To cluster for the specified `InstanceType`, you must specify the `HpcClusterId`.|
|MissingParameter|The input parameter VSwitchId that is mandatory for processing this request is not supplied.|400|The `VSwitchId` parameter is required.|
|QuotaExceed.AfterpayInstance|The maximum number of Pay-As-You-Go instances is exceeded.|400|You have exceeded the maximum number of Pay-As-You-Go instances. For more information, see [Limits](../../../../intl.en-US/User Guide/Limits.md#).|
|QuotaExceeded|Living instances quota exceeded in this VPC.|400|The number of instances in the specified VPC has reached the upper limit.|
|ResourceNotAvailable|Resource you requested is not available in this region or zone.|400|The resource you requested is unavailable in the specified RegionId or ZoneId. Please try again in other regions or zones.|
|CategoryNotSupported|The specified zone does not offer the specified disk category.|403|You cannot create a disk of the specified disk category in the specified zone.|
|DeleteWithInstance.Conflict|The specified disk is not a portable disk and cannot be set to DeleteWithInstance attribute.|403|You cannot specify `DeleteWithInstance` to true for the specified disk.|
|DependencyViolation.WindowsInstance|The instance creating is window, cannot use ssh key pair to login.|403|Parameter KeyPairName is valid only for a Linux instance.|
|Forbidden|User not authorized to operate on the specified resource.|403|You are not authorized to create the specified resource.|
|ImageNotSubscribed|The specified image has not be subscribed.|403|The specified image is from the marketplace. You must subscribe it in advance.|
|ImageNotSupportInstanceType|The specified image don’t support the InstanceType instance.|403|The specified image does not support the instance type.|
|ImageRemovedInMarket|The specified market image is not available, or the specified custom image includes product code because it is based on an image subscribed from marketplace, and that image in marketplace including exact the same product code has been removed.|403|The specified image on the marketplace is unavailable. Or the `product-code` in the marketplace of the specified custom image has been removed.|
|InstanceDiskCategoryLimitExceed|The total size of specified disk category in an instance exceeds.|403|The specified disk category exceeds the maximum capacity of a single instance.|
|InstanceDiskNumLimitExceed|The number of specified disk in an instance exceeds.|403|The number of data disks attached to one ECS must be less than 16.|
|InvalidDiskCategory.Mismatch|The specified disk categories combination is not supported.|403|The combination of specified disk categories is not supported.|
|InvalidDiskCategory.NotSupported|The specified disk category is not support the specified instance type.|403|The specified disk category is not supported by the specified instance type.|
|InvalidDiskSize.TooSmall|Specified disk size is less than the size of snapshot.|403|The capacity of the specified disk must be equal to or greater than the size of the specified snapshot.|
|InvalidInstanceType.ZoneNotSupported|The specified zone does not support this InstanceType.|403|The specified InstanceType cannot be created in the specified zone.|
|InvalidNetworkType.MismatchRamRole|Ram role cannot be attached to instances of Classic network type.|403|RAM roles cannot be attached to classic network instances.|
|InvalidPayMethod|The specified billing method is not valid.|403|The specified billing method does not exist.|
|InvalidResourceType.NotSupported|This resource type is not supported; please try other resource types.|403|The specified InstanceType is unavailable. Please try other instance types.|
|InnerServiceFailed|The request processing has failed due to some inner service error.|403|An internal server error.|
|InvalidSnapshotId.NotDataDiskSnapshot|The specified snapshot is system disk snapshot.|403|A data disk cannot be created from a system disk snapshot. A data disk cannot be created from the system disk snapshot.|
|InvalidSnapshotId.NotReady|The specified snapshot has not completed yet.|403|The snapshot has not been completed yet.|
|InvalidSystemDiskCategory.ValueUnauthorized|The disk category is not authorized.|403|You are not authorized to create a disk of the specified category.|
|InvalidUser.PassRoleForbidden|The RAM user does not have the privilege to pass a role.|403|A RAM user must be granted with a pass role permission before the user specifies RamRoleName for a new ECS instance. For more information, see [Attach policies to a RAM user](../../../../intl.en-US/Quick Start/Attach policies to a RAM user.md#).|
|InvalidUserData.Forbidden|User not authorized to input the parameter UserData, please apply for permission UserData.|403|You are not authorized to create the user data.|
|InvalidVSwitchId.NotFound|The VSwitchId provided does not exist in our records.|403|The specified `VSwitchId` does not exist.|
|IoOptimized.NotSupported|The specified image is not support IoOptimized Instance.|403|The specified image does not support the I/O optimized instances.|
|IoOptimized.NotSupported|Vpc is not support IoOptimized instance.|403 | I/O optimized instances are not supported in VPC.|
|OperationDenied|The specified snapshot is not allowed to create disk.|403|The snapshot of the specified disk is not allowed to create a disk, or the snapshot is not allowed to create a disk.|
|OperationDenied|The creation of Instance to the specified Zone is not allowed.|403|An instance cannot be created for the specified zone. Or the specified zone is not in the specified region.|
|OperationDenied|The specified Image is disabled or is deleted.|403|The specified ImageId does not exist.|
|OperationDenied|Sales of this resource are temporarily suspended in the specified region; please try again later.|403|The specified resource is out of stock. Please try other regions and zones.|
|OperationDenied|The capacity of snapshot exceeds the size limit of the specified disk category or the specified category is not authorized.|403|The specified `DataDisk.n.Size` is invalid. Or the maximum capacity of the specified DataDisk.n.Size has exceeded. Or you are not allowed to create a disk of the specified category.|
|OperationDenied|The type of the disk does not support the operation.|403|The specified category does not support the operation.|
|OperationDenied.NoStock|Sales of this resource are temporarily suspended in the specified region; please try again later.|403|The specified instance type is out of stock. Please try other instance types in the region or try other regions and zones.|
|QuotaExceed.BuyImage|The specified image is from the image market, you have not bought it or your quota has been exceeded.|403|The specified image is from the marketplace. You must purchase it in advance  or the image is out of stock in the specified region. For more information, see [Limits](../../../../intl.en-US/User Guide/Limits.md#).|
|QuotaExceed.PortableCloudDisk|The quota of portable cloud disk exceeds.|403|The number of disks that can be attached to an instance has exceeded 16.|
|RegionUnauthorized|There is no authority to create instance in the specified region.|403|You are not authorized to use the specified region.|
|SecurityGroupInstanceLimitExceed|The maximum number of instances in a security group is exceeded.|403|The maximum number of instances in the specified security group has exceeded.|
|Zone.NotOnSale|The specified zone is not available for purchase.|403|The specified zone is unavailable for creating instance. You can try again in other regions or zones. Alternatively, the VSwitch you choosed cannot be used in the specified zone.|
|Zone.NotOpen|The specified zone is not granted to you to buy resources yet.|403|You are not authorized to create instances in the specified zone.|
|ZoneId.NotFound|The specified zone does not exists.|403|The specified ZoneId does not exist.|
|DependencyViolation.IoOptimized|The specified InstanceType must be IoOptimized instance.|404|Only I/O optimized instances are allowed for the specified instance type.|
|HOSTNAME\_ILLEGAL|hostname is not valid.|404|The specified `HostName` is invalid.|
|InvalidDataDiskSnapshotId.NotFound|The specified parameter DataDisk.n.SnapshotId is not valid.|404|The specified `DataDisk.n.SnapshotId` does not exist.|
|InvalidImageId.NotFound|The specified ImageId does not exist.|404| The specified ImageId does not exist.|
|InvalidInstanceChargeType.NotFound|The InstanceChargeType does not exist in our records.|404|The specified `InstanceChargeType` does not exist.|
|InvalidKeyPairName.NotFound|The specified KeyPairName does not exist in our records.|404|The specified `KeyPairName` does not exist.|
|InvalidRamRole.NotFound|The specified RamRoleName does not exist.|404|The specified `RamRoleName` does not exist.|
|InvalidRegionId.NotFound|The specified RegionId does not exist.|404| The specified RegionId does not exist.|
|InvalidSecurityGroupId|The specified SecurityGroupId is invalid or does not exist.|404|The specified `SecurityGroupId` does not exist. or you are not authorized to use the specified SecurityGroupId.|
|InvalidSystemDiskSize|The specified parameter SystemDisk.Size is invalid.|404|The specified `SystemDisk.Size` is invalid.|
|InvalidSystemDiskSize.LessThanImageSize|The specified parameter SystemDisk.Size is less than the image size.|404|The value of specified `SystemDisk.Size` must be greater than the image size.|
|InvalidSystemDiskSize.LessThanMinSize|The specified parameter SystemDisk.Size is less than the min size.|404|The value of specified `SystemDisk.Size` must be less than the minimum capacity of the system disk.|
|InvalidSystemDiskSize.MoreThanMaxSize|The specified parameter SystemDisk.Size is more than the max size.|404|The value of specified `SystemDisk.Size` exceeds the maximum capacity of the system disk.|
|InvalidVSwitchId.NotFound|Specified virtual switch does not exist.|404|The specified VSwitch does not exist.|
|InvalidZoneId.NotFound|The specified ZoneId does not exist.|404|The specified ZoneId does not exist.|
|IoOptimized.NotSupported|The specified InstanceType is not support IoOptimized instance.|404|The specified instance type must be I/O optimized.|
|OperationDenied|Another Instance is being created.|404|Another instance is being created.|
|PaymentMethodNotFound|No billing method has been registered on the account.|404|No payment method is specified for your account.|
|InternalError |The request processing has failed due to some unknown error,exception or failure.|500|Internal error. Please try again later.|

