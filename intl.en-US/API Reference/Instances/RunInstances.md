# RunInstances {#doc_api_Ecs_RunInstances .reference}

You can call this operation to create one or more pay-as-you-go or subscription Elastic Compute Service \(ECS\) instances.

## Description {#description .section}

Before you create an instance, you can call the [DescribeAvailableResource](~~66186~~) operation to view the available resources in the specified region or zone.

Before you create an instance, we recommend that you learn more about the ECS billing methods. When you create an ECS instance, fees may apply for additional resources used by the instance. For more information, see [Billing overview](~~25398~~).

When you call this operation, you must note the following:

-   You can create a maximum of 100 instances at a time.
-   You can use the `AutoReleaseTime` parameter to set the automatic release time of the instances.
-   After an instance is created, you can go back to the instance list and call the [DescribeInstances](~~25506~~) operation to check the status of the new instance.
-   Before you create an instance, make sure that you have created a security group. For more information, see [CreateSecurityGroup](~~25553~~).
-   An instance automatically starts after it is created. It is ready to use when it is in the `Running` state.
-   Before creating a VPC-connected instance, you must [create a VPC](~~65430~~) in the same region.
-   The [CreateInstance](~~25499~~) operation does not automatically allocate a public IP address for the created instance. However, the `RunInstances` operation automatically allocates public IP addresses for the created instances if the value of `InternetMaxBandwidthOut` is greater than 0.
-   After you call this operation, an error is returned if the parameters are invalid or no resource is available. For more information, see the Error codes section of this topic.

 **Best practices** 

`RunInstances` is able to create multiple instances. To better organize and manage your instances, we recommend that you set tags for the instances \(`Tag.N.Key` and `Tag.N.Value`\), and append hostnames \(`HostName`\) and instance names \(`InstanceName`\) with ordered suffixes \(`UniqueSuffix`\).

An instance launch template automatically specifies parameters that are needed to create an instance. You can call the [CreateLaunchTemplate](~~74686~~) operation to create an instance launch template. Then, when you can call the `RunInstances` operation, you can specify `LaunchTemplateId` and `LaunchTemplateVersion` to use the launch template.

