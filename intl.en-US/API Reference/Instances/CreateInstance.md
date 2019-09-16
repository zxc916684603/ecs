# CreateInstance {#doc_api_Ecs_CreateInstance .reference}

You can call this operation to create a pay-as-you-go or subscription Elastic Compute Service \(ECS\) instance.

## Description {#description .section}

**Note:** Before you create an instance, you can call the [DescribeAvailableResource](~~66186~~) operation to view the available instance resources in the specified region or zone. If you want to create multiple instances that automatically enter the running state, we recommend that you call the [RunInstances](~~63440~~) operation.

Before you create an instance, we recommend that you learn more about the ECS billing methods. When you create an ECS instance, fees may apply for additional resources used by the instance. For more information, see [Billing overview](~~25398~~). If the billing method is set to subscription \(`PrePaid`\), available coupons under your account will be used by default.

When you create an instance, pay attention to the following types of request parameters:

For **instance types**:

-   You can specify the `IoOptimized` parameter to indicate whether to create an I/O-optimized instance.
-   If you want to create an instance with local SSDs \(`ephemeral_ssd`\), you cannot change the instance type after the disk is created.

For **images**:

When you create an instance, you must select an image to create the system disk of the new instance. After the instance is created based on the image, the system disk becomes a clone of the image.

-   If the instance memory is 512 MiB, the only Windows image that you can use is the Windows Server 1903 image.
-   If the instance memory is 4 GiB or more, you cannot use 32-bit OS images.

For **network configurations**:

-   You can only obtain a VPC-connected instance by specifying the network type as VPC when you create the instance. One VPC-connected instance can only be attached to one VSwitch.
-   If you specify `VSwitchId`, `SecurityGroupId` and `VSwitchId` must belong to the same VPC.
-   `VSwitchId` and `PrivateIpAddress` are both specified, `PrivateIpAddress` must be in the same CIDR block as the VSwitch.
-   `PrivateIpAddress` is dependent on `VSwitchId`, and you cannot only specify the `PrivateIpAddress` parameter.
-   If you call this operation to create an instance, the public IP address is not automatically allocated to the instance. You can call the [AllocatePublicIpAddress](~~25544~~) operation to allocate a public IP address to the instance.
-   When you create an instance, the `InternetChargeType` and `InternetMaxBandwidthOut` parameter values can affect the bandwidth fees. `InternetMaxBandwidthIn` is not related to billing. The inbound data traffic for the instance is free.
-   `InternetChargeType=PayByTraffic` indicates that the instance is charged based on the actual traffic and `InternetMaxBandwidthOut` is the upper limit of the bandwidth. The pay-as-you-go billing method is used.

For **security groups**:

-   You can call the [CreateSecurityGroup](~~25553~~) operation to create a security group before you create the instance.
-   You can also specify a security group when you create an instance or call the [ModifyInstanceAttribute](~~25503~~) operation to change the security group of the instance.
-   Instances in the same security group can communicate with each other in a private network. Instances in different security groups cannot communicate with each other by default. However, you can authorize the communication by calling specific operations. For more information, see [AuthorizeSecurityGroup](~~25554~~) and [AuthorizeSecurityGroupEgress](~~25560~~).
-   One security group can contain a maximum of 1,000 instances.

For **storage**:

-   The maximum capacity of data disks varies based on disk categories:
    -   The maximum capacity of a single basic disk \(`cloud`\) is 2,000 GiB.
    -   The maximum capacity of a single ultra disk \(`cloud_efficiency`\) is 32 TiB \(32,768 GiB\).
    -   The maximum capacity of a single standard SSD \(`cloud_ssd`\) is 32 TiB \(32,768 GiB\).
    -   The maximum capacity of a single enhanced SSD \(`cloud_essd`\) is 32 TiB \(32,768 GiB\).
    -   The maximum capacity of a single local SSD \(`ephemeral_ssd`\) is 800 GiB.
-   When you create an instance, ECS automatically selects the system disk size based on the specified image. The system disk capacity must be at least 20 GiB and equal to or greater than the size of the image. The system disk can be a basic disk \(`cloud`\), an ultra disk \(`cloud_efficiency`\), a standard SSD \(`cloud_ssd`\), or a local SSD \(`ephemeral_ssd`\).
-   When the system disk is a basic disk \(`cloud`\), an ultra disk \(`cloud_efficiency`\), or a standard SSD \(`cloud_ssd`\), the data disk cannot be a local SSD \(`ephemeral_ssd`\).
-   When you select an I/O-optimized instance, the system disk can be an ultra disk \(`cloud_efficiency`\) or standard SSD \(`cloud_ssd`\).
-   An instance can have a maximum of 16 data disks. The system creates the mount points for data disks by using automatically generated names, from /dev/xvdb to /dev/xvdz. If a local SSD \(`ephemeral_ssd`\) is used as the data disk, the system disk must also be a local SSD. The total capacity of local SSDs for an instance cannot exceed 1 TiB \(1,024 GiB, excluding the system disk\).
-   To use local SSDs \(`ephemeral_ssd`\), you must select local SSDs when you create an instance. Local SSDs cannot be added after the instance is created. For more information, see [Instance families](~~25378~~).

For **user data**:

If the instance type supports [user data](~~49121~~), you can pass in the UserData parameter. The UserData parameter must be encoded in Base64. We recommend that you do not pass in confidential information, such as passwords or keys, because the UserData parameter is passed in plaintext. If you need to pass in confidential information, we recommend that you first encrypt and encode the UserData parameter in Base64. You can then decode and decrypt the UserData parameter in the instance.

For **others**:

When you call the operations in the Alibaba Cloud Command Line Interface \(CLI\) and SDK, you must delete the periods \(.\) from some of the input parameters that contain periods \(.\). These parameters include: `SystemDisk.Category`, `SystemDisk.Size`, `SystemDisk.Description`, `DataDisk.N.Size`, `DataDisk.N.Category`, `DataDisk.N.SnapshotId`, `DataDisk.N.DiskName`, `DataDisk.N.Description`, `DataDisk.N.DeleteWithInstance`, and `DataDisk.N.PerformanceLevel`.

For example, in [Alibaba Cloud CLI](~~66653~~) and [SDK](https://github.com/aliyun), use `SystemDiskCategory` as the input parameter instead of `SystemDisk.Category`.

## Debugging {#api_explorer .section}

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=CreateInstance&type=RPC&version=2014-05-26)

## Request parameters {#parameters .section}

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|ImageId|String|Yes|win2008r2\_64\_ent\_sp1\_en-us\_40G\_alibase\_20170915.vhd|The ID of the image file. For marketplace images, you can view the `ImageId` of a specific image on its Product Details page at Alibaba Cloud Marketplace.

 |
|InstanceType|String|Yes|ecs.g5.large|The type of the instance. For more information, see [Instance families](~~25378~~) or call the [DescribeInstanceTypes](~~25620~~) operation to query the list of the latest instance types.

 |
|RegionId|String|Yes|cn-hangzhou|The region ID of the instance. You can call the [DescribeRegions](~~25609~~) operation to query the latest region list.

 |
|Action|String|No|CreateInstance|The operation that you want to perform. For HTTP and HTTPS requests, the `Action` parameter is required. Set this parameter to CreateInstance.

 |
