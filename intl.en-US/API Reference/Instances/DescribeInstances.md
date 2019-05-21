# DescribeInstances {#doc_api_1161578 .reference}

Views the details of one or more instances.

## Description {#description .section}

The AND operator is used to define the relationship between multiple request parameters. If the value of a parameter is null, the request fails. However, if InstanceIds is set to a blank JSON array, it is considered valid and null is returned.

## Debugging {#apiExplorer .section}

You can use [API Explorer](https://api.aliyun.com/#product=Ecs&api=DescribeInstances) to perform debugging. API Explorer allows you to perform various operations to simplify API usage. For example, you can retrieve APIs, call APIs, and dynamically generate SDK example code.

## Request parameters {#parameters .section}

|Name|Type|Required|Example|Description|
|----|----|--------|-------|-----------|
|RegionId|String|Yes|cn-hangzhou| The region ID of the instance. You can call the [DescribeRegions](~~25609~~) operation to view the latest region list.

 |
|Action|String|No|DescribeInstances| The operation that you want to perform. Set the value to DescribeInstances.

 |
|InstanceIds|String|No|\["i-xxxxxxxxx", "i-yyyyyyyyy", … "i-zzzzzzzzz"\]| The ID of the instance. It can be a JSON array that consists of multiple instance IDs. Separate multiple instance IDs with commas \(,\). A maximum of 100 instance IDs can be entered at a time.

 |
|VpcId|String|No|v-vpcid1| The ID of the VPC.

 |
|VSwitchId|String|No|vsw-vswitchid1| The ID of the VSwitch.

 |
|InstanceNetworkType|String|No|VPC| The network type of the instance. Valid values:

 -   classic.
-   VPC.

 |
|SecurityGroupId|String|No|sg-securitygroupid1| The ID of the security group to which the instance belongs.

 |
|ZoneId|String|No|cn-hangzhou-b| The zone ID of the instance.

 |
|PageNumber|Integer|No|1| The page number. This value starts from 1. Default value: 1.

 |
|PageSize|Integer|No|10| The number of rows per page. Maximum value: 100. Default value: 10.

 |
|InnerIpAddresses|String|No|\["10.1.1.1", "10.1.2.1", … "10.1.10.1"\]| The private IP address list of the classic instance. It is valid when InstanceNetworkType is set to classic. The value can be a JSON array that consists of multiple IP addresses. Separate multiple IP addresses with commas \(,\). A maximum of 100 IP addresses can be entered at a time.

 |
|PrivateIpAddresses|String|No|\["172.16.1.1", "172.16.2.1", … "172.16.10.1"\]| The private IP address list of the VPC-type instance. It is valid when InstanceNetworkType is set to VPC. The value can be a JSON array that consists of multiple IP addresses. Separate multiple IP addresses with commas \(,\). A maximum of 100 IP addresses can be entered at a time.

 |
|PublicIpAddresses|String|No|\["42.1.1.1", "42.1.2.1", … "42.1.10.1"\]| The public IP address list of the instance. It is valid when InstanceNetworkType is set to classic. The value can be a JSON array that consists of multiple IP addresses. Separate multiple IP addresses with commas \(,\). A maximum of 100 IP addresses can be entered at a time.

 |
|EipAddresses|String|No|\["42.1.1.1", "42.1.2.1", … "42.1.10.1"\]| The EIP address list of the instance. It is valid when InstanceNetworkType is set to VPC. The value can be a JSON array that consists of multiple IP addresses. Separate multiple IP addresses with commas \(,\). A maximum of 100 IP addresses can be entered at a time.

 |
|InstanceChargeType|String|No|PostPaid| The billing method of the instance. Valid values:

 -   PostPaid: Pay-As-You-Go.
-   PrePaid: subscription.

 |
|InternetChargeType|String|No|PayByTraffic| The billing method of the instance. Default value: PayByTraffic. Valid values:

 -   PayByTraffic: charged based on actual traffic.

 |
|InstanceName|String|No|\*Joshua| The name of the instance. Fuzzy search with the wildcard \* is supported.

 |
|ImageId|String|No|m-imageid1| The ID of the image.

 |
|Status|String|No|Running| The status of the instance. Valid values:

 -   Running.
-   Starting.
-   Stopping.
-   Stopped.

 |
|LockReason|String|No|security| The reason why the resource is locked.

 |
|IoOptimized|Boolean|No|true| Indicates whether it is an optimized instance.

 |
|NeedSaleCycle|Boolean|No|false| Indicates whether to return the sales cycle of the subscription instance. Default value: false.

 |
|Tag.N.Key|String|No|FinanceDept| The tag key of the instance. n ranges from 1 to 20. If you specify this parameter, it cannot be left empty. It must be no more than 64 characters in length. It cannot start with aliyun, acs:, http://, or https://.

 |
|Tag.N.Value|String|No|FinanceDeptJoshua| The tag value of the instance. n ranges from 1 to 20. If you specify this parameter, it can be left empty. It must be no more than 128 characters in length. It cannot start with aliyun, acs:, http://, or https://.

 |
|InstanceType|String|No|ecs.g5.larger| The type of the instance.

 |
|InstanceTypeFamily|String|No|ecs.g5| The type family of the instance.

 |
|KeyPairName|String|No|FinanceJoshua| The name of the SSH key pair for the instance.

 |
|ResourceGroupId|String|No|rg-resourcegroupid1| The ID of the resource group to which the instance belongs.

 |
|HpcClusterId|String|No|hpc-hpclusterid1| The ID of the HPC cluster to which the instance belongs.

 |
|RdmaIpAddresses|String|No|10.10.10.102| The RDMA IP address of the HPC instance.

 |
|DryRun|Boolean|No|false| Indicates whether to send a check request only. Default value: false.

 -   true: Only a check request is sent and no query is performed. The system checks whether your AccessKey is valid, whether RAM users are authorized, and whether the required parameters are set. If the check fails, the corresponding error code is returned. If the check succeeds, the DryRunOperation error code is returned.
-   false: A request is sent and then the query is performed if the 2XX HTTP status code is returned.

 |

## Response parameters {#resultMapping .section}

|Name|Type|Example|Description|
|----|----|-------|-----------|
|Instances| | | The returned instance information. It is an array that consists of InstanceAttributesType data.

 |
|└AutoReleaseTime|String|2017-12-10T04:04Z| The automatic release time of the Pay-As-You-Go instance.

 |
|└ClusterId|String|c-clusterid1| The ID of the cluster to which the instance belongs.

 **Note:** This parameter will be removed in the future. We recommend that you use other parameters to ensure compatibility.

 |
|└Cpu|Integer|8| The number of vCPUs.

 |
|└CreationTime|String|2017-12-10T04:04Z| The time when the instance is created.

 |
|└CreditSpecification|String|Standard| The running mode of the burstable performance instance \(t5\). Valid values:

 -   Standard: the standard mode. For more information, see [Standard t5 instances](~~90635~~).
-   Unlimited: the unlimited performance mode. For more information, see [Unlimited-performance t5 instances](~~90581~~).

 |
|└DedicatedHostAttribute| | | The host array that consists of DedicatedHostId and DedicatedHostName.

 |
|└DedicatedHostId|String|dh-dedicatedhostid1| The ID of the DDH.

 |
|└DedicatedHostName|String|FinanceDept| The name of the DDH.

 |
|└DeletionProtection|Boolean|false| The release protection attribute of the instance. It indicates whether you can use the ECS console or call the DeleteInstance operation to release the instance.

 -   true: enables release protection.
-   false: disables release protection.

 **Note:** This attribute is applicable to subscription, Pay-As-You-Go, and preemptible instances. It can only be used to block manual release operations, but not automatic release operations by the system.

 |
|└DeploymentSetId|String|ds-deploymentid1| The ID of the deployment set.

 |
|└Description|String|FinanceJoshua| The description of the instance.

 |
|└EcsCapacityReservationAttr| | | The capacity reservation attributes of the instance.

 |
|└ EipAddress| | | The EIP address binding information.

 |
|└AllocationId|String|i-instanceid1| The ID of the instance bound to an EIP address.

 |
|└Bandwidth|Integer|5| The peak speed of the EIP address. Unit: Mbit/s.

 Default: 5.

 |
|└InternetChargeType|String|PayByTraffic| The billing method of the EIP address.

 |
|└IpAddress|String|xxx.xx.xxx.xx| The EIP address.

 |
|└IsSupportUnassociate|Boolean|true| Indicates whether the EIP address can be unbound.

 |
|└ExpiredTime|String|2017-12-10T04:04Z| The expiration time of the instance. The time follows the [ISO 8601](~~25696~~) standard and is in UTC time. Format: yyyy-MM-ddTHH:mm:ssZ.

 |
|└GPUAmount|Integer|4| The number of GPUs for the instance type.

 |
|└GPUSpec|String|NVIDIA V100| The category of GPUs for the instance type.

 |
|└HostName|String|JoshuaHost| The host name of the instance.

 |
|└HpcClusterId|String|hpc-hpcclusterid1| The ID of the HPC cluster to which the instance belongs.

 |
|└ImageId|String|m-imageid1| The ID of the image in which the instance is running.

 |
|└InnerIpAddress| |10.170. XX.XXX| The private IP address of the instance.

 |
|└InstanceChargeType|String|PostPaid| The billing method of the instance. Valid values:

 -   PrePaid: subscription.
-   PostPaid: Pay-As-You-Go.

 |
|└InstanceId|String|i-instanceid1| The ID of the instance.

 |
|└InstanceName|String|FinanceJoshua| The name of the instance.

 |
|└InstanceNetworkType|String|VPC| The network type of the instance. Valid values:

 -   classic.
-   VPC.

 |
|└InstanceType|String|ecs.g5.large| The type of the instance.

 |
|└InstanceTypeFamily|String|ecs.g5| The type family of the instance.

 |
|└InternetChargeType|String|PayByTraffic| The billing method of the instance. Valid values:

 -   PayByTraffic: charged based on actual traffic.

 |
|└InternetMaxBandwidthIn|Integer|100| The maximum inbound bandwidth of the public network. Unit of measurement: Mbps.

 |
|└InternetMaxBandwidthOut|Integer|5| The maximum outbound bandwidth of the public network. Unit of measurement: Mbps.

 |
|└IoOptimized|Boolean|true| Indicates whether it is an optimized instance.

 |
|└KeyPairName|String|FinanceJoshua| The name of the key pair.

 |
|└LocalStorageAmount|Integer|2| The number of local disks that the instance is attached to.

 |
|└LocalStorageCapacity|Long|1000| The capacity of a local disk that the instance is attached to.

 |
|└Memory|Integer|1024| The memory size of the instance. Unit: MiB.

 |
|└NetworkInterfaces| | | The ENI list of the instance.

 |
|└MacAddress|String|00:16:3e:32:b4:dc| The MAC address of the ENI.

 |
|└NetworkInterfaceId|String|eni-2zeh9atclduxvf1zcyal| The ID of the ENI.

 |
|└PrimaryIpAddress|String|172.17. XX.XXX| The private IP address of the primary ENI.

 |
|└OSName|String|Ubuntu 16.04 64| The name of the operating system for the instance.

 |
|└OSNameEn|String|Ubuntu 16.04 64| The English name of the operating system for the instance.

 |
|└OSType|String|Linux| The type of the operating system for the instance. Valid values: Windows and Linux.

 |
|└OperationLocks| | | The reason why the instance is locked.

 |
|└LockMsg|String|The specified instance is locked due to financial reason.| The message returned when the instanced is locked.

 |
|└LockReason|String|Recycling| The type of the reason why the instance is locked. Valid values:

 -   financial: overdue payment.
-   security: security considerations.
-   Recycling: The preemptible instance is locked due to release protection.
-   dedicatedhostfinancial: The ECS instance is locked due to overdue payment of the DDH.

 |
|└PublicIpAddress| |172.17. XX.XXX| The public IP address of the instance.

 |
|└RdmaIpAddress| |10.10.10.102| The RDMA IP address of the HPC instance.

 |
|└Recyclable|Boolean|false| Indicates whether the instance can be recycled.

 |
|└RegionId|String|cn-hangzhou| The region ID of the instance.

 |
|└ResourceGroupId|String|rg-resourcegroupid1| The ID of the resource group to which the instance belongs.

 |
|└SaleCycle|String|month| The unit of a purchase cycle for the subscription instance. Valid values:

 -   week
-   month
-   year

 |
|└SecurityGroupIds| |sg-securitygroupid1| The ID of the security group to which the instance belongs.

 |
|└SerialNumber|String|51d1353b-22bf-4567-a176-8b3e12e43135| The serial number of the instance.

 |
|└SpotPriceLimit|Float|0.98| The maximum hourly price for the instance. It is precise up to three decimal places. It is valid only when SpotStrategy is set to SpotWithPriceLimit.

 |
|└SpotStrategy|String|NoSpot| The preemption policy of the Pay-As-You-Go instance. Valid values:

 -   NoSpot: a standard Pay-As-You-Go instance.
-   SpotWithPriceLimit: a preemptible instance with the upper price limit defined.
-   SpotAsPriceGo: a Pay-As-You-Go instance with its price based on the current market price.

 Default value: NoSpot.

 |
|└StartTime|String|2017-12-10T04:04Z| The start time of the preemption mode for the instance.

 |
|└Status|String|Running| The status of the instance.

 |
|└StoppedMode|String|KeepCharging| Indicates whether the ECS instance is still charged after it is stopped. Valid values:

 -   KeepCharging: The instance is charged after it is stopped, and resources in stock are reserved for it.
-   StopCharging: The instance is not charged after it is stopped. After the ECS instance is stopped, its resources such as its vCPU, memory, and public IP address are released. You may be unable to restart the instance if some of its resources are out of stock in the current region.
-   Not-applicable: Only KeepCharging is supported.

 |
|└Tags| | | The tag list of the instance.

 |
|└TagKey|String|FinanceDept| The tag key of the instance.

 |
|└TagValue|String|FinanceDept.Joshua| The tag value of the instance.

 |
|└VlanId|String|10| The VLAN ID of the instance.

 **Note:** This parameter will be removed in the future. We recommend that you use other parameters to ensure compatibility.

 |
|└VpcAttributes| | | The VPC attributes of the instance.

 |
|└NatIpAddress|String|172.17. XX.XXX| The public IP address of the instance. It is used for ECS instances in different VPCs to communicate with each other.

 |
|└PrivateIpAddress| |172.17. XX.XXX| The private IP address of the instance.

 |
|└VSwitchId|String|vsw-2zeh0r1pabwt\*\*\*\*ssgca| The ID of the VSwitch.

 |
|└VpcId|String|vpc-2zeuphj08tt7q3brdb36x| The ID of the VPC.

 |
|└ZoneId|String|cn-hangzhou-b| The zone ID of the instance.

 |
|PageNumber|Integer|1| The page number.

 |
|PageSize|Integer|10| The number of rows per page.

 |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E| The request ID.

 |
|TotalCount|Integer|6| The total number of instances.

 |

## Examples {#demo .section}

Sample requests

``` {#request_demo}
https://ecs.aliyuncs.com/?Action=DescribeInstances
&RegionId=cn-hangzhou
&<Common request parameters>
```

Successful response examples

`XML` format

``` {#xml_return_success_demo}
<DescribeInstancesResponse>
  <PageNumber>1</PageNumber> 
  <TotalCount>6</TotalCount> 
  <PageSize>10</PageSize>
  <RequestId>8EF01A45-FFFA-497B-B5C3-1DE1B74DB32D</RequestId> 
  <Instances>
    <Instance>
      <InnerIpAddress/> 
      <ImageId>ubuntu_16_0402_64_20G_alibase_20170818.vhd</ImageId> 
      <InstanceTypeFamily>ecs.g5</InstanceTypeFamily> 
      <VlanId/> 
      <NetworkInterfaces> 
        <NetworkInterface> 
          <MacAddress>00:16:3e:32:b4:dc</MacAddress> 
          <PrimaryIpAddress>172.17. XX.XXX</PrimaryIpAddress> 
          <NetworkInterfaceId>eni-2zeh9atclduxvf1zcyal</NetworkInterfaceId> 
        </NetworkInterface> 
      </NetworkInterfaces> 
      <InstanceId>XXXXXXXXXXX</InstanceId> 
      <EipAddress> 
        <IpAddress/> 
        <AllocationId/> 
        <InternetChargeType/> 
      </EipAddress> 
      <InternetMaxBandwidthIn>1000</InternetMaxBandwidthIn> 
      <ZoneId>cn-beijing-e</ZoneId> 
      <InternetChargeType>PayByBandwidth</InternetChargeType>
      <SpotStrategy>NoSpot</SpotStrategy> 
      <StoppedMode>Not-applicable</StoppedMode> 
      <SerialNumber>d9bd1cdc-624d-4736-9da5-2ba2f741a304</SerialNumber> 
      <IoOptimized>true</IoOptimized> 
      <Memory>8192</Memory> 
      <Cpu>2</Cpu> 
      <VpcAttributes> 
        <NatIpAddress/>
        <PrivateIpAddress> 
          <IpAddress>172.17. XX.XXX</IpAddress> 
        </PrivateIpAddress> 
        <VSwitchId>vsw-2zeh0r1pabwt****ssgca</VSwitchId> 
        <VpcId>vpc-2zeuphj08tt7q3brdb36x</VpcId>
      </VpcAttributes> 
      <InternetMaxBandwidthOut>1</InternetMaxBandwidthOut> 
      <SecurityGroupIds> 
        <SecurityGroupId>sg-2ze21r9qb638hvtrvsus</SecurityGroupId> 
      </SecurityGroupIds> 
      <SpotPriceLimit>0.0</SpotPriceLimit> 
      <SaleCycle>Week</SaleCycle> 
      <AutoReleaseTime/> 
      <InstanceName>ECS-BUY-2017-57-10</InstanceName> 
      <Description/>
      <ResourceGroupId/>
      <OSType>linux</OSType> 
      <OSName>Ubuntu 16.04 64</OSName> 
      <InstanceNetworkType>vpc</InstanceNetworkType> 
      <PublicIpAddress> 
        <IpAddress>47.94. XX.XX</IpAddress>
      </PublicIpAddress> 
      <HostName>iZ2zeh9atclduxvf1zxuylZ</HostName> 
      <InstanceType>ecs.g5.large</InstanceType> 
      <CreationTime>2017-12-10T04:04Z</CreationTime> 
      <Tags> 
        <Tag>
          <TagValue>fqwfew</TagValue> 
          <TagKey>fefqe</TagKey> 
        </Tag>
        <Tag>
          <TagValue>weqfwq</TagValue> 
          <TagKey>fqewfwqewf</TagKey> 
        </Tag>
        <Tag>
          <TagValue>ewqffeqw</TagValue> 
          <TagKey>fqfwewfqw</TagKey> 
        </Tag>
      </Tags> 
      <Status>Running</Status> 
      <ClusterId/> 
      <Recyclable>false</Recyclable> 
      <RegionId>cn-beijing</RegionId>
      <GPUSpec/> 
      <OperationLocks/> 
      <GPUAmount>0</GPUAmount> 
      <InstanceChargeType>PrePaid</InstanceChargeType> 
      <ExpiredTime>2017-12-17T16:00Z</ExpiredTime> 
    </Instance>
  </Instances>
</DescribeInstancesResponse>
```

`JSON` format

``` {#json_return_success_demo}
{
	"PageNumber":"1",
	"TotalCount":"1",
	"PageSize":"10",
	"RequestId":"14A07460-EBE7-47CA-9757-12CC4761D47A",
	"Instances":{
		"Instance":[
			{
				"ImageId":"centos6u5_64_20G_aliaegis_20150130.vhd",
				"InnerIpAddress":{
					"IpAddress":[
						"10.170. XX.XXX"
					]
				},
				"InstanceId":"XXXXXXXXX",
				"EipAddress":{},
				"InternetMaxBandwidthIn":"-1",
				"ZoneId":"cn-shenzhen-a",
				"InstanceNetworkType":"classic",
				"PublicIpAddress":{
					"IpAddress":[
						"120.25. XX.XXX"
					]
				},
				"InternetChargeType":"PayByTraffic",
				"HostName":"iZ94t3s0jxkZ",
				"InstanceType":"ecs.s2.large",
				"SerialNumber":"51d1353b-22bf-4567-a176-8b3e12e43135",
				"IoOptimized":"false",
				"CreationTime":"2015-07-27T07:08Z",
				"Status":"Running",
				"VpcAttributes":{
					"PrivateIpAddress":{
						"IpAddress":[]
					}
				},
				"InternetMaxBandwidthOut":"1",
				"SecurityGroupIds":{
					"SecurityGroupId":[
						"sg-94kd0cyg0"
					]
				},
				"RegionId":"cn-shenzhen",
				"OperationLocks":{
					"LockReason":[]
				},
				"InstanceChargeType":"PostPaid",
				"ExpiredTime":"2011-09-08T16:00Z",
				"InstanceName":"dd performance test"
			}
		]
	}
}
```

## Error codes { .section}

|HTTP status code|Error code|Error message|Description|
|----------------|----------|-------------|-----------|
|404|InvalidInstanceChargeType.NotFound|The InstanceChargeType does not exist in our records|The error message returned when the specified instance type does not exist.|
|404|InvalidInternetChargeType.ValueNotSupported|The specified InternetChargeType is not valid|The error message returned when the specified billing method is invalid.|
|404|InvalidNetworkType.NotFound|The specified InstanceNetworkType is not found|The error message returned when the specified bandwidth type does not exist.|
|400|InvalidHpcClusterId.NotFound|The specified HpcClusterId is not found.|The error message returned when the specified HPC cluster ID does not exist.|
|400|InvalidHpcClusterId.Creating|The specified HpcClusterId is creating.|The error message returned when the specified HPC cluster is being created.|

[View error codes](https://error-center.aliyun.com/status/product/Ecs)

