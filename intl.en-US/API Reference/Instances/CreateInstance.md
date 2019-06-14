# CreateInstance {#CreateInstance .reference}

Create an ECS instance.

## Description {#section_nnh_jcy_wdb .section}

**Note:** Before creating an instance, you can call [EN-US\_TP\_9976.md\#](reseller.en-US/API Reference/Regions/DescribeAvailableResource.md#) to view the available resources in a specified region. [EN-US\_TP\_9856.md\#](reseller.en-US/API Reference/Instances/RunInstances.md#) is recommended if you are going to create multiple instances in a single request.

You are billed when you launch ECS services, so make sure that you understand the billing methods of ECS instances \(`InstanceChargeType`\). And, you must maintain a sufficient balance in your linked credit card or PayPal account to complete the payment or preauthorization. For more information, see [Subscription](../reseller.en-US/Pricing/Subscription.md#) \(`PrePaid`\) and [Pay-As-You-Go](../reseller.en-US/Pricing/Pay-As-You-Go.md#) \(`PostPaid`\). For a subscribed \(`PrePaid`\) instance, your available coupons are the first payment options by default.

When you call this interface, consider the following:

**Instance type**

-   When you create an instance, you can choose an I/O optimized instance.
-   Once an instance is created with ephemeral SSDs, the instance type cannot be changed after the instance is created.

**Image** 

When you create an ECS instance, you must select an image for the system disk configuration. After an instance is created, the instance system disk becomes a clone of that image.

-   If the instance memory is 512 MB, Windows OS is not supported.

-   If the instance memory is 4 GB or larger, a 32-bit OS is not supported.


**Network** 

-   To create an instance for a VPC network, you must specify the VPC network and a VSwitch when creating the instance. One instance can only belong to one VSwitch.

-   If a `VSwitchId` is specified for creating an instance, `SecurityGroupId` and `VSwitchId` must belong to one VPC.

-   If `VSwitchId` and `PrivateIpAddress` are specified at the same time, `PrivateIpAddress` must be within the CidrBlock of the VSwitch.

-   `PrivateIpAddress` depends on `VSwitchId` and you must specify the VSwitch when you modify the `PrivateIpAddress` of your instance.

-   You can call [EN-US\_TP\_9931.md\#](reseller.en-US/API Reference/Networks/AllocatePublicIpAddress.md#) to assign a public IP address.

-   When you create an instance, `InternetChargeType` and `InternetMaxBandwidthOut` determine the bandwidth costs. `InternetMaxBandwidthIn` is not related to billing, and the inbound data traffic for the instance is free.

-   The relationship between `InternetChargeType` and `InternetMaxBandwidthOut` is shown in the following table.

    |Parameter|InternetChargeType|InternetMaxBandwidthOut|
    |:--------|:-----------------|:----------------------|
    |Values|`PayByTraffic`|You are billed according to actual traffic usage.|


**Security groups** 

-   The security group must be created in advance by using the [EN-US\_TP\_9916.md\#](reseller.en-US/API Reference/Security groups/CreateSecurityGroup.md#) interface.

-   You can specify the security group when creating the instance and change the instance security group by using the [ModifyInstanceAttribute](reseller.en-US/API Reference/Instances/ModifyInstanceAttribute.md#) interface.

-   Mutual access is allowed between instances in the same security group in the intranet. By default, firewalls are deployed between security groups, and mutual access between security groups is disabled. However, security group firewall permissions can be set through security group authorization \(by using the interface for granting security group permissions\). For more information, see [EN-US\_TP\_9917.md\#](reseller.en-US/API Reference/Security groups/AuthorizeSecurityGroup.md#) and [EN-US\_TP\_9918.md\#](reseller.en-US/API Reference/Security groups/AuthorizeSecurityGroupEgress.md#).

-   The maximum number of instances in one security group is 1,000. If the security group exceeds this limit, an error message is displayed.


**Block Storage** 

-   The maximum capacity of cloud disks varies according to disk categories:

    -   A single basic cloud disk \(`cloud`\) cannot exceed 2,000 GB.

    -   A single ultra cloud disk \(`cloud_efficiency`\) cannot exceed 32 TB \(32,768 GiB\).

    -   A single SSD cloud disk \(`cloud_ssd`\) cannot exceed 32 TB \(32,768 GiB\).

    -   A single ephemeral SSD \(`ephemeral_ssd`\) cannot exceed 800 GB.

-   ECS allocates a system disk of an appropriate size for the instance based on the the size of the specified image\}. The available disk categories for system disk are basic cloud disk \(`cloud`\), ultra cloud disk \(`cloud_efficiency`\), SSD cloud disk \(`cloud_ssd`\), and ephemeral SSD disk \(`ephemeral_ssd`\).

-   You must be authorized to create ephemeral SSD disk \(ephemeral\_ssd\). By default, new users are not authorized.

-   When an I/O optimized instance is selected, the system disk can choose only ultra cloud disk \(`cloud_efficiency`\) or SSD cloud disk \(`cloud_ssd`\).

-   A maximum of 16 data disks can be added to one instance. By default, device names of data disks are allocated in order, starting from /dev/xvdb to /dev/xvdz. If you choose ephemeral SSD \(`ephemeral_ssd`\) as the data disks of an instance, the system disk must be ephemeral SSD also. The total ephemeral SSD capacity of an instance, excluding the system disk, cannot exceed 1 TiB \(1,024 GiB\).

-   ECS does not allow users to separately create or add an ephemeral SSD. Therefore, the ephemeral SSD must be specified during instance creation. For more information of disk category and size limits, see [Instance type families](../reseller.en-US/Instances/Instance type families.md#).


**User data** 

[User data](../reseller.en-US/Instances/Manage instances/User-defined data/User data.md#) is provided by ECS for you to customize the startup behaviors of an ECS instance and to pass data into an ECS instance. UserData is encoded in Base64 format. User data transmission is not encrypted. We recommend that you do not contain confidential information, such as passwords or private keys, in plaintext.

**Others** 

When you call API in the Alibaba Cloud CLI and SDK, remove the period \(.\) from the request parameters that contain periods \(.\), such as `SystemDisk.Category`, `SystemDisk.Size`, `SystemDisk.Description`, `DataDisk.n.Size`, `DataDisk.n.Category`, `DataDisk.n.SnapshotId`, `DataDisk.n.DiskName`, `DataDisk.n.Description`, `DataDisk.n.DeleteWithInstance`.

For example, [CLI](https://partners-intl.aliyun.com/help/doc-detail/29993.htm) and [SDK](https://github.com/aliyun), use `SystemDiskCategory` instead of `SystemDisk.Category`.

## Request parameters {#section_cx1_3cy_wdb .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: CreateInstance.|
|RegionId|String|Yes|Region ID of an instance. For more information, call [DescribeRegions](../reseller.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|ImageId|String|Yes|ID of an image file. An image is a running environment template for ECS instances. The image ID. You can call [EN-US\_TP\_9899.md\#](reseller.en-US/API Reference/Images/DescribeImages.md#) Describes your available image. If you want to select image from the Alibaba Cloud marketplace, you can view the ImageId on the related image details page.

 |
|InstanceType|String|Yes|Instance type. For more information, see [Instance Type Family](../reseller.en-US/Instances/Instance type families.md#), or call [EN-US\_TP\_9872.md\#](reseller.en-US/API Reference/Instances/DescribeInstanceTypes.md#) to view the latest instance type list.|
|CreditSpecification|String|No| Modifies the running mode of an unlimited credit enabled t5 instance. Optional values:

 -   Standard: The standard running mode. For more information, see [t5 standard instances](../reseller.en-US/Instances/Instance type families/Burstable performance instances/t5 standard instances.md#).
-   Unlimited: The unlimited running mode. For more information, see [t5 unlimited instances](../reseller.en-US/Instances/Instance type families/Burstable performance instances/t5 unlimited instances.md#).

 Default value: null.

 |
|SecurityGroupId|String|Yes|ID of the security group to which an ECS instance belongs. A security group is a firewall group that manages instances in the same region with the same security requirements and mutual trust.|
|ZoneId|String|No|ID of a zone to which an instance belongs. If it is null, a zone is selected by the system. Default value: null.|
|InstanceName|String|No|Name of an ECS instance. -   It can contain \[2, 128\] characters in length, must begin with an English or Chinese character, and can contain digits, periods \(.\), colons \(:\), underscores \(\_\), and hyphens \(-\).
-   The instance name is displayed in the ECS console.
-   If this parameter is not specified, the default value is the InstanceId of the instance.
-   It cannot begin with "http://" or "https://".

 |
|Description|String|No|Description of an ECS instance. -   It can be \[2, 256\] characters in length.
-   The description is displayed in the ECS console.
-   Default value: null.
-   It cannot begin with "http://" or "https://".

 |
|InternetChargeType|String|No|Internet billing method. Optional value: -   PayByTraffic: You are billed based on the traffic usage.

 Default: PayByTraffic.|
|InternetMaxBandwidthIn|String|No|Maximum inbound bandwidth from the Internet, its unit of measurement is Mbit/s. Value range: -   \[1, 200\].

 Default value: 200.|
|InternetMaxBandwidthOut|String|No|Maximum outbound bandwidth to the Internet, its unit of measurement is Mbit/s. If this parameter is not specified, an error is returned. If necessary, you can open a ticket to request to change the bandwidth range to \[1, 200\] Mbit/s. Value range: -   PayByTraffic: \[0,100\]

 Default value: 0.|
|HostName|String|No| -   It cannot start or end with a period \(.\) or a hyphen \(-\) and it cannot have two or more consecutive periods \(.\) or hyphens \(-\).
-   For Windows: The host name can be \[2, 15\] characters in length. It can contain A-Z, a-z, numbers, periods \(.\), and hyphens \(-\). It cannot only contain numbers.
-   For other operating systems: The host name can be \[2, 64\] characters in length. It can be segments separated by periods \(.\). It can contain A-Z, a-z, numbers, and hyphens \(-\).

 |
|Password|String|No|Password of the ECS instance. The password can be \[8, 30\] characters in length. It must contain uppercase letters, lowercase letters, and numbers. The following special characters are allowed: \(\)\`~! @\#$%^&\*-\_+=|\{\}\[\]:;‘<\>,.? /. A slash \(/\) cannot be the first character of Windows instances administrative password. **Note:** If you specify a value for parameter `Password`, use HTTPS to call the API to avoid data breach.

 |
|PasswordInherit|Boolean|No|Whether to use the password pre-configured in the image you select or not. When PasswordInherit is specified, the `Password` must be null. For a secure access, make sure that the selected image has password configured.|
|IoOptimized|String|No|Whether it is an I/O-optimized instance or not. Optional values: -   none
-   optimized

 For [phased-out instance types](https://partners-intl.aliyun.com/help/faq-detail/55263.htm), the default value is none. For other instance types, the default value is optimized.

 |
|SystemDisk.Category|String|No|The category of the system disk. Optional values: -   Cloud: Basic cloud disk.
-   cloud\_efficiency: Ultra cloud disk.
-   cloud\_ssd: Cloud SSD.
-   ephemeral\_ssd: Ephemeral SSD.

 For [phased-out instance types](https://partners-intl.aliyun.com/help/faq-detail/55263.htm) and non-I/O optimized instances, the default value is cloud. Otherwise, the default value is cloud\_efficiency.

 |
|SystemDisk.Size|Integer|No|Size of the system disk, measured in GiB. Value range: \[20, 500\]. The specified value must be equal to or greater than max\{20, Imagesize\}. Default value: max\{40, ImageSize\}.|
|SystemDisk.DiskName|String|No|Name of the system disk. -   It can be \[2, 128\] characters in length, must begin with an English letter or Chinese character, and can contain digits, colons \(:\), underscores \(\_\), or hyphens \(-\).
-   The name is displayed in the ECS console.
-   It cannot begin with http:// or https://.
-   Default value: null.

 |
|SystemDisk.Description|String|No|Description of a system disk. -   It can be \[2, 256\] characters in length.
-   The description is displayed in the ECS console.
-   It cannot begin with http:// or https://.
-   Default value: null.

 |
|DataDisk.n.Size|Integer|No|Size of the n data disk in GBs, n starts from 1. Optional values: -   cloud: \[5, 2000\]
-   cloud\_efficiency: \[20, 32768\]
-   cloud\_ssd: \[20, 32768\]
-   ephemeral\_ssd: \[5, 800\]

 The value must be equal to or greater than the specific snapshot \(`SnapshotId`\).|
|DataDisk.n.Category|String|No|Category of the data disk n, the valid range of n is \[1, 16\]. Optional values: -   cloud: Basic cloud disk.
-   cloud\_efficiency: Ultra cloud disk.
-   cloud\_ssd: Cloud SSD.
-   ephemeral\_ssd: Ephemeral SSD.

 Default value: cloud.|
|DataDisk.n.Encrypted|Boolean|No|Whether the data disk n is encrypted or not. Optional values: -   true: Encrypted.
-   false: Not encrypted.

 Default value: false.|
|DataDisk.n.SnapshotId|String|No|Snapshot is used to create the data disk. After the parameter `DataDisk.n.SnapshotId` is specified, parameter `DataDisk.n.Size` is ignored, and the size of a new disk is the size of the specified snapshot. If the specified snapshot was created on or before July 15, 2013, this invocation is denied, and an error `InvalidSnapshot.TooOld` is returned.|
|DataDisk.n.DiskName|String|No|Name of a data disk. -   It can be \[2, 128\] characters in length. Must begin with an English letter or Chinese character. It can contain digits, colons \(:\), underscores \(\_\), or hyphens \(-\).
-   The data disk name is displayed in the ECS console.
-   Cannot begin with "http://" or "https://".
-   Default value: null.

 |
|DataDisk.n.Description|String|No|Description of a data disk. -   It can be \[2, 256\] characters in length.
-   The disk description is displayed in the console.
-   It cannot begin with http:// or https://.
-   Default value: null.

 |
|DataDisk.n.DeleteWithInstance|Boolean|No|Whether a data disk is released along with the instance or not. Optional values: -   true: The disk is released with the instance.
-   false: The disk is not released with the instance.

 Default value: true. This parameter is only valid for an independent cloud disk, whose value of parameter `DataDisk.n.Category` is `cloud`, `cloud_efficiency`, or `cloud_ssd`. If you specify a value to DataDisk.n.DeleteWithInstance for ephemeral\_ssd, an error is returned.|
|HpcClusterId|String|No|The cluster ID to which the instance belongs.|
|VSwitchId|String|No|The VSwitch ID must be specified when you create a VPC-connected instance.|
|PrivateIpAddress|String|No|Private IP address of an ECS instance. PrivateIpAddress depends on `VSwitchId` and cannot be specified separately.|
|InstanceChargeType|String|No|Billing methods. Optional values: -   PrePaid: Monthly, or annual subscription. Because the subscription payment is made immediately after the instance creation, make sure that your registered credit card is invalid or you have insufficient balance in your PayPal account. Otherwise, `InvalidPayMethod` error may occur.
-   PostPaid: Pay-As-You-Go.

 Default value: PostPaid.|
|SpotStrategy|String|No|The spot price you are willing to accept for a preemptible instance. It takes effect only when parameter `InstanceChargeType` is `PostPaid`. Optional values: -   NoSpot: A normal Pay-As-You-Go instance.
-   SpotWithPriceLimit: Sets the price threshold for a preemptible instance.
-   SpotAsPriceGo: A price that is based on the highest Pay-As-You-Go instance.

 Default value: NoSpot.|
|SpotPriceLimit|Float|No|The hourly price threshold for a preemptible instance, and it takes effect only when parameter `SpotStrategy` is `SpotWithPriceLimit`. Three decimal places are allowed at most.|
|Period|Integer|No|Unit: month. This parameter is valid and required only when `InstanceChargeType` is set to `PrePaid`. Optional values: -   1-9
-   12
-   24
-   36
-   48
-   60

 |
|Periodunit|String|No|Value: Optional values: week | month. When `PeriodUnit` is `Week`, -   Period can be one of \{“1”, “2”, “3”, “4”\}
-   AutoRenewPeriod can be one of \{“1”, “2”, “3”\}

 When `PeriodUnit` is `Month`, -   Period can be one of \{ “1”, “2”, “3”, “4”, “5”, “6”, “7”, “8”, “9”, “12”, “24”, “36”,”48”,”60”\}
-   AutoRenewPeriod can be one of \{“1”, “2”, “3”, “6”, “12”\}

 Default value: Month.|
|AutoRenew|String|No|Whether to set AutoRenew. Whether to set AutoRenew. This parameter is valid when `InstanceChargeType` is `PrePaid`. Optional values: -   True: Enable automatic renewal.
-   False: Disable automatic renewal.

 Default value: false.|
|AutoRenewPeriod|Integer|No|When `AutoRenew` is set to `True`, this parameter is required. Optional values: -   1
-   2
-   3
-   6
-   12

 |
|UserData|String|No|The user data for an instance must be encoded in Base64 format. The maximum size of the user-defined data is 16 KB.|
|ClientToken|String|No| Guarantees the idempotence of the request.  The value is generated by a client and must be globally unique. Only ASCII characters are allowed. It can contain a maximum of 64 ASCII characters. For more information, see [How to ensure idempotence](../reseller.en-US/API Reference/Appendix/How to ensure idempotence.md#).

 |
|KeyPairName|String|No|The name of the key pair. -   This parameter is valid only for a Linux instance. For a Windows ECS instance, if a value is set for parameter KeyPairName, the password still takes effect. Default value: null. If a value is set for parameter KeyPairName, the `Password` still takes effect.
-   The user name and password authentication method is disabled if a value is set for parameter KeyPairName for a Linux instance.

 |
|DeploymentSetId|String|No|Deployment Set ID. If you do not enter the value, 1 is used.|
|RamRoleName|String|No|The RAM role name of the instance. The name is provided and maintained by *RAM* and can be queried using [ListRoles](../../../../../reseller.en-US/API Reference/Role management APIs/ListRoles.md#). For more information, see [CreateRole](../../../../../reseller.en-US/API Reference/Role management APIs/CreateRole.md#) and [ListRoles](../../../../../reseller.en-US/API Reference/Role management APIs/ListRoles.md#).|
|SecurityEnhancementStrategy|String|No|Whether or not to enable security enhancement. Optional values: -   Active: Enables the security enhancement feature and installs a free network security software. Only applicable to the Alibaba Cloud official images.
-   Deactive: Disables the security enhancement feature. No network security software is installed. Applicable to all kinds of images.

 |
|Tag.n.Key|String|No|The key of a tag of which n is from 1 to 20. Once you use this parameter, it cannot be a null string. It can be up to 64 characters in length. It cannot begin with "aliyun", "acs:", "http://", or "https://".|
|Tag.n.Value|String|No|The value of a tag of which n is a number from 1 to 20. Once you use this parameter, it can be a null string. It can be up to 128 characters in length. It cannot begin with "aliyun", "acs:", "http://", or "https://".|
|DeletionProtection|Boolean|No|Whether an instance can be released manually through the console or API \([DeleteInstance](reseller.en-US/API Reference/Instances/DeleteInstance.md#)\). -   true: Enable deletion protection.
-   false \(default value\): Disable deletion protection.

 **Note:** This attribute applies to the Pay-As-You-Go instances. However, it can only restrict the manual release operation, not the release operation by Alibaba Cloud.

 |

## Response parameters {#section_m5f_rjm_xdb .section}

|Name|Type|Description|
|:---|:---|:----------|
|InstanceId|String|ID of the ECS instance. It is a unique identifier of the ECS instance.|

## Examples {#section_y3g_sjm_xdb .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=CreateInstance
&RegionId=cn-hangzhou
&ImageId=_32_23c472_20120822172155_aliguest.vhd
&SecurityGroupId=sg-c0003e8b9
&HostName=Bctest01
&InstanceType=ecs.t1.small
&<Common Response Parameters>
```

**XML format** 

```
<CreateInstanceResponse>
    <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
    <InstanceId>i-instance1</InstanceId>
</CreateInstanceResponse>
```

 **JSON format** 

```
{
    "RequestId": "04F0F334-1335-436C-A1D7-6C044FE73368",
    "InstanceId": "i-instance1"
}
```

## Error codes {#section_oxx_skm_xdb .section}

|Error code|Error message|HTTP status code|Description|
|:---------|:------------|:---------------|:----------|
|Account.Arrearage|Your account has an outstanding payment.|400|Your account has an overdue payment.|
|IncorrectVSwitchStatus|The current status of virtual switch does not support this operation.|400|The status of the specified VSwitch does not support the operation.|
|InstanceDiskCategoryLimitExceed|The specified DataDisk.n.Size beyond the permitted range, or the capacity of snapshot exceeds the size limit of the specified disk category.|400|The specified DataDisk.n.Size exceeds the maximum size of the specified disk category.|
|InstanceDiskNumber.LimitExceed|The total number of specified disk in an instance exceeds.|400|The number of data disks attached to one ECS exceeds 16.|
|InvalidAutoRenewPeriod.ValueNotSupported|The specified autoRenewPeriod is not valid.|400|The specified `AutoRenewPeriod` is invalid.|
|InvalidDataDiskCategory.ValueNotSupported|The specified parameter DataDisk.n.Category is not valid.|400|The specified `DataDisk.n.Category` is invalid.|
|InvalidDataDiskSize.ValueNotSupported|The specified DataDisk.n.Size beyond the permitted range, or the capacity of snapshot exceeds the size limit of the specified disk category.|400|The specified `DataDisk.n.Size` is invalid or exceeds the maximum size of the specified disk category.|
|InvalidDescription.Malformed|The specified parameter Description is not valid.|400|The specified `Description` is invalid.|
|InvalidDiskCategory.Mismatch|The specified disk categories’ combination is not supported.|400|The combination of specified disk categories is not supported.|
|InvalidDiskCategory.ValueNotSupported|The specified parameter DiskCategory is not valid.|400|The specified `DiskCategory` is invalid.|
|InvalidDiskDescription.Malformed|The specified parameter SystemDisk.DiskDescription or DataDisk.n.Description is not valid.|400|The specified `SystemDisk.DiskDescription` or `DataDisk.n.Description` is invalid.|
|InvalidDiskName.Malformed|The specified parameter SystemDisk.DiskName or DataDisk.n.DiskName is not valid.|400|The specified `SystemDisk.DiskName` or `DataDisk.n.DiskName` is invalid.|
|InvalidHostName.Malformed|The specified parameter HostName is not valid.|400|The specified `HostName` is invalid.|
|InvalidHpcClusterId.NotFound|The specified HpcClusterId is not found.|400|The specified `HpcClusterId` does not exist.|
|InvalidHpcClusterId.Creating|The specified HpcClusterId is creating.|400|The specified `HpcClusterId` is being created. Please try again later.|
|InvalidHpcClusterId.Unnecessary|The specified HpcClusterId is unnecessary.|400|You can specify the only for certain `InstanceType`.|
|InvalidVSwitchId.Necessary|The HpcClusterId is necessary.|400|For the specified `InstanceType`, you must specify the `HpcClusterId`.|
|InvalidInstanceName.Malformed|The specified parameter InstanceName is not valid.|400|The specified `InstanceName` is invalid.|
|InvalidInstanceType.ValueNotSupported|The specified InstanceType beyond the permitted range.|400|The specified `InstanceType` is invalid or does not exist.|
|InvalidInstanceType.ValueUnauthorized|The specified InstanceType is not authorized.|400|The specified `InstanceType` is unauthorized.|
|InvalidInternetChargeType.ValueNotSupported|The specified InternetChargeType is not valid.|400|The specified `InternetChargeType` does not exist.|
|InvalidIoOptimizedValue.ValueNotSupported|IoOptimized value not supported.|400|The specified `IoOptimized` is invalid or does not exist.|
|InvalidIPAddress.AlreadyUsed|The specified IPAddress is already used by other resource.|400|The specified PrivateIpAddress already exists.|
|InvalidNetworkType.Mismatch|Specified parameter InternetMaxBandwidthIn or InternetMaxBandwidthOut conflict with instance network type.|400|The specified `InternetMaxBandwidthIn` or `InternetMaxBandwidthOut` does not match the network type of the instance.|
|InvalidSpotStrategy|The specified SpotStrategy is not valid.|400|The parameter`SpotStrategy` is invalid.|
|InvalidSpotPriceLimit|The specified SpotPriceLimitis not valid.|400|The parameter `SpotPriceLimit` is invalid.|
|InvalidSpotAuthorized|The specified Spot param is unauthorized.|400|You cannot create a preemptible instance.|
|InvalidSpotPrepaid|The specified Spot type is not support PrePay Instance.|400|The billing method Subscription is not applicable for preemptible instance.|
|InvalidSpotPriceLimit.LowerThanPublicPrice|The specified parameter spotPriceLimit can’t be lower than current public price.|400|The specified SpotPriceLimit must be equal to or greater than the official price of the specified instance.|
|InvalidNetworkType.Mismatch|Specified parameter InternetChargeType conflict with instance network type.|400|The specified `InternetChargeType` is invalid for the network type of the instance.|
|InvalidNodeControllerId.Malformed|The specified parameter NodeControllerId is not valid.|400|The specified `NodeControllerId` is invalid.|
|InvalidParameter|The specified parameter InternetMaxBandwidthOut is not valid.|400|The specified `InternetMaxBandwidthOut` is invalid or exceeds the maximum rate.|
|InvalidParameter|The specified instance bandwidth is not valid.|400|The specified range of bandwidth is invalid.|
|InvalidParameter.Bandwidth|The specified parameter Bandwidth is not valid.|400|The specified instance bandwidth is not valid.|
|EncryptedOption.Conflict|Encryption value of disk and snapshot conflict.|400|Both the specified data disk and the specified snapshot must be encrypted or not at the same time.|
|InvalidParameter.Conflict|The specified image does not support the specified instance type.|400|You cannot use the specified image to create an ECS instance of the specified `InstanceType`.|
|InvalidParameter.Encrypted.KmsNotEnabled|The encrypted disk need enable KMS.|400|You have not enabled the Key Management Service \(KMS\) service.|
|InvalidParameter.EncryptedIllegal|The value of parameter Encrypted is illegal.|400|The specified `DataDisk.n.Encrypted` is invalid.|
|InvalidParameter.EncryptedNotSupported|Encrypted disk is not support in this region.|400|You cannot encrypt the data disk in the specified region.|
|InvalidParameter.EncryptedNotSupported|Corresponding data disk category does not support encryption.|400|You cannot encrypt the data disk of the specified DataDisk.n.Category.|
|InvalidParameter.Mismatch|Specified security group and virtual switch are not in the same VPC.|400|Both the specified security group and the specified VSwitch must be in the same VPC.|
|InvalidParameter.Mismatch|Specified virtual switch is not in the specified zone.|400|The specified VSwitch is not in the specified zone.|
|InvalidPassword.Malformed|The specified parameter Password is not valid.|400|The specified `Password` is invalid.|
|InvalidPrivateIpAddress|Specified private IP address is not in the CIDR block of virtual switch.|400|You must specify the PrivateIpAddress in the form of a Classless Inter-Domain Routing \(CIDR\) block of the specified VSwitch.|
|InvalidPrivateIpAddress.Duplicated|Specified private IP address is duplicated.|400|The specified `PrivateIpAddress` already exists.|
|InvalidPrivateIpAddress.Malformed|Specified private IP address is malformed.|400|The specified PrivateIpAddress is invalid.|
|InvalidPasswordParam.Mismatch|The input password should be null when passwdInherit is true.|400|When `PasswdInherit` is specified, the `Password` must be null.|
|InvalidSnapshotId.BasedSnapshotTooOld|The specified snapshot is created before 2013-07-15.|400|The specified DataDisk.n.SnapshotId was created before July 15, 2013.|
|InvalidSpotAliUid|The specified UID is not authorized to use SPOT instance.|400|You are not authorized to purchase a preemptible instance.|
|InvalidSystemDiskCategory.ValueNotSupported|The specified parameter SystemDisk.Category is not valid.|400|The specified `SystemDisk.Category` is invalid.|
|InvalidUserData.NotSupported|The specified parameter UserData only support the vpc and IoOptimized Instance.|400|You can only specify UserData for I/O optimized VPC-connected instances.|
|InvalidUserData.SizeExceeded|The specified parameter UserData exceeds the size.|400|The size of the UserData has exceeded 16 KB.|
|MissingParameter|The input parameter VSwitchId that is required for processing this request is not supplied.|400|The `VSwitchId` parameter is required.|
|MissingParamter|The specified parameter Period is not null.|400|The `Period` parameter is required.|
|QuotaExceed.AfterpayInstance|The maximum number of Pay-As-You-Go instances is exceeded.|400|The maximum number of Pay-As-You-Go instances is exceeded.|
|QuotaExceeded|Living instances quota exceeded in this VPC.|400|The number of instances in the specified VPC has reached the upper limit.|
|QuotaExceeded.PrivateIpAddress|Don’t have enough private IPs in this switch.|400|Insufficient number of PrivateIpAddress in the specified VSwitch.|
|ResourceNotAvailable|Resource you requested is not available in this region or zone.|400|The resource you requested is unavailable in the specified RegionId or ZoneId. Please try again in another regions or zones.|
|CategoryNotSupported|The specified zone does not offer the specified disk category.|403|You cannot create a disk of the specified disk category in the specified zone.|
|DeleteWithInstance.Conflict|The specified disk is not a portable disk and cannot be set to DeleteWithInstance attribute.|403|You cannot specify DeleteWithInstance to true for the specified disk.|
|DependencyViolation.WindowsInstance|The instance creating is window, cannot use ssh key pair to login.|403|Parameter KeyPairName is valid only for a Linux instance.|
|DeploymentSet.NoRoom|There is no room for more instance creation in the specified DeploymentSet.|403|No more instances can be created in the specified `DeploymentSetId`.|
|Forbbiden|User not authorized to operate on the specified resource.|403|You are not allowed to operate the specified resource.|
|ImageNotSubscribed|The specified image has not be subscribed.|403|The specified image on the marketplace is not subscribed.|
|ImageNotSupportInstanceType|The specified image don’t support the InstanceType instance.|403|The specified image does not support the instance type.|
|ImageRemovedInMarket|The specified market image is not available, or the specified custom image includes product code because it is based on an image subscribed from marketplace, and that image in marketplace including exact the same product code has been removed.|403|The specified image on the marketplace is unavailable, or the image on the marketplace corresponding to the product code is unavailable.|
|InstanceDiskCategoryLimitExceed|The total size of specified disk category in an instance exceeds.|403|The specified disk category exceeds the maximum capacity of a single instance.|
|InstanceDiskNumLimitExceed|The number of specified disk in an instance exceeds.|403|The number of data disks attached to one ECS must be less than 16.|
|InvalidDiskCategory.Mismatch|The specified disk categories combination is not supported.|403|The combination of specified disk categories is not supported.|
|InvalidDiskCategory.NotSupported|The specified disk category is not support the specified instance type.|403|The specified disk category is not supported by the specified instance type.|
|InvalidDiskSize.TooSmall|Specified disk size is less than the size of snapshot.|403|The capacity of the specified disk must be equal to or greater than the size of the specified snapshot.|
|InvalidInstanceType.ZoneNotSupported|The specified zone does not support this InstanceType.|403|The specified InstanceType cannot be created in the specified zone.|
|InvalidNetworkType.MismatchRamRole|Ram role cannot be attached to instances of Classic network type.|403|RAM roles cannot be attached to classic network instances.|
|InvalidParameter.ResourceOwnerAccount|ResourceOwnerAccount is Invalid.|403|The specified `ResourceOwnerAccount` is invalid.|
|InvalidPayMethod|The specified billing method is not valid.|403|The specified billing method does not exist.|
|InvalidResourceType.NotSupported|This resource type is not supported; please try other resource types.|403|The specified InstanceType is unavailable. Please try other instance types.|
|InvalidSnapshotId.NotDataDiskSnapshot|The specified snapshot is system disk snapshot.|403|A data disk cannot be created from the system disk snapshot.|
|InvalidSnapshotId.NotReady|The specified snapshot has not completed yet.|403|The snapshot has not been completed yet.|
|InvalidSystemDiskCategory.ValueUnauthorized|The disk category is not authorized.|403|You are not allowed to create a disk of the specified category.|
|InvalidUser.PassRoleForbidden|The RAM user does not have the privilege to pass a role.|403|A RAM user must be [granted](../../../../../reseller.en-US/Quick Start/Authorize RAM users.md#) with a pass role permission before he or she specify RamRoleName for a new ECS instance.|
|InvalidVSwitchId.NotFound|The VSwitchId provided does not exist in our records.|403|The specified `VSwitchId` does not exist.|
|IoOptimized.NotSupported|The specified image is not support IoOptimized Instance.|403|The instances of the specified instance type are not I/O optimized.|
|IoOptimized.NotSupported|Vpc is not support IoOptimized instance.|403|I/O optimized instances are not supported in VPC.|
|OperationDenied|The specified snapshot is not allowed to create disk.|403|The snapshot of the specified disk is not allowed to create a disk, or the snapshot is not allowed to create a disk.|
|OperationDenied|The creation of Instance to the specified Zone is not allowed.|403|The specified `ZoneId` is not in the specified `RegionId`. Or an instance cannot be created for the specified zone|
|OperationDenied|The specified Image is disabled or is deleted.|403|The specified image does not exist.|
|OperationDenied|Sales of this resource are temporarily suspended in the specified region; please try again later.|403|The specified zone is unavailable for creating Pay-As-You-Go instances.|
|OperationDenied|The capacity of snapshot exceeds the size limit of the specified disk category or the specified category is not authorized.|403|The specified DataDisk.n.Size is invalid. Or the maximum capacity of the specified DataDisk.n.Size is exceeded. Or you are not allowed to create a disk of the specified category.|
|OperationDenied|The type of the disk does not support the operation.|403|The specified disk type does not support this operation.|
|OperationDenied.NoStock|Sales of this resource are temporarily suspended in the specified region; please try again later.|403|The specified instance type is out of stock. Please try other instance types in the region or try other regions and zones.|
|QuotaExceed.BuyImage|The specified image is from the image market, You have not bought it or your quota has been exceeded.|403|The specified image is from the marketplace. You must purchase it in advance or the image is out of stock in the specified region.|
|QuotaExceed.PortableCloudDisk|The quota of portable cloud disk exceeds.|403|The number of cloud disks that can be attached to an instance has exceeded 16.|
|RegionUnauthorized|There is no authority to create instance in the specified region.|403|You are not authorized to use the specified region.|
|SecurityGroupInstanceLimitExceed|The maximum number of instances in a security group is exceeded.|403|The maximum number of instances in the specified security group is exceeded.|
|Zone.NotOnSale|The specified zone is not available for purchase.|403|The specified zone is unavailable for creating instance. You can try again in other regions or zones.|
|Zone.NotOpen|The specified zone is not granted to you to buy resources yet.|403|You are not allowed to create instances in the specified zone.|
|ZoneId.NotFound|The specified zone does not exists.|403|The specified ZoneId does not exist.|
|DependencyViolation.IoOptimized|The specified InstanceType must be IoOptimized instance.|404|Only I/O optimized instances are allowed for the specified instance type.|
|HOSTNAME\_ILLEGAL|hostname is not valid.|404|The specified `HostName` is invalid.|
|InvalidDataDiskSnapshotId.NotFound|The specified parameter DataDisk.n.SnapshotId is not valid.|404|The specified `DataDisk.n.SnapshotId` does not exist.|
|InvalidDeploymentSetId.NotFound|The specified DeploymentSetId does not exist.|404|The specified `DeploymentSetId` does not exist.|
|InvalidImageId.NotFound|The specified ImageId does not exist.|404|The specified ImageId does not exist.|
|InvalidInstanceChargeType.NotFound|The InstanceChargeType does not exist in our records.|404|The specified `InstanceChargeType` does not exist.|
|InvalidKeyPairName.NotFound|The specified KeyPairName does not exist in our records.|404|The specified `KeyPairName` does not exist.|
|InvalidRamRole.NotFound|The specified RamRoleName does not exist.|404|The specified `RamRoleName` does not exist.|
|InvalidRegionId.NotFound|The specified RegionId does not exist.|404|The specified `RegionId` does not exist.|
|InvalidSecurityGroupId.NotFound|The specified SecurityGroupId does not exist.|404|The specified `SecurityGroupId` does not exist. Or you are not authorized to use the specified SecurityGroupId.|
|InvalidSystemDiskSize|The specified parameter SystemDisk.Size is invalid.|404|The specified `SystemDisk.Size` is invalid.|
|InvalidSystemDiskSize.LessThanImageSize|The specified parameter SystemDisk.Size is less than the image size.|404|The value of specified `SystemDisk.Size` must be greater than the image size.|
|InvalidSystemDiskSize.LessThanMinSize|The specified parameter SystemDisk.Size is less than the min size.|404|The value of specified `SystemDisk.Size` must be less than the minimum capacity of the system disk.|
|InvalidSystemDiskSize.MoreThanMaxSize|The specified parameter SystemDisk.Size is more than the max size.|404|The value of specified `SystemDisk.Size` exceeds the maximum capacity of the system disk.|
|InvalidVSwitchId.NotFound|Specified virtual switch does not exist.|404|The specified VSwitch does not exist.|
|InvalidZoneId.NotFound|The specified ZoneId does not exist.|404|The specified ZoneId does not exist.|
|IoOptimized.NotSupported|The specified InstanceType is not support IoOptimized instance.|404|The instances of the specified instance type are not I/O optimized.|
|OperationDenied|Another Instance is being created.|404|Another Instance is being created.|
|PaymentMethodNotFound|No billing method has been registered on the account.|404|No payment method is registered for your account.|
|InternalError|The request processing has failed due to some unknown error,exception or failure.|500|Internal error. Please try again later.|