|SecurityGroupId|String|No|sg-bp15ed6xe1yxeycg7\*\*\*|The ID of the security group to which the instance belongs. Instances in the same security group can communicate with each other.

 |
|InstanceName|String|No|yk201812061032|The name of the instance. It must be 2 to 128 characters in length. It must start with a letter and cannot start with http:// or https://. It can contain digits, colons \(:\), hyphens \(-\), and underscores \(\_\). If this parameter is not specified, the name is set to the instance ID by default.

 |
|AutoRenew|Boolean|No|true|Specifies whether to enable automatic renewals. This parameter is valid when `InstanceChargeType` is set to `PrePaid`. Valid values:

 -   true: enables automatic renewal for the instance.
-   false: disables automatic renewal for the instance. This is the default value.

 |
|InternetChargeType|String|No|PayByTraffic|The billing method of the network bandwidth. Valid values:

 -   PayByTraffic: The billing method is based on actual traffic. This is the default value.

 |
|AutoRenewPeriod|Integer|No|2|The automatic renewal period of the instance. This parameter is required when AutoRenew is set to true. Valid values:

 If the PeriodUnit parameter is set to Month: 1, 2, 3, 6, and 12.

 |
|InternetMaxBandwidthIn|Integer|No|200|The maximum inbound bandwidth for Internet traffic. Unit: Mbit/s. Valid values: 1 to 200

 Default value: 200

 |
|InternetMaxBandwidthOut|Integer|No|5|The maximum outbound bandwidth for Internet traffic. Unit: Mbit/s. Valid values: 0 to 100

 Default value: 0

 |
|HostName|String|No|LocalHost|The hostname of the ECS instance.

 -   It cannot start or end with a period \(.\) or a hyphen \(-\). It cannot contain consecutive periods \(.\) or hyphens \(-\).
-   For Windows, the hostname must be 2 to 15 characters in length. The hostname cannot contain periods \(.\) or only contain digits. It can contain letters, digits, and hyphens \(-\).
-   For other operating systems such as Linux, the hostname must be 2 to 64 characters in length. It can be segments separated with periods \(.\). Each segment can contain letters, digits, and hyphens \(-\).

 |
|Password|String|No|EcsV587!|The password for the instance. The password must be 8 to 30 characters in length. It must include at least three of the following character types: uppercase letters, lowercase letters, digits, and special characters. Special characters include:

 ```

( ) ` ~ ! @ # $ % ^ & * - _ + = | { } [ ] : ; ' < > , . ? /

