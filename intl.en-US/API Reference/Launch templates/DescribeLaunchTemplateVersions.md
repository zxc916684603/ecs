# DescribeLaunchTemplateVersions {#DescribeLaunchTemplateVersions .reference}

Queries instance launch template versions.

## Request Parameters {#RequestParameter .section}

|Parameter|Type|Required|Description|
|:--------|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DescribeLaunchTemplateVersions.|
|RegionId|String|Yes.|Region ID of an instance launch template. You can all [DescribeRegions](reseller.en-US/API Reference/Regions/DescribeRegions.md#) to view the latest list of Alibaba Cloud regions,|
|LaunchTemplateId|String|No|Instance launch template ID. Either the `LaunchTemplateId` or `LaunchTemplateName` must be specified to determine the template.|
|LaunchTemplateName|String|No|Instance launch template name.|
|LaunchTemplateVersion.N|Long|No|One or more instance launch template versions.|
|MinVersion|Long|No|The minimum version number when a range is used to specify the template.|
|MaxVersion|Long|No|The maximum version number when a range is used to specify the template.|
|DefaultVersion|Boolean|No|Whether to query the default version.|
|PageNumber|Integer|No|Page number of the instance launch template list. Start value: 1.Default value: 1.

|
|PageSize|Integer|No|Number of rows per page when querying by page. Maximum Value: 50.Default value: 10.

|

## Response parameters {#ResponseParameter .section}

|Parameter |Type|Description|
|:---------|:---|:----------|
|TotalCount|Integer|Total number of instance launch templates.|
|Pagenumber|Integer|Current page number.|
|Pagesize|Integer|Number of rows per page when querying by page.|
|LaunchTemplateVersionSet|[LaunchTemplateVersionSet](#)|Information about the template version.|

**LaunchTemplateVersionSet** 

|Parameter |Type|Description|
|:---------|:---|:----------|
|CreateTime|String|Template creation time.|
|ModifiedTime|String|Time of last template modification.|
|LaunchTemplateId|String|Template ID.|
|LaunchTemplateName|String|Template name.|
|DefaultVersion|Boolean|Default template version.|
|VersionNumber|Long|Template version number.|
|VersionDescription|Long|Template version description.|
|CreatedBy|String|Creator of the template.|
|LaunchTemplateData|[LaunchTemplateData](#)|The specific template configuration.|

**Data type: LaunchTemplateData** 

|Parameter |Type|Description|
|:---------|:---|:----------|
|ImageId|String|Image ID.|
|InstanceType|String|Instance type.|
|SecurityGroupId|String|Security group ID.|
|VSwitchId|String|VSwitch ID.|
|InstanceName|String|Instance name.|
|Description|String|Instance description.|
|InternetMaxBandwidthIn|String|Maximum inbound public bandwidth.|
|InternetMaxBandwidthOut|String|Maximum outbound public bandwidth.|
|HostName|String|Instance host name.|
|ZoneId|String|Instance zone ID.|
|Systemdisk.Category|String|System disk type.|
|SystemDisk.Size|Integer|System disk size, in GiB.|
|SystemDisk.DiskName|String|System disk name.|
|SystemDisk.Description|String|System disk description.|
|DataDisk.n.Size|Integer|Data disk size.|
|DataDisk.n.SnapshotId|String|Snapshot ID used for the data disk.|
|DataDisk.n.Category|String|Data disk type.|
|DataDisk.n.Encrypted|Boolean|Whether the data disk is encrypted.|
|DataDisk.n.DiskName|String|System disk name|
|DataDisk.n.Description|String|System disk description.|
|DataDisk.n.DeleteWithInstance|String|Whether the data disk is released with its instance.|
|IoOptimized|String|Whether this is an I/O optimized instance.|
|NetworkInterface.n.PrimaryIpAddress|String|Primary private IP address of the ENI.|
|NetworkInterface.n.VSwitchId|String|The ID of the ENI's VSwitch.|
|NetworkInterface.n.SecurityGroupId|String|The security group ID, which must be in the same VPC as the ENI.|
|NetworkInterface.n.NetworkInterfaceName|String|ENI name.|
|NetworkInterface.n.Description|String|ENI description.|
|Period|Integer|Duration of purchased resource.|
|InternetChargeType|String|Public bandwidth billing method.|
|NetworkType|String|Network type.|
|UserData|String|User data of the instance, which is Base64-encoded.|
|KeyPairName|String|Key pair name.|
|RamRoleName|String|Instance's RAM role name.|
|AutoReleaseTime|String|Automatic release time.|
|SpotStrategy|String|Spot strategy for Pay-As-You-Go instances.|
|SpotPriceLimit|Float|Sets the maximum hourly price for instances.|
|SecurityEnhancementStrategy|String|Whether Security Reinforcement is enabled.|
|Tag.n.Key|String|Instance tag key.|
|Tag.n.Value|Float|Instance tag value.|

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DescribeLaunchTemplateVersions
&Regionid = cn-Hangzhou
&LaunchTemplateName=lt-name1
&<Common request parameters>
```

**Response example** 

**XML format**

```
<DescribeLaunchTemplateVersionsResponse>
	<RequestId>04F0F334-1335-436C-A1D7-6C044FExxxxx</RequestId>
	<TotalCount>1</TotalCount>
	<PageNumber>1</PageNumber>
	<PageSize>10</PageSize>
	<LaunchTemplateVersionSets>
		<LaunchTemplateVersionSet>
			<CreateTime>2018-05-14T14:18:00Z</CreateTime>
			<ModifiedTime>2018-05-14T14:18:00Z</ModifiedTime>
			<LaunchTemplateId>lt-m5e3ofjr1zn1aw7xxxx</LaunchTemplateId>
			<LaunchTemplateName>wd-1526307480xxx</LaunchTemplateName>
			<DefaultVersion>true</DefaultVersion>
			<VersionNumber>1</VersionNumber>
			<CreatedBy>1942111349714xxx</CreatedBy>
			<VersionDescription>wwww</VersionDescription>
			<launchtemplatedata>
					 <imageowneralias>ImageOwnerAlias1</imageowneralias>
					 <description>Description1</description>
					 <resourcegroupid>ResourceGroupId1</resourcegroupid>
					 <datadisks>
						 <datadisk>
							 <snapshotid>SnapshotId1</snapshotid>
							 <description>Description1</description>
							 <category>cloud_efficiency</category>
							 <encrypted>false</encrypted>
							 <size>44</size>
							 <deletewithinstance>true</deletewithinstance>
							 <diskname>DataDiskName1</diskname>
						 </datadisk>
					 </datadisks>
					 <userdata>UserData1</userdata>
					 <systemdisk.diskname>SystemDiskDiskName1</systemdisk.diskname>
					 <systemdisk.size>44</systemdisk.size>
					 <ramrolename>RamRoleName1</ramrolename>
					 <networktype>NetworkType1</networktype>
					 <networkinterfaces>
						 <networkinterface>
							 <description>Description1</description>
							 <securitygroupid>SecurityGroupId1</securitygroupid>
							 <vswitchid>VSwitchId1</vswitchid>
							 <networkinterfacename>NetworkInterfaceName1</networkinterfacename>
							 <primaryipaddress>PrimaryIpAddress1</primaryipaddress>
						 </networkinterface>
					 </networkinterfaces>
					 <imageid>windows2008.vhd</imageid>
					 <spotpricelimit>1</spotpricelimit>
					 <systemdisk.category>cloud_efficiency</systemdisk.category>
					 <instancetype>ecs.xn4.small</instancetype>
					 <spotstrategy>SpotWithPriceLimit</spotstrategy>
					 <hostname>HostName1</hostname>
					 <tags>
						 <instancetag>
							 <value>bb</value>
							 <key>ss</key>
						 </instancetag>
					 </tags>
					 <keypairname>KeyPairName1</keypairname>
					 <systemdisk.iops>22</systemdisk.iops>
					 <iooptimized>true</iooptimized>
					 <zoneid>ZoneId1</zoneid>
					 <systemdisk.description>SystemDiskDescription1</systemdisk.description>
					 <securitygroupid>sg-tiantt1234</securitygroupid>
					 <vswitchid>vsw-xxxxxx</vswitchid>
					 <period>1</period>
					 <internetchargetype>PayByBandwidth</internetchargetype>
					 <instancename>InstanceName1</instancename>
					 <internetmaxbandwidthout>20</internetmaxbandwidthout>
					 <internetmaxbandwidthin>1</internetmaxbandwidthin>
					 <securityenhancementstrategy>Active</securityenhancementstrategy>
					 <autoreleasetime>2019-10-21T00:00:00Z</autoreleasetime>
				 </launchtemplatedata>
		</LaunchTemplateVersionSet>
	</LaunchTemplateVersionSets>
</DescribeLaunchTemplateVersionsResponse>
```

 **JSON format ** 

```
{
	"RequestId": "04F0F334-1335-436C-A1D7-6C044FExxxxx",
	"TotalCount":1,
	"PageNumber":1,
	"PageSize":10,
	"LaunchTemplateVersionSets":{
		"LaunchTemplateVersionSet":[{
			{
					"LaunchTemplateData":{
						"Description":"Description1",
						"ResourceGroupId":"ResourceGroupId1",
						"DataDisks":{
							"DataDisk":[
								{
									"SnapshotId":"SnapshotId1",
									"Description":"Description1",
									"Category":"cloud_efficiency",
									"Encrypted":false,
									"Size":44,
									"DeleteWithInstance":true,
									"DiskName":"DataDiskName1"
								}
							]
						},
						"UserData":"UserData1",
						"SystemDisk.DiskName":"SystemDiskDiskName1",
						"SystemDisk.Size":44,
						"RamRoleName":"RamRoleName1",
						"NetworkType":"NetworkType1",
						"NetworkInterfaces":{
							"NetworkInterface":[
								{
									"Description":"Description1",
									"SecurityGroupId":"SecurityGroupId1",
									"VSwitchId":"VSwitchId1",
									"NetworkInterfaceName":"NetworkInterfaceName1",
									"PrimaryIpAddress":"PrimaryIpAddress1"
								}
							]
						},
						"ImageId":"windows2008.vhd",
						"SpotPriceLimit":1,
						"SystemDisk.Category":"cloud_efficiency",
						"InstanceType":"ecs.xn4.small",
						"SpotStrategy":"SpotWithPriceLimit",
						"HostName":"HostName1",
						"Tags":{
							"InstanceTag":[
								{
									"Value":"bb",
									"Key":"ss"
								}
							]
						},
						"KeyPairName":"KeyPairName1",
						"SystemDisk.Iops":22,
						"IoOptimized":"true",
						"ZoneId":"ZoneId1",
						"SystemDisk.Description":"SystemDiskDescription1",
						"SecurityGroupId":"sg-tiantt1234",
						"VSwitchId":"vsw-xxxxxx",
						"Period":1,
						"InternetChargeType":"PayByBandwidth",
						"InstanceName":"InstanceName1",
						"InternetMaxBandwidthOut":20,
						"InternetMaxBandwidthIn":1,
						"SecurityEnhancementStrategy":"Active",
						"AutoReleaseTime":"2019-10-21T00:00:00Z"
					},
					"LaunchTemplateName":"wd-1526308145065",
					"CreatedBy":"1942111349714263",
					"VersionDescription":"wwwdesc",
					"ModifiedTime":"2018-05-14T14:29:05Z",
					"CreateTime":"2018-05-14T14:29:05Z",
					"DefaultVersion":true,
					"LaunchTemplateId":"lt-m5efs0xpur7pey3y9yt7",
					"VersionNumber":1
				}
		}]
	}
}
```

## Error codes {#ErrorCode .section}

|Error code |Error message |HTTP status code|Meaning|
|:----------|:-------------|:---------------|:------|
|InvalidLaunchTemplate.NotFound|The specified LaunchTemplateId “\{0\}” LaunchTemplateName “\{1\}” is not found.|400|The specified `LaunchTemplateId` or `LaunchTemplateName` is not found.|
|MissingParameter|The input parameter “\{0\}” that is mandatory for processing this Request is not supplied.|400|A required parameter is missing.|
|InvalidParameter|the parameter\(s\) “\{0\}” provided is\(are\) invalid.|400|The specified parameter is invalid.|
|Innerservicefailed|Call inner service failed|403|Internal server error.|