In the [ECS console](https://partners-intl.console.aliyun.com/#/ecs), you can view the best practices for calling the `RunInstances` operation when you create an ECS instance. On the Preview page, click View Open API in the Configurations Selected section. On the left side of the dialog box, the **API Workflow** pane displays the operations and request parameters that are associated with the `RunInstances` operation. On the right side, SDK examples in **Java** and **Python** are provided.

## Debugging {#api_explorer .section}

[OpenAPI Explorer automatically calculates the signature value. For your convenience, we recommend that you call this operation in OpenAPI Explorer. OpenAPI Explorer dynamically generates the sample code of the operation for different SDKs.](https://api.aliyun.com/#product=Ecs&api=RunInstances&type=RPC&version=2014-05-26)

## Request parameters {#parameters .section}

|Parameter|Type|Required|Example|Description|
|---------|----|--------|-------|-----------|
|RegionId|String|Yes|cn-hangzhou| The region ID of the instance. You can call the [DescribeRegions](~~25609~~) operation to query the latest region list.

 |
|Action|String|No|RunInstances| The operation that you want to perform. Set the value to RunInstances. For HTTP and HTTPS requests, the `Action` parameter is required. Set this parameter to RunInstances.

 |
|ZoneId|String|No|cn-hangzhou-g| The zone ID of the instance. You can call the [DescribeZones](~~25610~~) operation to query the latest zone list.

 If you do not specify a zone ID, the system randomly selects a zone.

 |
|ImageId|String|No|win2008r2\_64\_ent\_sp1\_en-us\_40G\_alibase\_20170915.vhd| The ID of the image to create the instance. You can call the [DescribeImages](~~25534~~) operation to view the available image resources. If you do not specify `LaunchTemplateId` or `LaunchTemplateName` to set the launch template, you must specify the `ImageId` parameter.

 |
|SecurityGroupId|String|No|sg-bp15ed6xe1yxeycg7o\*\*\*| The ID of the security group to which the instances belong. Instances in the same security group can communicate with each other. One security group can contain a maximum of 1,000 instances.

 **Note:** The SecurityGroupId parameter determines the network type of its instances. For example, a security group of the VPC type can only contain VPC-connected instances and you must also specify the VSwitchId parameter to create these instances.

 If you do not specify `LaunchTemplateId` or `LaunchTemplateName` to set the launch template, you must specify the `SecurityGroupId` parameter.

 |
|VSwitchId|String|No|vsw-bp1s5fnvk4gn2tws03\*\*\*| The ID of the VSwitch. It must be specified when you create VPC-connected instances.

 |
|InstanceType|String|No|ecs.g5.large| The type of the instance. For more information, see [Instance families](~~25378~~) or call the [DescribeInstanceTypes](~~25620~~) operation to query the list of the latest instance types.

 If you do not specify `LaunchTemplateId` or `LaunchTemplateName` to set the launch template, you must specify the `InstanceType` parameter.

 |
|InternetMaxBandwidthIn|Integer|No|200| The maximum inbound bandwidth for Internet traffic. Unit: Mbit/s. Valid values: 1 to 200

 Default value: 200

 |
|InternetMaxBandwidthOut|Integer|No|5| The maximum outbound bandwidth for Internet traffic. Unit: Mbit/s. Valid values: 0 to 100

 Default value: 0

 |
|InstanceName|String|No|k8s-node-\[1,4\]-alibabacloud| The name of the instance. The name must be 2 to 128 characters in length. It must start with a letter, but cannot start with http:// or https://. It can contain letters, digits, colons \(:\), underscores \(\_\), periods \(.\), and hyphens \(-\). The default value is set to the `InstanceId` of the instance.

 **Note:** When you create multiple ECS instances, you can use `UniqueSuffix` to specify different names for the instances. You can also use the `name_prefix[begin_number,bits]name_suffix` format to name the instances in a numeric order. For example, you can set `InstanceName` to `k8s-node-[1,4]-alibabacloud` and the name of the first instance to `k8s-node-0001-alibabacloud`. For more information, see [API FAQ](~~122617#howToAddSequentialSuffix~~).

 When you do not add suffixes `name_suffix` to the instance names or the hostnames, and instead use the `name_prefix[begin_number,bits]` format, the `UniqueSuffix` parameter is ignored. For example, when you set `InstanceName` to `instance-[99,3]` and `UniqueSuffix` to `true`, the resulting instance name is `instance099` instead of `instance099001`.

 |
|HostName|String|No|k8s-node-\[1,4\]-ecshost| The hostname of the instance.

 -   It cannot start or end with a period \(.\) or a hyphen \(-\). It cannot contain consecutive periods \(.\) or hyphens \(-\).
-   For Windows, the hostname must be 2 to 15 characters in length. The hostname cannot contain periods \(.\) or only contain digits. It can contain letters, digits, and hyphens \(-\).
-   For other operating systems such as Linux, the hostname must be 2 to 64 characters in length. It can be segments separated with periods \(.\). Each segment can contain letters, digits, and hyphens \(-\).

 **Note:** When you create multiple ECS instances, you can use `UniqueSuffix` to specify different names for the instances. You can also use the `name_prefix[begin_number,bits]name_suffix` format to name the instances in a numeric order. For example, you can set `HostName` to `k8s-node-[1,4]-ecshost` and the name of the first instance to `k8s-node-0001-ecshost`. For more information, see [API FAQ](~~122617#howToAddSequentialSuffix~~).

 When you do not add suffixes `name_suffix` to the instance names or the hostnames, and instead use the `name_prefix[begin_number,bits]` format, the `UniqueSuffix` parameter is ignored. For example, when you set `InstanceName` to `instance-[99,3]` and set `UniqueSuffix` to `true`, the resulting instance name is `instance099` instead of `instance099001`.

 |
|UniqueSuffix|Boolean|No|true| Specifies whether to add sequential suffixes to `HostName` and `InstanceName`. The sequential suffix ranges from 001 to 999. For example, the names can be `LocalHost001`, `LocalHost002` and `MyInstance001`, `MyInstance002`. Default value: false

 |
|Description|String|No|FinanceDept| The description of the instance. It must be 2 to 256 characters in length and cannot start with http:// or https://.

 |
|PasswordInherit|Boolean|No|false| Specifies whether to use the password that is predefined in the image. If the PasswordInherit parameter is set to true, the Password parameter must not be specified. You must ensure that the selected image has a password configured.

 |
|Password|String|No|EcsV587!| The password for the instance. It must be 8 to 30 characters in length. It must include at least three of the following characters types: uppercase letters, lowercase letters, digits, and special characters. Special characters include:

 ``` {#codeblock_zn5_c3f_k7c}

( ) ` ~ ! @ # $ % ^ & * - _ + = \ | { } [ ] : ; ' < > , . ? /

```

 Passwords for Windows instances cannot start with a forward slash \(/\).

 **Note:** If the `Password` parameter is specified, we recommend that you send requests over the HTTPS protocol to ensure the security of your password.

 |
|KeyPairName|String|No|Instancetest| The name of the key pair.

 -   For Windows instances, ignore this parameter. Default value: null The `Password` parameter is still used if the KeyPairName parameter is specified.
-   For Linux instances, password authentication is disabled by default.

 |
|SystemDisk.Size|String|No|40| The size of the system disk. Unit: GiB. Valid values: 20 to 500

 The parameter value must be a minimum of 20 and greater than or equal to the size of the image. Default value: 40 or the size of the image, depending on whichever is greater

 |
|SystemDisk.Category|String|No|cloud\_ssd| The category of the system disk. The default value for [retired instance types](~~55263~~) without I/O optimizations is cloud. The default value for other types of instances is cloud\_efficiency. Valid values:

 -   cloud: basic disk
-   cloud\_efficiency: ultra disk
-   cloud\_ssd: standard SSD
-   ephemeral\_ssd: local SSD
-   cloud\_essd: enhanced SSD \(ESSD\)

 |
|SystemDisk.DiskName|String|No|cloud\_ssdSystem| The name of the system disk. It must be 2 to 128 characters in length. It must start with a letter and cannot start with http:// or https://. It can contain letters, digits, colons\(:\), underscores \(\_\), and hyphens \(-\). Default value: null

 |
|SystemDisk.Description|String|No|FinanceDept| The description of the system disk. It must be 2 to 256 characters in length and cannot start with http:// or https://.

 |
|DataDisk.N.Size|Integer|No|2000| The size of Nth data disk. Valid values of N: 1 to 16. Unit: GiB. Valid values:

 -   cloud: 5 to 2,000
-   cloud\_efficiency: 20 to 32,768
-   cloud\_ssd: 20 to 32,768
-   cloud\_essd: 20 to 32,768
-   ephemeral\_ssd: 5 to 800

 The value of this parameter must be equal to or greater than the snapshot size specified by the `SnapshotId` parameter.

 |
|DataDisk.N.SnapshotId|String|No|s-bp17441ohwka0yuhx\*\*\*| The ID of the snapshot used to create the Nth data disk. Valid values of N: 1 to 16 If the `DataDisk.N.SnapshotId` parameter is specified, the `DataDisk.N.Size` parameter is ignored, and the size of the created disk is the size of the specified snapshot. Snapshots created on or before July 15, 2013 are not applicable. Otherwise, an error will be returned and your request will be rejected.

 |
|DataDisk.N.Category|String|No|cloud\_ssd| The category of the Nth data disk. Valid values:

 -   cloud: basic disk. This is the default value.
-   cloud\_efficiency: ultra disk
-   cloud\_ssd: standard SSD
-   ephemeral\_ssd: local SSD
-   cloud\_essd: enhanced SSD \(ESSD\)

 |
|DataDisk.N.Encrypted|String|No|false| Specifies whether the Nth data disk is encrypted. Default value: false

 |
|DataDisk.N.KMSKeyId|String|No|0e478b7a-4262-4802-b8cb-00d3fb408\*\*\*| The customer master key ID that is provided by Key Management Service \(KMS\) for the Nth data disk.

 |
|DataDisk.N.DiskName|String|No|cloud\_ssdData| The name of the Nth data disk. It must be 2 to 128 characters in length. It must start with a letter and cannot start with http:// or https://. It can contain letters, digits, colons\(:\), underscores \(\_\), and hyphens \(-\). Default value: null

 |
|DataDisk.N.Description|String|No|FinanceDept| The description of the Nth data disk. It must be 2 to 256 characters in length and cannot start with http:// or https://.

 |
|DataDisk.N.Device|String|No|/dev/vda| The mount point of the Nth data disk.

 **Note:** This parameter is deprecated and will be later removed. we recommend that you use other parameters to ensure maximum compatibility.

 |
|DataDisk.N.DeleteWithInstance|Boolean|No|true| Specifies whether the Nth data disk is released along with the instance. Default value: true

 |
|IoOptimized|String|No|optimized| Specifies whether the instance is an I/O optimized instance. The default value for [retired instance types](~~55263~~) is none. The default value for other instances is optimized. Valid values:

 -   none: The instance is not I/O optimized.
-   optimized: The instance is I/O optimized.

 |
|NetworkInterface.N.PrimaryIpAddress|String|No|172.16.236.\*\*\*| The primary IP address of the secondary ENI. Valid values of N: 1

 **Note:** You can only attach one secondary ENI when you create an ECS instance. You can call [CreateNetworkInterface](~~58504~~) and [AttachNetworkInterface](~~58515~~) to attach additional secondary ENIs.

 The default value is an IP address that is randomly selected from the VSwitch to which the ENI belongs.

 |
|NetworkInterface.N.VSwitchId|String|No|vsw-vswitchid2| The ID of the VSwitch to which the secondary ENI belongs. Valid values of N: 1

 The default value is the VSwitch to which the ECS instance belongs.

 |
|NetworkInterface.N.SecurityGroupId|String|No|sg-securitygroupid2| The ID of the security group to which the secondary ENI belongs. Valid values of N: 1

 The default value is the ID of the security group to which the instance belongs.

 |
|NetworkInterface.N.NetworkInterfaceName|String|No|FinanceJoshua| The name of the secondary ENI. Valid values of N: 1

 |
|NetworkInterface.N.Description|String|No|FinanceDept| The description of the secondary ENI. Valid values of N: 1 The description must be 2 to 256 characters in length and cannot start with http:// or https://.

 |
|RamRoleName|String|No|FinanceDept| The RAM role name of the instance. You can call the [ListRoles](~~28713~~) operation provided by RAM to query the RAM roles that you have created.

 |
|UserData|String|No|ZWNobyBoZWxsbyBlY3Mh| The user data of the instance. It must be encoded in Base64. The maximum size for the raw data is 16 KB.

 |
|MinAmount|Integer|No|2| The minimum number of the specified instances to purchase. Valid values: 1 to 100

 -   If the number of available ECS instances is less than the MinAmount value, the operation fails.
-   If the number of available ECS instances is greater than or equal to the MinAmount value, the number of instances that are created equals the total available instances.

 |
|Amount|Integer|No|3| The number of instances you want to create. Valid values: 1 to 100

 Default value: 1

 |
|SpotPriceLimit|Float|No|0.97| The maximum hourly price for the preemptible instance. This parameter supports a maximum of three decimal places and takes effect when the `SpotStrategy` parameter is set to `SpotWithPriceLimit`.

 |
|SpotStrategy|String|No|NoSpot| The bidding mode of the pay-as-you-go instance. This parameter is valid when `InstanceChargeType` is set to `PostPaid`. Valid values:

 -   NoSpot: a standard pay-as-you-go instance. This is the default value.
-   SpotWithPriceLimit: a preemptible instance with an upper price limit.
-   SpotAsPriceGo: a preemptible instance that is billed based on the actual market price.

 |
|SpotInterruptionBehavior|String|No|Terminate| The interruption mode of the preemptible instance. Only the Terminate mode is supported. The instance is automatically released. This is the default value.

 |
|CreditSpecification|String|No|Standard| Specifies the performance mode of the t5 burstable instance. Valid values:

 -   Standard: the Standard mode. For more information, see the Standard mode section of [Burstable instances](~~59977~~).
-   Unlimited: the Unlimited mode. For more information, see the Unlimited mode section of [Burstable instances](~~59977~~).

 Default value: null

 |
|SecurityEnhancementStrategy|String|No|Active| Specifies whether to enable security enhancement. Valid values:

 -   Active: enables security enhancement. It is only applicable to public images.
-   Deactive: disables security enhancement for all image types.

 |
|DeploymentSetId|String|No|ds-bp1brhwhoqinyjd6t\*\*\*| The ID of the deployment set.

 |
|DedicatedHostId|String|No|dh-dedicatedhost1| The ID of the dedicated host for the ECS instance. You can call the [DescribeDedicatedHosts](~~94572~~) operation to view the dedicated host list.

 No preemptible instance can be created on a dedicated host. Therefore, if you specify `DedicatedHostId`, the values of `SpotStrategy` and `SpotPriceLimit` is ignored.

 |
|Tag.N.Key|String|No|FinanceDept| The tag key of the instances, disks, and primary ENIs. Valid values of N: 1 to 20 It cannot be an empty string. It can be a maximum of 64 characters in length and cannot start with aliyun or acs:. It cannot contain http:// or https://.

 |
|Tag.N.Value|String|No|FinanceDept.Joshua| The tag value of the instances, disks, and primary ENIs. Valid values of N: 1 to 20 The tag value can be an empty string. It can be a maximum of 128 characters in length and cannot start with aliyun or acs:. It cannot contain http:// or https://.

 |
|HpcClusterId|String|No|hpc-clusterid| The ID of the E-HPC cluster to which the instance belongs.

 |
|ResourceGroupId|String|No|rg-resourcegroupid1| The ID of the resource group to which the instance belongs.

 |
|LaunchTemplateId|String|No|lt-bp1apo0bbbkuy0rj3\*\*\*| The ID of the launch template. For more information, call the [DescribeLaunchTemplates](~~73759~~) operation.

 You must specify either `LaunchTemplateId` or `LaunchTemplateName` to set a launch template.

 |
|LaunchTemplateName|String|No|JoshuaWinPostPaid| The name of the launch template. You must specify either `LaunchTemplateId` or `LaunchTemplateName` to set a launch template.

 |
|LaunchTemplateVersion|Long|No|3| The version of the instance launch template. If you specify `LaunchTemplateId` or `LaunchTemplateName`, but not the version of the launch template, the default template version is used.

 |
|DeletionProtection|Boolean|No|false| Specifies whether you can use the ECS console or call the [DeleteInstance](~~25507~~) operation to release the instances. Valid values:

 -   true: enables release protection.
-   false: disables release protection. This is the default value.

 **Note:** This parameter is only applicable to pay-as-you-go instances. It can only protect against manual releases and is not supported for system releases.

 |
|AutoReleaseTime|String|No|2018-01-01T12:05:00Z| The time when the instance is automatically released. The time follows the [ISO 8601](~~25696~~) standard in UTC+0. The format is yyyy-MM-ddTHH:mm:ssZ.

 -   If the value of the seconds field \(`ss`\) is not `00`, the time will automatically be set to the start of the current minute \(`mm`\).
-   It must be at least 30 minutes after the current time.
-   The automatic release time must be less than 3 years from the current time.

 |
|InternetChargeType|String|No|PayByTraffic| The billing method of the network bandwidth. Valid values:

 -   PayByTraffic: The billing method is based on actual traffic. This is the default value.

 |
|Period|Integer|No|1| The subscription period of the instance. Unit: Months. The values that are valid for this parameter depend on the value specified in the PeriodUnit parameter. This parameter is only valid and required when the `InstanceChargeType` parameter is set to `PrePaid`. If the `DedicatedHostId` parameter is specified, the specified period cannot exceed the subscription period of the dedicated host. Valid values:

 -   `Week:`1, 2, 3, and 4.
-   `Month:`1, 2, 3, 4, 5, 6, 7, 8, 9, 12, 24, 36, 48, and 60.

 |
|AutoRenew|Boolean|No|true| Specifies whether to enable automatic renewal. This parameter is valid when `InstanceChargeType` is set to `PrePaid`. Valid values:

 -   true: enables automatic renewal for the instance.
-   false: disables automatic renewal for the instance. This is the default value.

 |
|PeriodUnit|String|No|Month| The unit of the billing cycle for the instance. Valid values:

 -   Week.
-   Month. This is the default value.

 |
|AutoRenewPeriod|Integer|No|1| The automatic renewal period of the instance. The values that are valid for this parameter depend on the value specified in the PeriodUnit parameter. Valid values:

 -   `Week:`1, 2, and 3.
-   `Month:`1, 2, 3, 6, 12, 24, 36, 48, and 60.

 Default value: 1

 |
|InstanceChargeType|String|No|PrePaid| The billing method of the instance. Valid values:

 -   PrePaid: The billing method is subscription.
-   PostPaid: The billing method is pay-as-you-go. This is the default value.

 |
|Ipv6AddressCount|Integer|No|1| The number of randomly generated IPv6 addresses that are allocated to the ENI.

 **Note:** You cannot specify both `Ipv6Addresses.N` and `Ipv6AddressCount` at the same time.

 |
|PrivateIpAddress|String|No|172.16.236.14X| The private IP address of the instance. This private IP address must be selected from the range defined by the CIDR block of the VSwitch.

 **Note:** When you specify `PrivateIpAddress`, the `Amount` parameter must be set to 1.

 |
|Ipv6Address.N|RepeatList|No|Ipv6Address.1=2001:db8:1234:1a00::\*\*\*| Allocates one or more IPv6 addresses to the ENI. Currently, the value of N must be 1. Example:`Ipv6Address.1=2001:db8:1234:1a00::***`

 **Note:** You cannot specify both `Ipv6Addresses.N` and `Ipv6AddressCount` at the same time.

 |
|DryRun|Boolean|No|false| Specifies whether to send a dry-run request.

 -   true: Only a dry-run request is sent and no instance is created. The system checks whether the required parameters are set, and validates the request format, service permissions, and available ECS instances. If the validation fails, the corresponding error code is returned. If the validation succeeds, the `DryRunOperation` error code is returned.
-   false: A request is sent. If the validation succeeds, the instance is created. This is the default value.

 |
|ClientToken|String|No|123e4567-e89b-12d3-a456-426655440000| The client token that is used to ensure the idempotence of the request. You can use your own methods to generate this value, but you must ensure that it is unique among different requests.**ClientToken** can only contain ASCII characters, and cannot exceed 64 characters in length. For more information, see [How to ensure idempotence](~~25693~~).

 |
|SecurityGroupIds.N|RepeatList|No|sg-bp15ed6xe1yxeycg7o\*\*\*| The list of security groups to which the instance belongs. The valid values for N are based on the maximum number of security groups that the specified instance supports. For more information, see [Security group limits](~~101348~~).

 **Note:** You cannot specify both SecurityGroupId and SecurityGroupIds.N at the same time.

 |
|SystemDisk.PerformanceLevel|String|No|PL1| The performance level of the system disk. Valid values:

 -   PL1: a single ESSD delivers up to 50,000 random read/write IOPS. This is the default value.
-   PL2: a single ESSD delivers up to 100,000 random read/write IOPS.
-   PL3: a single ESSD delivers up to 1,000,000 random read/write IOPS.

 For more information about ESSD performance levels, see [ESSD cloud disk](~~122389~~).

 |
|DataDisk.N.PerformanceLevel|String|No|PL2| The performance level of the Nth ESSD data disk. The value of N must be the same as that in `DataDisk.N.Category=cloud_essd`. Valid values:

 -   PL1: a single ESSD delivers up to 50,000 random read/write IOPS. This is the default value.
-   PL2: a single ESSD delivers up to 100,000 random read/write IOPS.
-   PL3: a single ESSD delivers up to 1,000,000 random read/write IOPS.

 For more information about ESSD performance levels, see [ESSD cloud disk](~~122389~~).

 |
|Affinity|String|No|default| Specifies whether an instance on a dedicated host is associated with the dedicated host. This parameter is applicable to instances with the No Charges After Instance Is Stopped feature enabled. Valid values:

 -   default: The instance is not associated with the dedicated host. If the associated dedicated host has insufficient resources after the stopped instance is restarted, the instance is automatically allocated to an alternative dedicated host.
-   host: The instance is associated with a specific dedicated host. The stopped instance still resides on the associated dedicated host after it is restarted. If the available resources of the original dedicated host are insufficient, the instance will fail to restart.

 Default value: default

 |
|Tenancy|String|No|default| Specifies whether to create an instance on a dedicated host. Valid values:

 -   default: creates an instance that is not on a dedicated host.
-   host: creates an instance that is on a dedicated host. If you do not specify the `DedicatedHostId` parameter, then ECS automatically selects a dedicated host for the instance.

 Default value: default

 |

## Response parameters {#resultMapping .section}

|Parameter|Type|Example|Description|
|---------|----|-------|-----------|
|InstanceIdSets| |\["i-instanceid1", "i-instanceid2", "i-instanceid3"\]| The list of instance IDs \(`InstanceId`\).

 |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E| The ID of the request.

 |

## Examples {#demo .section}

Sample requests

``` {#request_demo}
https://ecs.aliyuncs.com/?Action=RunInstances
&RegionId=cn-hangzhou
&InstanceType=ecs.cm4.6xlarge
&SecurityGroupId=sg-securitygroupid
&Amount=3
&<Common request parameters>
```

Sample success responses

`XML` format

``` {#xml_return_success_demo}
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

`JSON` format

``` {#json_return_success_demo}
{
	"RequestId":"04F0F334-1335-436C-A1D7-6C044FE73368",
	"InstanceIdSets":{
		"InstanceIdSet":[
			"i-instanceid1",
			"i-instanceid2",
			"i-instanceid3"
		]
	}
}
```

## Error codes {#section_2a3_57n_scd .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|400|InvalidInstanceType.ValueUnauthorized|The specified InstanceType is not authorized.|The error message returned because you are not authorized to use the specified instance type.|
|404|InvalidSecurityGroupId|The specified SecurityGroupId is invalid or does not exist.|The error message returned because the specified security group ID does not exist.|
|400|InvalidInstanceType.ValueNotSupported|The specified InstanceType beyond the permitted range.|The error message returned because the specified instance type is invalid.|
|404|InvalidSecurityGroupId.NotFound|The SecurityGroupId provided does not exist in our records.|The error message returned because the specified security group does not exist under this account. Check whether the security group ID is valid.|
|400|InvalidDescription.Malformed|The specified parameter "Description" is not valid.|The error message returned because the specified description is invalid. The description must be 2 to 256 characters in length and cannot start with http:// or https://.|
|400|InvalidInternetChargeType.ValueNotSupported|The specified InternetChargeType is not valid.|The error message returned because the specified InternetChargeType does not exist.|
|400|InvalidParameter|The specified parameter "InternetMaxBandwidthOut" is not valid.|The error message returned because the specified InternetMaxBandwidthOut is invalid.|
|400|InvalidHostName.Malformed|The specified parameter "HostName" is not valid.|The error message returned because the specified HostName is invalid.|
|403|InvalidParams.InstanceNameExceed|The uniqueSuffix takes three naming places, please shorten your InstanceName.|The error message returned because the specified InstanceName exceeds the maximum length. The UniqueSuffix parameter value occupies three character spaces.|
|403|InvalidParams.HostnameExceed|The uniqueSuffix takes three naming places, please shorten your Hostname.|The error message returned because the specified HostName exceeds the maximum length. The UniqueSuffix parameter value occupies three character spaces.|
|400|InvalidPassword.Malformed|The specified parameter "Password" is not valid.|The error message returned because the specified Password is invalid.|
|400|InvalidPasswordParam.Mismatch|The input password should be null when PasswdInherit is true.|The error message returned because if PasswdInherit is set to true, the Password parameter must not be specified.|
|400|InvalidSystemDiskCategory.ValueNotSupported|The specified parameter "SystemDisk.Category" is not valid.|The error message returned because the specified SystemDisk.Category is invalid.|
|400|InvalidDiskName.Malformed|The specified parameter "SyatemDisk.DiskName or DataDisk.n.DiskName" is not valid.|The error message returned because the system disk or data disk name is invalid. The name must be 2 to 128 characters in length. It can contain letters, digits, colons \(:\), underscores \(\_\), and hyphens \(-\). It must start with a letter and cannot start with http:// or https://.|
|400|InvalidDiskDescription.Malformed|The specified parameter "SyatemDisk.DiskDescription" or "DataDisk.n.Description" is not valid.|The error message returned because the specified SystemDisk.DiskDescription or DataDisk.N.Description is invalid.|
|400|InvalidDataDiskSize.ValueNotSupported|The specified DataDisk.n.Size beyond the permitted range, or the capacity of snapshot exceeds the size limit of the specified disk category.|The error message returned because the specified size of the data disk exceeds the upper limit or the size the snapshot exceeds the upper limit of the specified disk category.|
|400|InvalidDataDiskCategory.ValueNotSupported|The specified parameter "DataDisk.n.Category" is not valid.|The error message returned because the specified DataDisk.N.Category is invalid.|
|404|InvalidDataDiskSnapshotId.NotFound|The specified parameter DataDisk.n.SnapshotId is not valid.|The error message returned because the specified DataDisk.N.SnapshotId is invalid.|
|400|InvalidDataDevice.Malformed|The specified parameter "DataDisk.n.Device" is not valid.|The error message returned because the specified DataDisk.N.Device is invalid.|
|400|InvalidNodeControllerId.Malformed|The specified parameter "NodeControllerId" is not valid.|The error message returned because the specified NodeControllerId is invalid.|
|400|InvalidInnerIpAddress.Malformed|The specified parameter "InnerIpAddress" is not valid.|The error message returned because the specified InnerIpAddress is invalid.|
|400|InvalidInnerIpAddress.Unusable|The specified InnerIpAddress is already used or not found in usable ip range.|The error message returned because the specified InnerIpAddress is unavailable or invalid.|
|400|InvalidParameter.Conflict|The specified image does not support the specified instance type.|The error message returned because the specified image cannot be used for the specified instance type.|
|400|ImageNotSupportCloudInit|The specified image does not support cloud-init.|The error message returned because the specified image does not support cloud-init.|
|400|InvalidSnapshotId.BasedSnapshotTooOld|The specified snapshot is created before 2013-07-15.|The error message returned because the specified snapshot was created on or before July 15, 2013.|
|400|QuotaExceed.AfterpayInstance|Living afterpay instances quota exceeded.|The error message returned because the number of active pay-as-you-go instances has reached the upper limit.|
|403|ImageNotSubscribed|The specified image has not be subscribed.|The error message returned because you have not subscribed to the specified image in the marketplace.|
|403|InvalidSystemDiskCategory.ValueUnauthorized|The disk category is not authorized.|The error message returned because you are not authorized to use the specified disk category.|
|403|InvalidSnapshotId.NotReady|The specified snapshot has not completed yet.|The error message returned because the specified snapshot is being created.|
|403|InstanceDiskCategoryLimitExceed|The total size of specified disk category in an instance exceeds.|The error message returned because the total size of the specified disks exceeds the maximum capacity that is allowed for the disk category.|
|403|InvalidDevice.InUse|The specified device has been occupied.|The error message returned because the specified device has been mounted to a disk and is not available.|
|403|ImageRemovedInMarket|The specified market image is not available, Or the specified user defined image includes product code because it is based on an image subscribed from marketplace, and that image in marketplace includeing exact the same product code has been removed.|The error message returned because the specified marketplace image is unavailable.|
|404|InvalidClusterId.NotFound|The ClusterId provided does not exist in our records.|The error message returned because the specified ClusterId does not exist.|
|403|CategoryNotSupported|The specified zone does not offer the specified disk category.|The error message returned because the specified disk category is unavailable in the specified zone.|
|400|InvalidInstanceName.Malformed|The specified parameter "InstanceName" is not valid.|The error message returned because the format of the specified instance name is invalid. The name must be 2 to 128 characters in length. It can contain letters, digits, colons \(:\), underscores \(\_\), and hyphens \(-\). It must start with a letter and cannot start with http:// or https://.|
|400|InvalidDiskDescription.Malformed|The specified parameter "SyatemDisk.DiskDescription or DataDisk.n.Description" is not valid.|The error message returned because the specified SystemDisk.DiskDescription or DataDisk.N.Description is invalid.|
|403|QuotaExceed.PortableCloudDisk|The quota of portable cloud disk exceeds.|The error message returned because the number of portable disks has reached the upper limit.|
|500|InternalError|The request processing has failed due to some unknown error.|The error message returned because an internal error has occurred. Try again later. If the problem persists, open a ticket.|
|400|InvalidParameter.Conflict|The speicified region and cluster do not match.|The error message returned because the specified region does not match the specified cluster.|
|403|SecurityGroupInstanceLimitExceed|Exceeding the allowed amount of instances of a security group.|The error message returned because the number of instances in the security group has reached the upper limit.|
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
|403|Forbbiden|User not authorized to operate on the specified resource.|The error message returned because you are not authorized to perform operations on the specified resource.|
|403|DeleteWithInstance.Conflict|The specified disk is not a portable disk and cannot be set to DeleteWithInstance attribute.|The error message returned because the specified disk is not portable and cannot be released along with the instance.|
|404|InvalidImageId.NotFound|The specified ImageId does not exist.|The error message returned because the specified image does not exist under this account. Check whether the image ID is valid.|
|403|InstanceDiskNumLimitExceed|The number of specified disk in an instance exceeds.|The error message returned because the number of disks in the instance has reached the upper limit.|
|403|IoOptimized.NotSupported|The specified image is not support IoOptimized Instance.|The error message returned because the specified image does not support I/O-optimized instances.|
|404|IoOptimized.NotSupported|The specified instancetype is not support IoOptimized instance.|The error message returned because the specified instance type does not support I/O optimization.|
|403|InvalidDiskSize.TooSmall|Specified disk size is less than the size of snapshot|The error message returned because the specified disk size is less than the snapshot size.|
|404|InvalidInstanceChargeType.NotFound|The InstanceChargeType does not exist in our records|The error message returned because the specified instance type does not exist.|
|400|MissingParamter|The specified parameter "Period" is not null.|The error message returned because the RegionId parameter is not specified.|
|400|InvalidPeriod|The specified period is not valid.|The error message returned because the specified period is invalid.|
|403|InvalidDiskCategory.Mismatch|The specified disk categories combination is not supported.|The error message returned because the combination of the specified disk types is not supported.|
|403|IoOptimized.NotSupported|Vpc is not support IoOptimized instance.|The error message returned because the VPC does not support I/O-optimized instances.|
|400|InvalidDataDiskCategory.ValueNotSupported|The specified parameter " DataDisk.n.Category " is not valid.|The error message returned because the specified data disk type is invalid.|
|400|InvalidSystemDiskCategory.ValueNotSupported|The specified parameter " SystemDisk.Category " is not valid.|The error message returned because the specified system disk type is invalid.|
|403|InvalidDiskCategory.NotSupported|The specified disk category is not support the specified instance type.|The error message returned because the specified instance type does not support the specified disk category.|
|400|InstanceDiskCategoryLimitExceed|The specified DataDisk.n.Size beyond the permitted range, or the capacity of snapshot exceeds the size limit of the specified disk category.|The error message returned because the specified size of the data disk exceeds the upper limit or the size the snapshot exceeds the upper limit of the specified disk category.|
|403|QuotaExceed.BuyImage|The specified image is from the image market? You have not bought it or your quota has been exceeded.|The error message returned because the specified image has not been purchased or the number of images has reached the upper limit.|
|404|DependencyViolation.IoOptimized|The specified instancetype must be IoOptimized instance.|The error message returned because the specified instance type must be I/O-optimized. Check whether the instance type is valid.|
|404|PaymentMethodNotFound|No payment method has been registered on the account.|The error message returned because you have not registered the payment method for your account.|
|400|InvalidInstanceType.ValueNotSupported|InternetMaxBandwidthOut should be set.|The error message returned because the InternetMaxBandwidthOut parameter is not specified.|
|400|InvalidInstanceType.ValueNotSupported|instancetype is not valid.|The error message returned because the specified InstanceType parameter is invalid.|
|400|InvalidClientToken.ValueNotSupported|clienttoken is not valid.|The error message returned because the specified ClientToken is invalid.|
|400|InvalidIoOptimize.ValueNotSupported|The specified IoOptimize is not valid.|The error message returned because the specified I/O-optimized instance is invalid.|
|400|InvalidHostName.Malformed|The specified parameter HostName is not valid.|The error message returned because the specified HostName is invalid.|
|404|HOSTNAME\_ILLEGAL|hostname is not valid.|The error message returned because the specified hostname is invalid.|
|400|InvalidInternetMaxBandwidthOut.Malformed|The specified parameter internetMaxBandwidthOut is not valid.|The error message returned because the specified InternetMaxBandwidthOut is invalid.|
|400|InvalidInternetMaxBandwidthIn.Malformed|The specified parameter internetMaxBandwidthIn is not valid.|The error message returned because the specified InternetMaxBandwidthIn is invalid.|
|400|InvalidSnapshotId.NotFound|The specified parameter SnapshotId is not exist.|The error message returned because the specified snapshot does not exist. Check whether the snapshot ID is valid.|
|400|InvalidTagKey.Malformed|The specified Tag.n.Key is not valid.|The error message returned because the specified Tag.N.Key parameter is invalid.|
|400|InvalidTagValue.Malformed|The specified Tag.n.Value is not valid.|The error message returned because the specified Tag.N.Value parameter is invalid.|
|403|InvalidResourceId.NotSupported|The specified ResourceId does not support tagging.|The error message returned because the specified resource does not support tagging.|
|400|InvalidTag.Mismatch|The specified Tag.n.Key and Tag.n.Value are not match.|The error message returned because the specified Tag.N.Key and Tag.N.Value parameters do not correspond to each other.|
|400|InvalidTagCount|The specified tags are beyond the permitted range.|The error message returned when the number of specified tags has reached the upper limit.|
|400|InvalidMinAmount.Malformed|The specified parameter MinAmount is not valid.|The error message returned because the specified MinAmount is invalid. Check whether the value of this parameter is valid.|
|400|InvalidMaxAmount.Malformed|The specified parameter MaxAmount is not valid.|The error message returned because the specified MaxAmount is invalid.|
|400|InvalidAutoReleaseTime.Malformed|The specified parameter AutoReleaseTime is not valid.|The error message returned because the specified AutoReleaseTime is invalid. The time follows the ISO 8601 standard in UTC+0. The format is yyyy-MM-ddTHH:mm:ssZ.|
|400|InvalidPrivateIpAddress.Malformed|The specified parameter PrivateIpAddress is not valid.|The error message returned because the specified PrivateIpAddress is invalid.|
|400|InvalidInnerIpAddress.Malformed|The specified parameter InnerIpAddress is not valid.|The error message returned because the specified InnerIpAddress is invalid.|
|404|InvalidSystemDiskSize.LessThanImageSize|The specified parameter SystemDisk.Size is less than the image size.|The error message returned because the specified SystemDisk.Size is less than the image size.|
|404|InvalidSystemDiskSize.LessThanMinSize|The specified parameter SystemDisk.Size is less than the min size.|The error message returned because the specified system disk size is less than the minimum capacity requirement.|
|404|InvalidSystemDiskSize.MoreThanMaxSize|The specified parameter SystemDisk.Size is more than the max size|The error message returned because the specified SystemDisk.Size parameter is invalid.|
|403|OperationDenied|The specified RegionId does not support the creation of the network type ECS instance.|The error message returned because the ECS instance of the specified network type cannot be created in the specified region. Check whether this network type is available in the specified region.|
|400|OperationDenied.NoVlan|The specified parameter "VlanId" is not valid or vlan has not enough IP address.|The error message returned when the specified VLAN ID is invalid or the number of IP addresses in this VLAN has reached the upper limit.|
|403|OperationDenied.ImageNotValid|The specified Image is disabled or is deleted.|The error message returned because the specified image does not exist.|
|403|OperationDenied.SnapshotNotValid|The specified snapshot is not allowed to create disk.|The error message returned because the snapshot is invalid and you cannot create disks with the specified snapshot.|
|403|OperationDenied.SnapshotNotAllowed|The specified snapshot is not allowed to create disk.|The error message returned because the specified snapshot is not allowed to create disks.|
|403|OperationDenied.ZoneNotAllowed|The creation of Instance to the specified Zone is not allowed.|The error message returned because no instance can be created in the specified zone.|
|403|OperationDenied.ZoneSystemCategoryNotMatch|The specified Zone or cluster does not offer the specified disk category or the speicified zone and cluster do not match.|The error message returned because the specified disk category is unavailable in the specified zone or cluster, or because the specified zone and cluster do not correspond to each other.|
|403|OperationDenied.ResourceControl|The specified region is in resource control, please try later.|The error message returned because the specified region is in resource control. Try again later.|
|403|OperationDenied.NoStock|The resource is out of usage.|The error message returned because the instance is not in the running state. Start the instance or check whether the specified operation is valid.|
|403|OperationDenied.SnapshotParamsNotValid|The capacity of snapshot exceeds the size limit of the specified disk category or the specified category is not authorizied.|The error message returned because the snapshot size exceeds the size limit of the specified disk category or you are not authorized to use the specified disk type.|
|404|OperationDenied.CreatingConflict|Another Instance has been creating|The error message returned because no new instances can be created.|
|403|OperationDenied.DiskTypeNotSupport|The type of the disk does not support the operation|The error message returned because the specified operation is invalid.|
|400|OperationDenied.QuotaExceed|The quota of tags on resource is beyond permitted range.|The error message returned because the number of resource tags has reached the upper limit.|
|400|Account.Arrearage|Your account has been in arrears.|The error message returned because your account has insufficient balance. Top up your account and try again.|
|403|InvalidUserData.Forbidden|User not authorized to input the parameter "UserData", please apply for permission "UserData"|The error message returned because you are not authorized to configure user data.|
|400|InvalidUserData.SizeExceeded|The specified parameter "UserData" exceeds the size.|The error message returned because the UserData size exceeds the maximum.|
|400|InvalidUserData.NotSupported|TThe specified parameter "UserData" only support the vpc and IoOptimized Instance.|The error message returned because the specified UserData is only supported for VPC-connected and I/O-optimized instances.|
|400|InvalidUserData.NotSupported|The specified parameter "UserData" only support the vpc and IoOptimized Instance.|The error message returned because the specified UserData is only supported for VPC-connected and I/O-optimized instances.|
|400|InvalidUserData.Base64FormatInvalid|The specified UserData is not valid|The error message returned because the specified UserData is invalid.|
|404|InvalidZoneId.NotFound|The specified zoneId does not exist.|The error message returned because the specified zone ID does not exist.|
|403|Zone.NotOpen|The specified zone is not granted to you to buy resources yet.|The error message returned because you are not authorized to purchase resources in the specified zone.|
|403|Zone.NotOnSale|The resource in the specified zone is no longer available for sale. Please try other regions and zones.|The error message returned because no resources are available in the specified zone.|
|403|InvalidClusterId.NotFound|The specified clusterId does not exist.|The error message returned because the specified ClusterId does not exist.|
|403|InvalidResourceType.NotSupported|This resource type is not supported. Please try other resource types.|The error message returned because the specified resource type is not supported.|
|403|OperationDenied.NoStock|The resource is out of stock in the specified zone. Please try other types, or choose other regions and zones.|The error message returned because no resources are available in the specified zone.|
|403|InvalidInstanceType.ZoneNotSupported|The specified zone does not support this instancetype.|The error message returned because the specified instance type is not supported in the specified zone.|
|400|InstanceDiskNumber.LimitExceed|The total number of specified disk in an instance exceeds.|The error message returned because the number of disks in the instance has reached the upper limit.|
|400|InvalidDiskCategory.ValueNotSupported|The specified parameter "DiskCategory" is not valid.|The error message returned because the specified DiskCategory is invalid.|
|400|InvalidSpotStrategy|The specified SpotStrategy is not valid.|The error message returned because the specified SpotStrategy parameter is invalid.|
|400|InvalidSpotPriceLimit|The specified SpotPriceLimitis not valid.|The error message returned because the specified SpotPriceLimit is invalid.|
|400|InvalidSpotDuration|The specified SpotDuration is not valid.|The error message returned because the specified SpotDuration is invalid.|
|400|InvalidSpotAuthorized|The specified Spot param is unauthorized.|The error message returned because you do not have the permission to create the preemptible instance.|
|400|InvalidSpotPrepaid|The specified Spot type is not support PrePay Instance.|The error message returned because the specified preemptible instance does not support the subscription billing method.|
|400|InvalidSpotAliUid|The specified UID is not authorized to use SPOT instance.|The error message returned because the specified UID does not have the permission to use preemptible instances.|
|400|InvalidParameter.Bandwidth|%s|The error message returned because the bandwidth parameter is not supported.|
|400|InvalidDataDiskCategory.ValueNotSupported|%s|The error message returned because the specified data disk category is not supported.|
|400|InvalidSystemDiskCategory.ValueNotSupported|%s|The error message returned because the specified system disk category is not supported.|
|400|InvalidParameter.Conflict|%s|The error message returned because one specified parameter conflicts with another specified parameter.|
|400|InvalidInternetChargeType.ValueNotSupported|%s|The error message returned because the specified InternetChargeType is not supported.|
|400|InvalidInstanceType.ValueNotSupported|%s|The error message returned because the specified instance type is invalid.|
|403|InstanceType.Offline|%s|The error message returned because the specified instance type is unavailable.|
|400|RegionUnauthorized|%s|The error message returned because the specified region is not supported.|
|400|Zone.NotOnSale|%s|The error message returned because the specified zone is disabled.|
|400|InvalidSystemDiskSize.ValueNotSupported|%s|The error message returned because the specified system disk size is invalid.|
|400|InvalidDataDiskSize.ValueNotSupported|%s|The error message returned because the specified data disk size is invalid.|
|404|InvalidKeyPairName.NotFound|The specified parameter "KeyPairName" does not exist in our records.|The error message returned because the specified KeyPairName does not exist.|
|403|DependencyViolation.WindowsInstance|The instance creating is window, cannot use ssh key pair to login.|The error message returned because SSH key pairs are not supported for Windows instances.|
|400|InvalidInstanceType.ValueNotSupported|The specified parameter "KeyPairName" only support IoOptimized Instance.|The error message returned because only I/O-optimized instances support SSH key pairs.|
|404|InvalidResourceGroup.NotFound|The ResourceGroup provided does not exist in our records.|The error message returned because the resource group does not exist.|
|403|InvalidNetworkType.MismatchRamRole|A RAM role t be used for classic instance.|The error message returned because classic network-connected instances do not support RAM roles.|
|403|InvalidUser.PassRoleForbidden|The RAM user does not have the privilege to pass a RAM role.|The error message returned because the RAM user is not authorized to pass the RAM role.|
|404|InvalidRamRole.NotFound|The specified parameter "RAMRoleName" does not exist.|The error message returned because the specified RAMRoleName does not exist.|
|404|InvalidLaunchTemplate.NotFound|%s|The error message returned because the specified template name is not found.|
|404|InvalidLaunchTemplateVersion.NotFound|%s|The error message returned because the specified template version is not found.|
|400|InvalidInstanceType.ElasticNetworkInterfaceNotSupported|The specified instance type does not support Elastic Network Interface, you can not attach Elastic Network Interface to generation I instances.|The error message returned because ENIs are not supported in the specified instance type.|
|400|InvalidParameter.EncryptedIllegal|%s|The error message returned when the parameter does not support encrypted disks.|
|400|InvalidParameter.EncryptedNotSupported|%s|The error message returned because the parameter is not supported for encrypted disks.|
|400|InvalidParameter.Encrypted.KmsNotEnabled|The encrypted disk need enable KMS|The error message returned because KMS has not been activated. KMS must be activated to encrypt disks.|
|500|InternalError|The request processing has failed due to some unknown error, exception or failure.|The error message returned because an unknown error occurs.|
|403|Forbidden.RiskControl|This operation is forbidden by Aliyun RiskControl system.|The error message returned because the operation is prohibited by the risk control system of Alibaba Cloud.|
|403|InvalidInstance.UnPaidOrder|The specified Instance has unpaid order.|The error message returned because you have outstanding bills for the specified instance. Complete the payment and try again.|
|403|RealNameAuthenticationError|Your account has not passed the real-name authentication yet.|The error message returned because you failed to complete real-name authentication.|
|403|InvalidInstanceType.NotSupported|The specified InstanceType is not Supported.|The error message returned because the specified InstanceType is not supported.|
|403|InvalidPayMethod|The specified pay method is not valid.|The error message returned because the specified payment method is invalid.|
|403|InvalidAccountStatus.NotEnoughBalance|Your account does not have enough balance.|The error message returned because your account has insufficient balance to pay for the service. Top up your account and try again.|
|400|InvalidSpotPriceLimit.LowerThanPublicPrice|The specified parameter "spotPriceLimit" can't be lower than the current public price.|The error message returned because the specified spotPriceLimit is lower than the current market price.|
|400|InvalidRelationResource.NotFound|The relation resource has been deleted.|The error message returned because the related resource is deleted.|
|400|IncorrectRecycleBinStatus|The operation is not permitted due to resource status.|The error message returned because the operation is not supported while the resource is in the current state.|
|400|InvalidHpcClusterId.Unnecessary|The specified HpcClusterId is unnecessary|The error message returned because the specified HpcClusterId is not required.|
|400|InvalidVSwitchId.Necessary|The VSwitchId is necessary|The error message returned because VSwitchId is not specified.|
|400|InvalidHpcClusterId.Necessary|The HpcClusterId is necessary|The error message returned because HpcClusterId is not specified.|
|400|InvalidHpcClusterId.NotFound|The specified HpcClusterId is not found|The error message returned because the specified HPC cluster does not exist.|
|400|InvalidHpcClusterId.Creating|The specified HpcClusterId is creating|The error message returned because the specified HPC cluster is being created.|
|404|InvalidVSwitchId.NotExist|%s|The error message returned because the specified VSwitch does not exist.|
|403|ImageNotSupportInstanceType|The specified image does not support the specified InstanceType.|The error message returned because the specified instance type is not supported in the specified image.|
|400|InvalidSecurityGroup.NotInDefaultVpc|%s|The error message returned because the specified security group is not associated with the default VPC.|
|400|VpcNotFound|Vpc is not found according to the specified VSwitch or the vpc does not belong to you.|The error message returned because the specified VPC does not exist.|
|400|InvalidSystemDiskSize.ImageNotSupportResize|The specified image does not support resize.|The error message returned because the specified image does not support resizing.|
|403|OperationDenied.InvalidNetworkType|%s|The error message returned because the specified network type is not supported.|
|400|InvalidSpotInterruptionBehavior|%s|The error message returned because the specified SpotInterruptionBehavior is invalid.|
|403|InvalidSpotInterruptionBehavior.ClassicNetworkNotSupport|The specified SpotInterruptionBehavior does not support Classic network Instance.|The error message returned because the SpotInterruptionBehavior parameter is only applicable to VPC-connected preemptible instances, but not classic network-connected instances.|
|403|InvalidSpotInterruptionBehavior.LocalDiskNotSupport|The specified SpotInterruptionBehavior does not support local disk instance.|The error message returned because preemptible instances do not support local disks.|
|400|InvalidDeploymentOnHost|%s|The error message returned because dedicated hosts are not supported in the specified deployment set.|
|400|InvalidInstanceChargeType.NotSupport|The Dedicated host not support the specified Instance charge type.|The error message returned because the billing method is not supported for dedicated hosts.|
|400|InvalidNetworkType.NotSupported|The classic networkType not support create ECS on dedicatedHost|The error message returned because the classic network is not supported for dedicated hosts.|
|400|InvalidDedicatedHostId.NotFound|The specified DedicatedHostId does not exist.|The error message returned because the specified dedicated host ID does not exist.|
|400|InvalidDedicatedHostStatus.NotSupport|Operation denied due to dedicated host status.|The error message returned because the operation is not supported while the dedicated host is in the current state.|
|400|IncorrectDedicatedHostStatus|The current status of the resource does not support this operation.|The error message returned because the operation is not supported while the dedicated host is in the current state.|
|400|ChargeTypeViolation.PostPaidDedicatedHost|Prepaid instance onto postpaid dedicated host is not allowed|The error message returned because you cannot change the billing method for instances that are on a dedicated host.|
|400|InvalidPeriod.ExceededDedicatedHost|Instance expired date can't exceed dedicated host expired date.|The error message returned because the expiration date of the instance is later than that of the dedicated host.|
|400|InvalidInstanceType.ValueUnauthorized|The specified InstanceType is not authorize.|The error message returned because you are not authorized to use this instance type.|
|400|DedicatedHostType.Unmatched|The specified DedicatedHostType t match the instance type.|The error message returned because dedicated hosts do not support preemptible instances.|
|400|MissingParameter|The input parameter ImageId that is mandatory for processing this request is not supplied.|The error message returned because ImageId is not specified.|
|400|MissingParameter|The input parameter InstanceType that is mandatory for processing this request is not supplied.|The error message returned because InstanceType is not specified.|
|400|ChargeTypeViolation.PostPaidDedicatedHost|Prepaid instance onto postpaid dedicated host is not allowed.|The error message returned because you cannot change the billing method for instances that are on a dedicated host.|
|400|InvalidParam.NetworkInterface|%s|The error message returned because the specified parameter is invalid.|
|403|OperationDenied.ImageNotValid|%s|The error message returned because the specified image does not support this operation.|
|403|QuotaExceed.PostPaidDisk|Living postPaid disks quota exceeded.|The error message returned because the number of pay-as-you-go disks has reached the upper limit.|
|401|InvalidRamRole.NotEcsRole|The specified ram role is not authorized for ecs, please check your role policy.|The error message returned because the specified RAM role is not authorized to access ECS.|
|403|InvalidParameter.NotMatch|%s|The error message returned because one specified parameter conflicts with another specified parameter.|
|403|InvalidVSwitch.DefaultVSwitchNotSupport|The specified zone in vpc can't support create default vSwitch.|The error message returned because the default VSwitch is not supported for VPCs of the specified zone.|
|400|InvalidParameter.CreditSpecification|The specified CreditSpecification is not supported in this region.|The error message returned because the specified CreditSpecification is not supported in this region.|
|404|InvalidMarketImage.NotFound|The specified marketplace image does not exist, please change the imageId and try again.|The error message returned because the specified image is not available in the image marketplace.|
|400|IncorrectVpcStatus|Current VPC status does not support this operation.|The error message returned because the operation is not supported while the VPC is in the current state.|
|400|InvalidInstanceType.NotSupported|The specified instanceType is not supported by the deployment set.|The error message returned because the specified instance type is not supported in the specified deployment set.|
|400|InvalidVpcZone.NotSupported|The specified operation is not allowed in the zone to which your VPC belongs, please try in other zones.|The error message returned because the operation is not supported in the specified zone.|
|400|IncorrectDefaultVpcStatus|The status of the default VPC is invalid.|The error message returned because the status of the default VPC is invalid.|
|404|DeploymentSet.NotFound|The specified deployment set does not exist.|The error message returned because the specified deployment set does not exist.|
|400|InvalidAutoRenewPeriod.ValueNotSupported|The specified autoRenewPeriod is invalid.|The error message returned because the specified AutoRenewPeriod is invalid.|
|403|OperationDenied.LocalDiskUnsupported|The configuration change is not allowed when the specified instance has local disks mounted.|The error message returned because configuration changes are not supported for instances with local disks attached.|
|403|OperationDenied.InconsistentNetwork|The specified security group and vswitch are not in the same vpc.|The error message returned because the security group and the VSwitch must share the same VPC.|
|403|OperationDenied|If the network segment of the vswitch is the same as that of its VPC. Therefore, the VPC cannot create other vswitchs across the region.|The error message returned because the VPC and VSwitch have the same CIDR block and no additional VSwitches can be created for other zones of this VPC.|
|403|DefaultVswitch.Existed|The default vswitch for VPC already exists.|The error message returned because the default VSwitch has been created for the VPC.|
|400|InvalidMarketImageChargeType.NotSupport|The specified chargeType of marketImage is unsupported.|The error message returned because the billing method for marketplace images is invalid.|
|403|OperationDenied.NoStock|The requested resource is sold out in the specified zone; try other types of resources or other regions and zones.|The error message returned because of insufficient inventory for the requested resource. Try again with other resource types or other regions and zones.|
|403|IncorrectInstanceStatus|The current status of the resource does not support this operation.|The error message returned because the operation is not supported while the resource is in the current state.|
|403|CategoryViolation|The specified instance does not support this operation because of its disk category.|The error message returned because the configurations of instances with local disks attached cannot be upgraded or downgraded.|
|400|InvalidPeriodType.ValueNotSupported|The specified parameter PeriodType is invalid.|The error message returned because the specified PeriodType is invalid.|
|403|ResourcesNotInSameZone|The specified instance and dedicated host are not in the same zone.|The error message returned because the instance and the dedicated host must be in the same region.|
|403|InvalidDisk.SystemDiskSize|The specified SystemDiskSize beyond the permitted range.|The error message returned because the maximum size of the specified system disk is reached.|
|400|InvalidClientToken.ValueNotSupported|The ClientToken provided is invalid.|The error message returned because the specified ClientToken is invalid.|
|400|OperationDenied|The current user does not support this operation.|The error message returned because the current user is not authorized to perform this operation.|
|400|IncorrectImageStatus|The specified marketplace image is not available.|The error message returned because the specified marketplace image is not available.|
|403|InsufficientBalance|Your account does not have enough balance.|The error message returned because your account has insufficient balance. Top up your account and try again.|
|400|InvalidInstanceType.ValueNotSupported|The specified InstanceType does not exist or beyond the permitted range.|The error message returned because the specified instance type is not supported.|
|400|InvalidParam.Tenancy|The specified Tenancy is invalid.|The error message returned because the specified Tenancy parameter is invalid.|
|403|MaxEniIpv6IpsCountExceeded|%s|The error message returned because the number of IPv6 addresses that the ENI can support has reached the upper limit.|
|403|InvalidIp.IpRepeated|%s|The error message returned because the specified IP addresses are not unique.|
|403|InvalidIp.IpAssigned|%s|The error message returned because the specified IP address has been assigned.|
|403|InvalidIp.Address|%s|The error message returned because the specified IPv6 address is invalid.|
|403|InvalidOperation.Ipv4CountExceeded|%s|The error message returned because the maximum number of IPv4 addresses is reached.|
|403|InvalidOperation.Ipv6CountExceeded|%s|The error message returned because the maximum number of IPv6 addresses is reached.|
|403|InvalidOperation.Ipv6NotSupport|%s|The error message returned because the specified instance type does not support IPv6 addresses.|
|403|InvalidVSwitch.Ipv6NotTurnOn|%s|The error message returned because IPv6 not enabled for the specified VSwitch.|
|403|InvalidParam.Amount|%s|The error message returned because the specified Amount is invalid.|
|403|InvalidVSwitchId.IpInvalid|%s|The error message returned because the specified private IP address is invalid.|
|403|Forbidden.RegionId|%s|The error message returned because the feature is not supported in the specified region.|
|400|IncorrectVpcStatus|The current status of vpc does not support this operation.|The error message returned because the operation is not supported while the VPC is in the current state.|
|403|QuotaExceed.DeploymentSetInstanceQuotaFull|instance quota in one deployment set exceeded.|The error message returned because the number of instances in the current deployment set has reached the upper limit.|
|403|InvalidRegion.NotSupport|The specified region does not support byok.|The error message returned because BYOK encryption is not supported in this region.|
|403|UserNotInTheWhiteList|The user is not in byok white list.|The error message returned because you are not authorized to use BYOK encryption.|
|400|InvalidParameter.EncryptedIllegal|The specified parameter Encrypted must be true when kmsKeyId is not empty.|The error message returned because the DataDisk.N.Encrypted parameter is not specified after you set the KmsKeyId parameter.|
|400|IoOptimized.NotSupported|The specified instance must be IoOptimized instance when kmsKeyId is not empty.|The error message returned because the specified instance type must be I/O-optimized are not used after you specified KmsKeyId.|
|404|InvalidParameter.KMSKeyId.NotFound|The specified KMSKeyId does not exist.|The error message returned because the specified KMSKeyId does not exist.|
|403|InvalidParameter.KMSKeyId.KMSUnauthorized|ECS service have no right to access your KMS.|The error message returned because ECS is not authorized to access your KMS resources.|
|403|SecurityRisk.3DVerification|We have detected a security risk with your default credit or debit card. Please proceed with verification via the link in your email.|The error message returned because your payment method has security risks. You can troubleshoot the issue by following the provided instructions.|
|400|Duplicate.TagKey|The Tag.N.Key contain duplicate key.|The error message returned because the specified tag key is not unique.|
|404|InvalidSecurityGroupId.NotFound|%s|The error message returned because the specified security group ID does not exist.|
|404|InvalidDiskIds.NotPortable|The specified DiskId is not portable.|The error message returned because the specified disk is not portable.|