```

 Passwords for Windows instances cannot start with a forward slash \(/\).

 **Note:** If the `Password` parameter is specified, we recommend that you send requests over the HTTPS protocol to ensure the security of your password.

 |
|PasswordInherit|Boolean|No|false|Specifies whether to use the password predefined in the image. If the PasswordInherit parameter is set to true, the Password parameter must not be specified. You must ensure that the selected image has a password configured.

 |
|DeploymentSetId|String|No|ds-bp1brhwhoqinyjd6t\*\*\*|The ID of the deployment set.

 |
|ZoneId|String|No|cn-hangzhou-g|The ID of the zone to which the instance belongs. For more information about the available zones, see [DescribeZones](~~25610~~).

 Default value: null. If you do not specify a zone, the system randomly selects a zone.

 |
|ClusterId|String|No|c-clusterid1|The ID of the cluster to which the instance belongs.

 **Note:** This parameter is deprecated and will be later removed. we recommend that you use other parameters to ensure maximum compatibility.

 |
|ClientToken|String|No|123e4567-e89b-12d3-a456-426655440000|The client token that is used to ensure the idempotence of the request. You can use your own methods to generate this value, but you must ensure that it is unique among different requests. **ClientToken** can only contain ASCII characters, and cannot exceed 64 characters in length. For more information, see [How to ensure idempotence](~~25693~~).

 |
|VlanId|String|No|10|The VLAN ID of the instance.

 |
|InnerIpAddress|String|No|10.0.0.0|The private network IP address of the instance.

 |
|SystemDisk.Size|Integer|No|40|The size of the system disk. Unit: GiB. Valid values: 20 to 500

 The parameter must be at least 20 and equal to or more than the size of the image.

 Default value: 40 or the size of the image, depending on whichever is greater

 |
|SystemDisk.Category|String|No|cloud\_ssd|The type of the system disk. The default value for [retired instance types](~~55263~~) without I/O optimizations is cloud. The default value for other types of instances is cloud\_efficiency. Valid values:

 -   cloud: basic disk
-   cloud\_efficiency: ultra disk
-   cloud\_ssd: standard SSD
-   ephemeral\_ssd: local SSD
-   cloud\_essd: enhanced SSD \(ESSD\)

 |
|SystemDisk.DiskName|String|No|SystemDisk|The name of the system disk of created instances. It must be 2 to 128 characters in length. It must start with a letter and cannot start with http:// or https://. It can contain digits, colons \(:\), hyphens \(-\), and underscores \(\_\). Default value: null

 |
|SystemDisk.Description|String|No|SystemDiskFinance|The description of the system disk. It must be 2 to 256 characters in length and cannot start with http:// or https://. Default value: null

 |
|DataDisk.N.Size|Integer|No|2000|The size of the Nth data disk. Valid values of N: 1 to 16. Unit: GiB. Valid values:

 -   cloud: 5 to 2,000
-   cloud\_efficiency: 20 to 32,768
-   cloud\_ssd: 20 to 32,768
-   cloud\_essd: 20 to 32,768
-   ephemeral\_ssd: 5 to 800

 The value of this parameter must be greater than or equal to the size of the snapshot specified by the `SnapshotId` parameter.

 |
|DataDisk.N.SnapshotId|String|No|s-bp17441ohwka0yuhx\*\*\*|The ID of the snapshot used to create the Nth data disk. Valid values of N: 1 to 16 If the `DataDisk.N.SnapshotId` parameter is specified, the `DataDisk.N.Size` parameter will be ignored, and the size of the created disk will be the size of the specified snapshot. Snapshots created on or before July 15, 2013 are not applicable. Otherwise, an error will be returned and your request will be rejected.

 |
|DataDisk.N.Category|String|No|cloud\_ssd|The category of Nth data disk. Valid values:

 -   cloud: basic disk. This is the default value.
-   cloud\_efficiency: ultra disk
-   cloud\_ssd: standard SSD
-   ephemeral\_ssd: local SSD
-   cloud\_essd: enhanced SSD \(ESSD\)

 |
|DataDisk.N.DiskName|String|No|DataDisk|The name of Nth data disk. It must be 2 to 128 characters in length. It must start with a letter and cannot start with http:// or https://. It can contain digits, colons \(:\), hyphens \(-\), and underscores \(\_\). Default value: null

 |
|DataDisk.N.Description|String|No|DataDiskFinance|The description of the Nth data disk. It must be 2 to 256 characters in length and cannot start with http:// or https://. Default value: null

 |
|DataDisk.N.Device|String|No|/dev/xvda|The mount point of the Nth data disk.

 |
|DataDisk.N.DeleteWithInstance|Boolean|No|true|Specifies whether the Nth data disk is released when the instance is released. Default value: true

 |
|DataDisk.N.Encrypted|Boolean|No|false|Specifies whether the Nth data disk is encrypted. Default value: false

 |
|Description|String|No|InstanceFinance|The description of the instance. It must be 2 to 256 characters in length and cannot start with http:// or https://. Default value: null

 |
|VSwitchId|String|No|vsw-bp1s5fnvk4gn2tws03\*\*\*|The ID of the VSwitch. It must be specified when you create VPC-connected instances.

 |
|PrivateIpAddress|String|No|172.16.236.14X|The private IP address of the instance. This private IP address must be selected from the range defined by the CIDR block of the VSwitch.

 |
|IoOptimized|String|No|optimized|Specifies whether the instance is an I/O-optimized instance. The default value for [retired instance types](~~55263~~) is none. The default value for other instances is optimized. Valid values:

 -   none: The instance is not an I/O-optimized type.
-   optimized: The instance is an I/O-optimized type.

 |
|UseAdditionalService|Boolean|No|true|Specifies whether to use additional system tools provided by Alibaba Cloud \(Windows: NTP and KMS. Linux: NTP and YUM\).

 |
|InstanceChargeType|String|No|PrePaid|The billing method of the instance. Valid values:

 -   PrePaid: The billing method is subscription. If it is set to PrePaid, you must ensure that your payment account has sufficient balance or credit. Otherwise, the `InvalidPayMethod` error code is returned.
-   PostPaid: The billing method is pay-as-you-go. This is the default value.

 |
|Period|Integer|No|1|The subscription period of the instance. Unit: Month. This parameter is valid and only required when the value of the `InstanceChargeType` parameter is `PrePaid`. If the `DedicatedHostId` parameter is specified, the specified period cannot exceed the subscription period of the dedicated host. Valid values:

 If the PeriodUnit parameter is set to Month: 1, 2, 3, 4, 5, 6, 7, 8, 9, 12, 24, 36, 48, and 60.

 |
|PeriodUnit|String|No|Month|The unit of the billing cycle for the instance. Valid values: Week and Month. Default value: Month

 |
|Tag.N.Key|String|No|FinanceDept|The tag key of the instances, disks, and primary ENIs. Valid values of N: 1 to 20 It cannot be an empty string. It can be up to 64 characters in length and cannot start with aliyun or acs:. It cannot contain http:// or https://.

 |
|Tag.N.Value|String|No|FinanceDeptJoshua|The tag value of the instances, disks, and primary ENIs. Valid values of N: 1 to 20 The tag value can be an empty string. It can be up to 128 characters in length and cannot start with aliyun or acs:. It cannot contain http:// or https://.

 |
|UserData|String|No|ZWNobyBoZWxsbyBlY3Mh|The user data of the instance. It must be encoded in Base64. The maximum size for the raw data is 16 KB.

 |
|SpotStrategy|String|No|NoSpot|The bidding mode of the pay-as-you-go instance. This parameter is valid when `InstanceChargeType` is set to `PostPaid`. Valid values:

 -   NoSpot: a standard pay-as-you-go instance. This is the default value.
-   SpotWithPriceLimit: a preemptible instance with an upper price limit.
-   SpotAsPriceGo: a preemptible instance that is billed based on the actual market price.

 |
|KeyPairName|String|No|Instancetest|The name of the SSH key pair.

 -   For Windows instances, this parameter is ignored. Default value: null The `Password` parameter is still used if the KeyPairName parameter is specified.
-   For Linux instances, password authentication is disabled by default. To improve instance security, we recommend that you use the SSH key pair for connection.

 |
|SpotPriceLimit|Float|No|0.98|The maximum hourly price for the instance. This parameter supports a maximum of three decimal places and takes effect when the `SpotStrategy` parameter is set to `SpotWithPriceLimit`.

 |
|SpotInterruptionBehavior|String|No|Terminate|The interruption mode of the preemptible instance. Only the Terminate mode is supported, in which the instance is released. Default value: Terminate

 |
|RamRoleName|String|No|FinanceDept|The name of the RAM role for the instance. You can call the [ListRoles](~~28713~~) operation provided by RAM to query the RAM roles that you have created.

 |
|SecurityEnhancementStrategy|String|No|Active|Specifies whether to enable security enhancement. Valid values:

 -   Active: enables security enhancement. It is only applicable to the system image.
-   Deactive: disables security enhancement for all image types.

 |
|ResourceGroupId|String|No|rg-resourcegroupid|The ID of the resource group to which the instance belongs.

 |
|HpcClusterId|String|No|hpc-hpcclusterid|The ID of the HPC cluster to which the instance belongs.

 |
|DryRun|Boolean|No|false|Specifies whether to send a dry-run request.

 -   true: Only a dry-run request is sent and no instance is created. The system checks whether the required parameters are set, and validates the request format, service permissions, and available ECS instances. If the validation fails, the corresponding error code is returned. If the validation succeeds, the `DryRunOperation` error code is returned.
-   false: A request is sent. If the validation succeeds, the instance is created. This is the default value.

 |
|DedicatedHostId|String|No|dh-dedicatedhost1|The ID of the dedicated host for the ECS instance. You can call the [DescribeDedicatedHosts](~~94572~~) operation to view the dedicate host list.

 No preemptible instances can be created on a dedicated host. Therefore, if you specify `DedicatedHostId`, the `SpotStrategy` and `SpotPriceLimit` parameters will be ignored.

 |
|CreditSpecification|String|No|Standard|The performance mode of the t5 burstable instance. Valid values:

 -   Standard: the standard mode. For more information, see the standard mode section of [Burstable instances](~~59977~~).
-   Unlimited: the unlimited mode. For more information, see the unlimited mode section of [Burstable instances](~~59977~~).

 Default value: null

 |
|DeletionProtection|Boolean|No|false|Specifies whether you can use the ECS console or call the [DeleteInstance](~~25507~~) operation to release the instance. Valid values:

 -   true: enables release protection.
-   false: disables release protection. This is the default value.

 **Note:** This parameter is only applicable to pay-as-you-go instances. It can only protect against manual releases and is not supported for system releases.

 |
|SystemDisk.PerformanceLevel|String|No|PL1|The performance level of the ESSD system disk. Valid values:

 -   PL1: a single ESSD delivers up to 50,000 random read/write IOPS. This is the default value.
-   PL2: a single ESSD delivers up to 100,000 random read/write IOPS.
-   PL3: a single ESSD delivers up to 1,000,000 random read/write IOPS.

 For more information about ESSD performance levels, see [ESSD cloud disk](~~122389~~).

 |
|DataDisk.N.PerformanceLevel|String|No|PL2|The performance level of the Nth ESSD data disk. The value of N must be the same as that in `DataDisk.N.Category=cloud_essd`. Valid values:

 -   PL1: a single ESSD delivers up to 50,000 random read/write IOPS. This is the default value.
-   PL2: a single ESSD delivers up to 100,000 random read/write IOPS.
-   PL3: a single ESSD delivers up to 1,000,000 random read/write IOPS.

 For more information about ESSD performance levels, see [ESSD cloud disk](~~122389~~).

 |
|Affinity|String|No|default|Specifies whether an instance on a dedicated host is associated with the dedicated host. This parameter is applicable to instances with the No Charges After Instance Is Stopped feature enabled. Valid values:

 -   default: The instance is not associated with the dedicated host. If the associated dedicated host has insufficient resources after the stopped instance is restarted, the instance is automatically allocated to an alternative dedicated host.
-   host: The instance is associated with the dedicated host. The stopped instance still resides on the associated dedicated host after it is restarted. If the available resources of the original dedicated host are insufficient, the instance will fail to restart.

 Default value: default

 |
|Tenancy|String|No|default|Specifies whether to create an instance on a dedicated host. Valid values:

 -   default: creates an instance that is not on a dedicated host.
-   host: creates an instance that is on a dedicated host. If you do not specify the `DedicatedHostId` parameter, then ECS automatically selects a dedicated host for the instance.

 Default value: default

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|InstanceId|String|i-instanceid1|The ID of the instance. It is the unique identifier of the instance.

 |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|The ID of the request. The request ID is returned, regardless of whether the operation is successful.

 |

## Examples {#demo .section}

Sample requests

``` {#request_demo}
https://ecs.aliyuncs.com/?Action=CreateInstance
&RegionId=cn-hangzhou
&ImageId=_32_23c472_20120822172155_aliguest.vhd
&SecurityGroupId=sg-bp15ed6xe1yxeycg7***
&HostName=Bctest01
&InstanceType=ecs.t1.small
&<Common request parameters>
```

Sample success responses

`XML` format

``` {#xml_return_success_demo}
<CreateInstanceResponse>
      <RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
      <InstanceId>i-instance1</InstanceId>
</CreateInstanceResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
	"InstanceId":"i-instance1",
	"RequestId":"04F0F334-1335-436C-A1D7-6C044FE73368"
}
```

## Error codes { .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|InvalidInstanceType.ValueUnauthorized|The specified InstanceType is not authorized.|The error message returned because you are not authorized to use the specified instance type.|
|400|InvalidInternetChargeType.ValueNotSupported|The specified InternetChargeType is not valid.|The error message returned because the specified InternetChargeType does not exist.|
|400|InvalidParameter|The specified parameter "InternetMaxBandwidthOut" is not valid.|The error message returned because the specified InternetMaxBandwidthOut is invalid.|
|400|InvalidSystemDiskCategory.ValueNotSupported|The specified parameter " SystemDisk.Category " is not valid.|The error message returned because the specified system disk category is invalid.|
|404|IoOptimized.NotSupported|The specified instancetype is not support IoOptimized instance|The error message returned because the specified instance type does not support I/O optimization.|
|400|InvalidDataDiskSize.ValueNotSupported|The specified DataDisk.n.Size beyond the permitted range, or the capacity of snapshot exceeds the size limit of the specified disk category.|The error message returned because the specified size of the data disk exceeds the upper limit or the size the snapshot exceeds the upper limit of the specified disk category.|
|403|InvalidDiskCategory.NotSupported|The specified disk category is not support the specified instance type.|The error message returned because the specified instance type does not support the specified disk category.|
|400|InvalidInstanceType.ValueNotSupported|The specified InstanceType does not exist or beyond the permitted range.|The error message returned because the specified instance type is not supported.|
|404|InvalidSecurityGroupId.NotFound|The specified SecurityGroupId does not exist.|The error message returned because the specified security group does not exist under this account. Check whether the security group ID is valid.|
|400|InvalidDescription.Malformed|The specified parameter "Description" is not valid.|The error message returned because the specified description is invalid. The description must be 2 to 256 characters in length and cannot start with http:// or https://.|
|400|InvalidHostName.Malformed|The specified parameter "HostName" is not valid.|The error message returned because the format of the specified HostName is invalid.|
|400|InvalidPassword.Malformed|The specified parameter "Password" is not valid.|The error message returned because the format of the Password parameter is invalid.|
|400|InvalidPasswordParam.Mismatch|The input password should be null when passwdInherit is true.|The error message returned because if PasswdInherit is set to true, the Password parameter must not be specified.|
|400|InvalidSystemDiskCategory.ValueNotSupported|The specified parameter "SystemDisk.Category" is not valid.|The error message returned because the specified SystemDisk.Category is invalid.|
|400|InvalidDiskName.Malformed|The specified parameter "SystemDisk.DiskName or DataDisk.n.DiskName" is not valid.|The error message returned because the SystemDisk.DiskName or DataDisk.N.DiskName parameter is invalid.|
|400|InvalidDiskDescription.Malformed|The specified parameter "SystemDisk.DiskDescription" or "DataDisk.n.Description" is not valid.|The error message returned because the specified SystemDisk.DiskDescription or DataDisk.N.Description is invalid.|
|400|InvalidDataDiskCategory.ValueNotSupported|The specified parameter "DataDisk.n.Category" is not valid.|The error message returned because the specified DataDisk.N.Category is invalid.|
|404|InvalidDataDiskSnapshotId.NotFound|The specified parameter "DataDisk.n.SnapshotId" is not valid.|The error message returned because the specified DataDisk.N.SnapshotId parameter is invalid.|
|400|InvalidDataDevice.Malformed|The specified parameter "DataDisk.n.Device" is not valid.|The error message returned because the DataDisk.N.Device parameter is invalid.|
|400|InvalidNodeControllerId.Malformed|The specified parameter "NodeControllerId" is not valid.|The error message returned because the specified NodeControllerId is invalid.|
|400|InvalidInnerIpAddress.Malformed|The specified parameter "InnerIpAddress" is not valid.|The error message returned because the specified InnerIpAddress is invalid.|
|400|InvalidInnerIpAddress.Unusable|The specified InnerIpAddress is already used or not found in usable ip range.|The error message returned because the specified InnerIpAddress is unavailable.|
|400|OperationDenied|The specified parameter "VlanId" is not valid or vlan has not enough IP address.|The error message returned because the specified VLAN ID is invalid or the number of IP addresses in the VLAN has reached the upper limit.|
|400|InvalidParameter.Conflict|The specified image does not support the specified instance type.|The error message returned because the specified image cannot be used for the specified instance type.|
|400|ImageNotSupportCloudInit|The specified image does not support cloud-init.|The error message returned because the specified image does not support cloud-init.|
|400|InvalidSnapshotId.BasedSnapshotTooOld|The specified snapshot is created before 2013-07-15.|The error message returned because the specified snapshot was created before July 15, 2013.|
|400|QuotaExceed.AfterpayInstance|The maximum number of Pay-As-You-Go instances is exceeded: %s|The error message returned because the number of pay-as-you-go instances that are allowed to be created has reached the upper limit.|
|403|ImageNotSubscribed|The specified image has not be subscribed.|The error message returned because you have not subscribed to the specified image in the marketplace.|
|400|InvalidMarketImageChargeType.NotSupport|The specified chargeType of marketImage is unsupported.|The error message returned because the billing method for marketplace images is invalid.|
|403|OperationDenied|The specified Image is disabled or is deleted.|The error message returned because the specified image is disabled or deleted.|
|403|InvalidSystemDiskCategory.ValueUnauthorized|The disk category is not authorized.|The error message returned because you are not authorized to use the specified disk category.|
|403|InvalidSnapshotId.NotReady|The specified snapshot has not completed yet.|The error message returned because the specified snapshot is being created.|
|403|OperationDenied|The specified snapshot is not allowed to create disk.|The error message returned because no disk can be created for the specified snapshot.|
|403|InstanceDiskCategoryLimitExceed|The total size of specified disk category in an instance exceeds.|The error message returned because the total size of the specified disks exceeds the maximum capacity that is allowed for the disk category.|
|403|InvalidDevice.InUse|The specified device has been occupied.|The error message returned because the specified device has been mounted to a disk and is not available.|
|403|ImageRemovedInMarket|The specified market image is not available, Or the specified user defined image includes product code because it is based on an image subscribed from marketplace, and that image in marketplace includeing exact the same product code has been removed.|The error message returned because the specified marketplace image is not available.|
|404|InvalidClusterId.NotFound|The ClusterId provided does not exist in our records.|The error message returned because the specified ClusterId does not exist.|
|403|OperationDenied|The creation of Instance to the specified Zone is not allowed.|The error message returned because no instance can be created in the specified zone.|
|403|CategoryNotSupported|The specified zone does not offer the specified disk category.|The error message returned because the specified disk category is unavailable in the specified zone.|
|403|OperationDenied|The specified Zone or cluster does not offer the specified disk category or the speicified zone and cluster do not match.|The error message returned because the specified disk category is unavailable in the specified zone or cluster, or because the specified zone and cluster do not correspond to each other.|
|403|OperationDenied.NoStock|The requested resource is sold out in the specified zone; try other types of resources or other regions and zones.|The error message returned because of insufficient inventory for the requested resource. Try again with other resource types or other regions and zones.|
|400|InvalidInstanceName.Malformed|The specified parameter "InstanceName" is not valid.|The error message returned because the format of the specified instance name is invalid. The name must be 2 to 128 characters in length. It can contain letters, digits, colons \(:\), underscores \(\_\), and hyphens \(-\). It must start with a letter and cannot start with http:// or https://.|
|400|InvalidDiskDescription.Malformed|The specified parameter "SystemDisk.DiskDescription or DataDisk.n.Description" is not valid.|The error message returned because the specified SystemDisk.DiskDescription or DataDisk.N.Description is invalid.|
|403|QuotaExceed.PortableCloudDisk|The quota of portable cloud disk exceeds.|The error message returned because the number of portable disks has reached the upper limit.|
|500|InternalError|The request processing has failed due to some unknown error.|The error message returned because an internal error has occurred. Try again later. If the problem persists, submit a ticket.|
|403|OperationDenied|Sales of this resource are temporarily suspended in the specified region; please try again later.|The error message returned because the sales of the specified resources in the specified region are disabled.|
|400|InvalidParameter.Conflict|The specified region and cluster do not match.|The error message returned because the specified region does not correspond to the specified cluster.|
|403|SecurityGroupInstanceLimitExceed|The maximum number of instances in a security group is exceeded.|The error message returned because the number of instances in the security group has reached the upper limit.|
|403|NodeControllerUnavailable|The Node Controller is temporarily unavailable.|The error message returned because the node controller is currently unavailable.|
|403|RegionUnauthorized|There is no authority to create instance in the specified region.|The error message returned because you are not authorized to create instances in the specified region.|
|403|CategoryNotSupported|The specified Zone or cluster does not offer the specified disk category.|The error message returned because the specified disk category is unavailable in the specified zone or cluster.|
|403|InvalidSnapshotId.NotDataDiskSnapshot|The specified snapshot is system disk snapshot.|The error message returned because the specified snapshot is a system disk snapshot.|
|403|CategoryNotSupported|The specified cluster does not offer the specified disk category.|The error message returned because the specified disk category is unavailable in the specified cluster.|
|404|InvalidVSwitchId.NotFound|Specified virtual switch does not exist.|The error message returned because the specified VSwitch does not exist.|
|400|InvalidParameter.Mismatch|Specified security group and virtual switch are not in the same VPC.|The error message returned because the specified security group is not in the same VPC as the VSwitch.|
|400|InvalidNetworkType.Mismatch|Specified parameter "InternetMaxBandwidthIn" or "InternetMaxBandwidthOut" conflict with instance network type.|The error message returned because the specified InternetMaxBandwidthIn or InternetMaxBandwidthOut value conflicts with the instance network type.|
|400|InvalidNetworkType.Mismatch|Specified parameter "InternetChargeType" conflict with instance network type.|The error message returned because the network type of the instance does not support the specified network billing method.|
|400|InvalidPrivateIpAddress|Specified private IP address is not in the CIDR block of virtual switch.|The error message returned because the specified private IP address is not in the same CIDR block as the VSwitch.|
|400|InvalidPrivateIpAddress.Malformed|Specified private IP address is malformed.|The error message returned because the specified private IP address is invalid.|
|400|InvalidPrivateIpAddress.Duplicated|Specified private IP address is duplicated.|The error message returned because the specified private IP address has been used. Change the IP address and try again.|
|400|QuotaExceeded.PrivateIpAddress|Don't have enough private IPs in this switch|The error message returned because all the private IP addresses under the VSwitch are being used. Try another VSwitch.|
|400|QuotaExceeded|Living instances quota exceeded in this VPC.|The error message returned because the number of active instances has reached the upper limit.|
|400|IncorrectVSwitchStatus|The current status of virtual switch does not support this operation.|The error message returned because the specified VSwitch is in the pending state and cannot be deleted.|
|400|InvalidParameter.Mismatch|Specified virtual switch is not in the specified zone.|The error message returned because the specified VSwitch does not exist in the specified zone.|
|400|ResourceNotAvailable|Resource you requested is not available in this region or zone.|The error message returned because the specified region or zone does not support VPC.|
|400|MissingParameter|The input parameter "VSwitchId" that is mandatory for processing this request is not supplied.|The error message returned because the VSwitchId parameter is not specified.|
|400|InvalidDiskCategory.Mismatch|The specified disk categories' combination is not supported.|The error message returned because the combination of the specified disk types is not supported.|
|403|DeleteWithInstance.Conflict|The specified disk is not a portable disk and cannot be set to DeleteWithInstance attribute.|The error message returned because the specified disk is not portable and cannot be released along with the instance.|
|404|InvalidImageId.NotFound|The specified ImageId does not exist.|The error message returned because the specified image does not exist under this account. Check whether the image ID is valid.|
|403|InstanceDiskNumLimitExceed|The number of specified disk in an instance exceeds.|The error message returned because the number of disks in the instance has reached the upper limit.|
|403|IoOptimized.NotSupported|The specified image is not support IoOptimized Instance.|The error message returned because the specified image does not support I/O-optimized instances.|
|403|ImageNotSupportInstanceType|The specified image don't support the InstanceType instance.|The error message returned because the specified instance type is not supported for the specified image.|
|400|InvalidIoOptimizedValue.ValueNotSupported|IoOptimized value not supported.|The error message returned because the specified IoOptimized value is invalid.|
|404|OperationDenied|Another Instance has been creating|The error message returned because no new instances can be created while another instance is being created.|
|403|InvalidDiskSize.TooSmall|Specified disk size is less than the size of snapshot|The error message returned because the specified disk size is less than the snapshot size.|
|403|OperationDenied|The type of the disk does not support the operation|The error message returned because the specified disk type does not support the specified operation.|
|404|InvalidInstanceChargeType.NotFound|The InstanceChargeType does not exist in our records|The error message returned because the specified InstanceChargeType is invalid.|
|400|MissingParamter|The specified parameter "Period" is not null.|The error message returned because the Period parameter is not specified.|
|400|InvalidPeriod|The specified period is not valid.|The error message returned because the specified period is invalid.|
|403|InvalidDiskCategory.Mismatch|The specified disk categories combination is not supported.|The error message returned because the combination of the specified disk types is not supported.|
|403|IoOptimized.NotSupported|Vpc is not support IoOptimized instance.|The error message returned because the VPC does not support I/O-optimized instances.|
|400|InvalidDataDiskCategory.ValueNotSupported|The specified parameter " DataDisk.n.Category " is not valid.|The error message returned because the specified data disk category is invalid.|
|400|InstanceDiskCategoryLimitExceed|The specified DataDisk.n.Size beyond the permitted range, or the capacity of snapshot exceeds the size limit of the specified disk category.|The error message returned because the specified size of the data disk exceeds the upper limit or the size the snapshot exceeds the upper limit of the specified disk category.|
|403|OperationDenied|The resource is out of usage.|The error message returned because the instance is not in the running state. Start the instance or check whether the specified operation is valid.|
|403|QuotaExceed.BuyImage|The specified image is from the image market, You have not bought it or your quota has been exceeded.|The error message returned because you have not purchased the specified image from the marketplace or the total number of images you can own has reached the upper limit.|
|404|DependencyViolation.IoOptimized|The specified instancetype must be IoOptimized instance.|The error message returned because the specified instance type must be I/O-optimized. Check whether the instance type is valid.|
|404|PaymentMethodNotFound|No payment method has been registered on the account.|The error message returned because you have not registered the payment method for your account.|
|404|HOSTNAME\_ILLEGAL|hostname is not valid.|The error message returned because the specified hostname is invalid.|
|404|InvalidSystemDiskSize.LessThanImageSize|The specified parameter SystemDisk.Size is less than the image size.|The error message returned because the specified system disk size is less than the image size.|
|404|InvalidSystemDiskSize.LessThanMinSize|The specified parameter SystemDisk.Size is less than the min size.|The error message returned because the specified system disk size is less than the minimum capacity requirement.|
|404|InvalidSystemDiskSize.MoreThanMaxSize|The specified SystemDisk.Size parameter exceeds the maximum size.|The error message returned because the size of the specified system disk exceeds the maximum capacity that is allowed.|
|404|InvalidDataDiskSnapshotId.NotFound|The specified parameter DataDisk.n.SnapshotId is not valid.|The error message returned because the specified snapshot ID of the data disk is invalid.|
|403|InvalidVSwitchId.NotFound|The VSwitchId provided does not exist in our records.|The error message returned because the specified VSwitchId does not exist.|
|400|InvalidParameter|The specified vm bandwidth is not valid.|The error message returned because the specified virtual machine bandwidth is invalid.|
|400|InvalidSystemDiskCategory.ValueNotSupported|The specified parameter SystemDisk.Category is not valid.|The error message returned because the specified SystemDisk.Category is invalid.|
|403|InvalidParameter.ResourceOwnerAccount|ResourceOwnerAccount is Invalid.|The error message returned because the specified ResourceOwnerAccount is invalid.|
|404|InvalidSystemDiskSize|The specified parameter SystemDisk.Size is invalid.|The error message returned because the specified SystemDisk.Size parameter is invalid.|
|400|InvalidParameter.Bandwidth|The specified parameter Bandwidth is not valid.|The error message returned because the specified Bandwidth value is invalid.|
|400|InvalidIPAddress.AlreadyUsed|The specified IPAddress is already used by other resource.|The error message returned because other resources are currently using the specified IP address.|
|403|InvalidUserData.Forbidden|User not authorized to input the parameter "UserData", please apply for permission "UserData"|The error message returned because you are not authorized to configure user data.|
|400|InvalidUserData.SizeExceeded|The specified parameter "UserData" exceeds the size.|The error message returned because the UserData size exceeds the maximum.|
|400|InvalidUserData.NotSupported|The specified parameter "UserData" only support the vpc and IoOptimized Instance.|The error message returned because the specified UserData is only supported for VPC-connected and I/O-optimized instances.|
|403|Zone.NotOpen|The specified zone is not granted to you to buy resources yet.|The error message returned because you are not authorized to purchase resources in the specified zone.|
|403|Zone.NotOnSale|The specified zone is not available for purchase.|The error message returned because the requested instance resources are unavailable in the specified zone. Change the instance type or select a different zone.|
|403|InvalidClusterId.NotFound|The specified clusterId does not exist.|The error message returned because the specified ClusterId does not exist.|
|403|InvalidResourceType.NotSupported|This resource type is not supported; please try other resource types.|The error message returned because the instances of the specified resource type are not available.|
|403|InvalidInstanceType.ZoneNotSupported|The specified zone does not support this instancetype.|The error message returned because the specified instance type is not supported in the specified zone.|
|400|InstanceDiskNumber.LimitExceed|The total number of specified disk in an instance exceeds.|The error message returned because the number of disks in the instance has reached the upper limit.|
|400|Account.Arrearage|Your account has an outstanding payment.|The error message returned because your account has outstanding payments.|
|400|InvalidDiskCategory.ValueNotSupported|The specified parameter "DiskCategory" is not valid.|The error message returned because the specified DiskCategory is invalid.|
|400|InvalidAutoRenewPeriod.ValueNotSupported|The specified autoRenewPeriod is not valid.|The error message returned because the specified AutoRenewPeriod is invalid.|
|400|QuotaExceed.AfterpayInstance|The maximum number of Pay-As-You-Go instances is exceeded.|The error message returned because the number of pay-as-you-go instances has reached the upper limit.|
|400|InvalidSpotStrategy|The specified SpotStrategy is not valid.|The error message returned because the specified SpotStrategy parameter is invalid.|
|400|InvalidSpotParam.EmptyZoneID|The specified ZoneId is empty when SpotStrategy is set.|The error message returned because you did not specify ZoneId after you set the SpotStrategy parameter.|
|400|InvalidSpotPriceLimit|The specified SpotPriceLimitis not valid.|The error message returned because the specified SpotPriceLimit is invalid.|
|400|InvalidSpotDuration|The specified SpotDuration is not valid.|The error message returned because the specified SpotDuration is invalid.|
|400|InvalidSpotAuthorized|The specified Spot param is unauthorized.|The error message returned because you do not have the permission to create the preemptible instance.|
|400|InvalidSpotPrepaid|The specified Spot type is not support PrePay Instance.|The error message returned because the specified preemptible instance does not support the subscription billing method.|
|400|InvalidSpotAliUid|The specified UID is not authorized to use SPOT instance.|The error message returned because the specified UID does not have the permission to use preemptible instances.|
|403|InvalidPayMethod|The specified pay method is not valid.|The error message returned because the specified payment method is invalid.|
|403|OperationDenied.ImageNotValid|The specified Image is disabled or is deleted.|The error message returned because the specified image does not exist.|
|403|InvalidUserData.Base64FormatInvalid|The specified UserData is not valid|The error message returned because the specified UserData is invalid.|
|400|InvalidTagKey.Malformed|The specified Tag.n.Key is not valid.|The error message returned because the specified Tag.N.Key parameter is invalid.|
|400|InvalidParameter.Bandwidth|%s|The error message returned because the bandwidth parameter is not supported.|
|400|InvalidDataDiskCategory.ValueNotSupported|%s|The error message returned because the specified data disk category is not supported.|
|400|InvalidSystemDiskCategory.ValueNotSupported|%s|The error message returned because the specified system disk category is not supported.|
|400|InvalidParameter.Conflict|%s|The error message returned because one specified parameter conflicts with another specified parameter.|
|400|InvalidInternetChargeType.ValueNotSupported|%s|The error message returned because the specified InternetChargeType is not supported.|
|400|InvalidInstanceType.ValueNotSupported|%s|The error message returned because the specified instance type is invalid.|
|403|InstanceType.Offline|%s|The error message returned because the specified instance type is unavailable.|
|400|RegionUnauthorized|%s|The error message returned because the specified region is not supported.|
|500|InternalError|%s|The error message returned because an unknown internal error occurs.|
|400|Zone.NotOnSale|%s|The error message returned because the specified zone is disabled.|
|400|InvalidSystemDiskSize.ValueNotSupported|%s|The error message returned because the specified system disk size is invalid.|
|400|InvalidDataDiskSize.ValueNotSupported|%s|The error message returned because the specified data disk size is invalid.|
|404|InvalidKeyPairName.NotFound|The specified parameter "KeyPairName" does not exist in our records.|The error message returned because the specified KeyPairName does not exist.|
|403|DependencyViolation.WindowsInstance|The instance creating is window, cannot use ssh key pair to login.|The error message returned because SSH key pairs are not supported for Windows instances.|
|400|InvalidInstanceType.ValueNotSupported|The specified parameter "KeyPairName" only support IoOptimized Instance.|The error message returned because only I/O-optimized instances support SSH key pairs.|
|403|RealNameAuthenticationError|Your account has not passed the real-name authentication yet.|The error message returned because you failed to complete real-name authentication.|
|403|InvalidNetworkType.MismatchRamRole|Ram role cannot be applied to instances of Classic network type.|The error message returned because an instance RAM role can only be used for VPC-connected instances, but not for classic network-connected instances.|
|403|InvalidUser.PassRoleForbidden|The RAM user does not have the privilege to pass a RAM role.|The error message returned because the RAM user is not authorized to pass the RAM role.|
|404|InvalidRamRole.NotFound|The specified RAMRoleName does not exist.|The error message returned because the specified RAM role name does not exist.|
|400|OperationDenied|The specified InstanceType or Zone is not available or not authorized.|The error message returned because the specified instance type or zone is unavailable or unauthorized.|
|403|InvalidAccountStatus.NotEnoughBalance|Your account does not have enough balance.|The error message returned because your account has insufficient balance to pay for the service. Top up your account and try again.|
|500|InternalError|The request processing has failed due to some unknown error, exception or failure.|The error message returned because an internal error has occurred.|
|404|InvalidResourceGroup.NotFound|The ResourceGroup provided does not exist in our records.|The error message returned because the resource group does not exist.|
|403|IncorrectVpcStatus|Current VPC status does not support this operation.|The error message returned because the operation is not supported while the VPC is in the current state.|
|400|InvalidParameter.EncryptedIllegal|%s|The error message returned because the parameter is not supported for encrypted disks.|
|400|InvalidParameter.EncryptedNotSupported|%s|The error message returned because the parameter is not supported for encrypted disks.|
|400|EncryptedOption.Conflict|%s|The error message returned because the parameter is not supported for encrypted disks.|
|400|InvalidParameter.Encrypted.KmsNotEnabled|The encrypted disk need enable KMS|The error message returned because Key Management Service \(KMS\) has not been activated. KMS must be activated to encrypt disks.|
|400|InvalidSpotPriceLimit.LowerThanPublicPrice|The specified parameter "soptPriceLimit" can't be lower than current public price.|The error message returned because the specified SpotPriceLimit is lower than the current price.|
|400|InvalidHpcClusterId.Unnecessary|The specified HpcClusterId is unnecessary.|The error message returned because the specified HpcClusterId is invalid.|
|400|InvalidVSwitchId.Necessary|The VSwitchId is necessary.|The error message returned because VSwitchId is not specified.|
|400|InvalidHpcClusterId.Necessary|The HpcClusterId is necessary.|The error message returned because HpcClusterId is not specified.|
|400|InvalidHpcClusterId.NotFound|The specified HpcClusterId is not found.|The error message returned because the specified HPC cluster ID does not exist.|
|400|InvalidHpcClusterId.Creating|The specified HpcClusterId is creating.|The error message returned because the specified HPC cluster is being created.|
|400|QuotaExceeded.PrivateIpAddress|Don't have enough private IPs in this switch.|The error message returned because the specified VSwitch has no available private IP addresses to create the instance.|
|400|InvalidPeriodUnit.ValueNotSupported|The specified parameter PeriodUnit is not valid.|The error message returned because the specified PeriodUnit is invalid.|
|400|IncorrectImageStatus|Encrypted snapshots do not support this operation.|The error message returned because the operation is not supported on encrypted snapshots.|
|400|InvalidTagValue.Malformed|The specified Tag.n.Value is not valid.|The error message returned because the specified Tag.N.Value is invalid.|
|400|InvalidSecurityGroup.NotInDefaultVpc|%s|The error message returned because the specified security group is not associated with the default VPC.|
|400|VpcNotFound|Vpc is not found according to the specified VSwitch or the vpc does not belong to you.|The error message returned because the specified VPC does not exist.|
|403|InvalidParameter.NotMatch|%s|The error message returned because one specified parameter conflicts with another specified parameter.|
|403|OperationDenied.InvalidNetworkType|%s|The error message returned because the specified network type is not supported.|
|400|InvalidSpotInterruptionBehavior|%s|The error message returned because the specified SpotInterruptionBehavior is invalid.|
|403|InvalidSpotInterruptionBehavior.ClassicNetworkNotSupport|The specified SpotInterruptionBehavior does not support Classic network Instance.|The error message returned because the SpotInterruptionBehavior parameter is only applicable to VPC-connected preemptible instances, but not classic network-connected instances.|
|403|InvalidSpotInterruptionBehavior.LocalDiskNotSupport|The specified SpotInterruptionBehavior does not support local disk instance.|The error message returned because preemptible instances does not support local disks.|
|400|OperationDenied.IllegalPaymentPolicy|The current payment policy is illegal, please connect your service provider to authenticate relative agreement.|The error message returned because the current payment policy is not supported.|
|400|InvalidDeploymentOnHost|%s|The error message returned because dedicated hosts are not supported in the specified deployment set.|
|400|InvalidInstanceChargeType.NotSupport|The Dedicated host not support the specified Instance charge type.|The error message returned because the billing method is not supported for dedicated hosts.|
|400|InvalidNetworkType.NotSupported|The classic networkType not support create ECS on dedicatedHost|The error message returned because the classic network is not supported for dedicated hosts.|
|400|InvalidDedicatedHostId.NotFound|The specified DedicatedHostId does not exist.|The error message returned because the specified dedicated host ID does not exist.|
|400|InvalidDedicatedHostStatus.NotSupport|Operation denied due to dedicated host status.|The error message returned because the operation is not supported while the dedicated host is in the current state.|
|400|IncorrectDedicatedHostStatus|The current status of the resource does not support this operation.|The error message returned because the operation is not supported while the dedicated host is in the current state.|
|400|ChargeTypeViolation.PostPaidDedicatedHost|Prepaid instance onto postpaid dedicated host is not allowed|The error message returned because you cannot change the billing method for instances that are on a dedicated host.|
|400|InvalidPeriod.ExceededDedicatedHost|Instance expired date can't exceed dedicated host expired date.|The error message returned because the expiration date of the instance is later than that of the dedicated host.|
|400|InvalidInstanceType.ValueUnauthorized|The specified InstanceType is not authorize.|The error message returned because you are not authorized to use this instance type.|
|400|DedicatedHostType.Unmatched|The specified DedicatedHostType doesn? t match the instance type.|The error message returned because dedicated hosts do not support preemptible instances.|
|400|ChargeTypeViolation.PostPaidDedicatedHost|Prepaid instance onto postpaid dedicated host is not allowed.|The error message returned because you cannot change the billing method for instances that are on a dedicated host.|
|403|OperationDenied.ImageNotValid|%s|The error message returned because the specified image does not support this operation.|
|403|QuotaExceed.PostPaidDisk|Living postPaid disks quota exceeded.|The error message returned because the number of pay-as-you-go disks has reached the upper limit.|
|403|QuotaExceed.DeploymentSetInstanceQuotaFull|instance quota in one deployment set exceeded.|The error message returned because the number of instances in the current deployment set has reached the upper limit.|
|403|InvalidDiskCategory.NotSupported|The specified disk category is not supported.|The error message returned because the specified disk category is not supported.|
|403|InvalidVSwitch.DefaultVSwitchNotSupport|The specified zone in vpc can't support create default vSwitch.|The error message returned because the default VSwitch is not supported for VPCs of the specified zone.|
|400|InvalidParameter.CreditSpecification|The specified CreditSpecification is not supported in this region.|The error message returned because the specified CreditSpecification is not supported in this region.|
|400|IncorrectImageStatus|The specified Image is not available.|The error message returned because the status of the specified source image is invalid.|
|403|OperationDenied.ImageNotValid|the specified image is not published in the region.|The error message returned because the specified image is not available in the current region.|
|403|OperationDenied.ImageNotValid|the specified image is not found in marketplace.|The error message returned because the specified image is not available in the image marketplace.|
|404|InvalidMarketImage.NotFound|The specified marketplace image does not exist, please change the imageId and try again.|The error message returned because the specified image is not available in the image marketplace.|
|400|InvalidInstanceType.NotSupported|The specified instanceType is not supported by the deployment set.|The error message returned because the specified instance type is not supported in the specified deployment set.|
|400|InvalidVpcZone.NotSupported|Zone of the specified VSwitch is not available for creating, please try in other zones.|The error message returned because the default VSwitch is not supported for VPCs of the specified zone.|
|400|IncorrectDefaultVpcStatus|The status of the default VPC is invalid.|The error message returned because the status of the default VPC is invalid.|
|404|DeploymentSet.NotFound|The specified deployment set does not exist.|The error message returned because the specified deployment set does not exist.|
|403|OperationDenied.LocalDiskUnsupported|The configuration change is not allowed when the specified instance has local disks mounted.|The error message returned because configuration changes are not supported for instances with local disks attached.|
|403|OperationDenied.InconsistentNetwork|The specified security group and vswitch are not in the same vpc.|The error message returned because the security group and the VSwitch must share the same VPC.|
|403|OperationDenied|If the network segment of the vswitch is the same as that of its VPC. Therefore, the VPC cannot create other vswitchs across the region.|The error message returned because the VPC and VSwitch have the same CIDR block and no additional VSwitches can be created for other zones of this VPC.|
|403|DefaultVswitch.Existed|The default vswitch for VPC already exists.|The error message returned because the default VSwitch has been created for the VPC.|
|403|IncorrectInstanceStatus|The current status of the resource does not support this operation.|The error message returned because the operation is not supported while the dedicated host is in the current state.|
|403|CategoryViolation|The specified instance does not support this operation because of its disk category.|The error message returned because the configurations of instances with local disks attached cannot be upgraded or downgraded.|
|403|ResourcesNotInSameZone|The specified instance and dedicated host are not in the same zone.|The error message returned because the instance and the dedicated host must be in the same region.|
|403|InvalidRegion.NotSupport|The specified region does not support byok.|The error message returned because BYOK encryption is not supported in this region.|
|403|UserNotInTheWhiteList|The user is not in byok white list.|The error message returned because you are not authorized to use BYOK encryption.|
|400|InvalidParameter.EncryptedIllegal|The specified parameter Encrypted must be true when kmsKeyId is not empty.|The error message returned because the DataDisk.N.Encrypted parameter is not specified after you set the KmsKeyId parameter.|
|400|IoOptimized.NotSupported|The specified instance must be IoOptimized instance when kmsKeyId is not empty.|The error message returned because I/O-optimized instances are not used after you set KmsKeyId.|
|404|InvalidParameter.KMSKeyId.NotFound|The specified KMSKeyId does not exist.|The error message returned because the specified KMSKeyId does not exist.|
|403|InvalidParameter.KMSKeyId.KMSUnauthorized|ECS service have no right to access your KMS.|The error message returned because ECS is not authorized to access your KMS resources.|
|403|SecurityRisk.3DVerification|We have detected a security risk with your default credit or debit card. Please proceed with verification via the link in your email.|The error message returned because your payment method has security risks. You can troubleshoot the issue by following the provided instructions.|
|403|InvalidDisk.SystemDiskSize|The specified SystemDiskSize beyond the permitted range.|The error message returned because the maximum size of the specified system disk is reached.|
|400|InvalidClientToken.ValueNotSupported|The ClientToken provided is invalid.|The error message returned because the specified ClientToken is invalid.|
|400|OperationDenied|The current user does not support this operation.|The error message returned because the current user is not authorized to perform this operation.|
|403|InsufficientBalance|Your account does not have enough balance.|The error message returned because your account has insufficient balance. Top up your account and try again.|
|400|Duplicate.TagKey|The Tag.N.Key contain duplicate key.|The error message returned because the specified tag key is not unique.|
|400|InvalidParam.Tenancy|The specified Tenancy is invalid.|The error message returned because the specified Tenancy parameter is invalid.|
|404|InvalidSecurityGroupId.NotFound|%s|The error message returned because the specified security group ID does not exist.|
|403|InvalidVSwitchId.IpInvalid|%s|The error message returned because the specified private IP address is invalid.|
|404|InvalidDiskIds.NotPortable|The specified DiskId is not portable.|The error message returned because the specified disk is not portable.|

For more information about error codes, see [Error codes](https://error-center.alibabacloud.com/status/product/Ecs).

