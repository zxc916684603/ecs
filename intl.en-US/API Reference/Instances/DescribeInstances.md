# DescribeInstances {#DescribeInstances .reference}

Describes the details of one or more instances.

## Description {#section_phb_mrs_xdb .section}

The request parameters are filters used for describing a specific list of results. The filters use the \(`AND`\) logic, which matches a set of resources by specific criteria, such as IDs, billing methods, or tags.  A parameter with null value does not play the role of a filter However, if the `InstanceIds`  parameter is a null JSON array InstanceIds= `[]`, it is regarded as a valid filter and the responded value is null.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DescribeInstances|
|RegionId|String|Yes|Regional ID. For more information, call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|VpcId|String|No|VPC ID. |
|VSwitchId|String|No|VSwitch ID.|
|ZoneId|String|No|Zone ID.|
|InstanceIds|String|No|Instance ID.  The value can contain an array of up to 100 instance IDs. The IDs are displayed in the format of \["i-xxxxxxxxx", "i-yyyyyyyyy", … "i-zzzzzzzzz"\] and are separated by commas \(`,`\).|
|InstanceType|String|No|Instance type. |
|InstanceTypeFamily |String|No|Instance type family.|
|InstanceNetworkType|String|No|Network type of the instance. Optional values:-   Classic: Classic network
-   vpc: VPC

|
|PrivateIpAddresses|String|No|List of private IP addresses of VPC-Connected instances. This parameter is effective when `InstanceNetworkType=vpc`. The value can contain an array of up to 100 IP addresses. The IP addresses are displayed in the format of \["172.16.1.1", "172.16.2.1", … "172.16.10.1"\] and are separated by commas \(`,`\).|
|InnerIpAddresses|String|No|List of private IP addresses of classic network-connected instances. This parameter is effective when `InstanceNetworkType=classic`. The value can contain an array of up to 100 IP addresses.  The IP addresses are displayed in the format of \["10.16.1.1", "10.16.2.1", … "10.16.10.1"\] and are separated by commas \(`,`\).|
|PublicIpAddresses |String|No|List of public IP addresses of classic network-connected instances.  This parameter is effective when `InstanceNetworkType=classic`. The value can contain an array of up to 100 IP addresses. The IP addresses are displayed in the format of \["42.1.1.1", "42.1.2.1", … "42.1.10.1"\] and are separated by commas \(`,`\).|
|SecurityGroupId|String|No|Security group to which the instances belong.|
|InstanceChargeType |String|No|Billing method of the instances. Optional values:-   PrePaid: Subscribed instances
-   PostPaid: Pay-As-You-Go instances

|
|SpotStrategy|String|No|The spot strategy of a Pay-As-You-Go instance, This parameter is effective when `InstanceChargeType=PostPaid`. Optional values:-   NoSpot: standard Pay-As-You-Go instance
-   SpotWithPriceLimit: sets an example of a bid for a maximum price.
-   SpotAsPriceGo: the system will automatically bid and pay the highest price.

Default: NoSpot|
|InternetChargeType|String|No|Billing method of the instance bandwidth. Optional value:-   PayByTraffic

|
|InstanceName|String|No|Instance ID. You can use wildcard for fuzzy search.|
|ImageId|String|No|Image ID|
|DeploymentSetId|String|No|Deployment Set ID.|
|Status|String|No|Status of the instances.  Optional value:-   Running
-   Starting
-   Stopping
-   Stopped

|
|IoOptimized|String|No|Whether an instance is I/O optimized. Optional values:-   True
-   False

|
|Tag.n.Key|String|No|The key of a tag. The valid range of n is \[1, 5\]. Supports up to 64 characters. It cannot begin with aliyun, acs, http://, or https://.|
|Tag.n.Value|String|No|The value of a tag. The valid range of n is \[1, 5\]. Supports up to 128 characters. It cannot begin with aliyun, acs, http://, or https://.|
|PageNumber|Integer|No|Page number of the instance status list. Initial value: 1.Default value: 1.

|
|PageSize|Integer|No|The maximum entries on a page. Maximum: 100Default value: 10.

|

## Return parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|TotalCount|Integer|Total number of instances.|
|PageNumber|Integer|Page number of the instance list|
|PageSize|Integer|Number of lines per page set during input|
|Instances|[InstanceAttributesType](intl.en-US/API Reference/Data type/InstanceAttributesType.md#)|Array format composed of InstanceAttributesType, which returns instance information.|

## Example { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DescribeInstances
&RegionId=cn-hangzhou
&<Common Request Parameters>
```

**Response sample** 

**XML format**

```
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
        <VSwitchId>vsw-2zeh0r1pabwtg6wcssgca</VSwitchId>
        <VpcId>vpc-2zeuphj08tt7q3brdb36x</VpcId>
      </VpcAttributes>
      <InternetMaxBandwidthOut>1</InternetMaxBandwidthOut>
      <DeviceAvailable>true</DeviceAvailable>
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

 **JSON format** 

```
{
  "Instances": {
    "Instance": [
      {
        "CreationTime": "2015-07-27T07:08Z",
        "DeviceAvailable": "true",
        "EipAddress": {},
        "ExpiredTime": "2011-09-08T16:00Z",
        "HostName": "iZ94t3s0jxkZ",
        "ImageId": "centos6u5_64_20G_aliaegis_20150130.vhd",
        "Innipaddress ":{
          "IpAddress": [
            "10.170. XX.XXX"
          ]
        },
        "InstanceChargeType": "PostPaid",
        "InstanceId": "XXXXXXXXX",
        "InstanceName": "dd\u6027\u80fd\u6d4b\u8bd5",
        "InstanceNetworkType": "classic",
        "InstanceType": "ecs.s2.large",
        "InternetChargeType": "PayByTraffic",
        "InternetMaxBandwidthIn": "-1",
        "InternetMaxBandwidthOut": "1",
        "IoOptimized": "false",
        "OperationLocks": {
          "LockReason": []
        },
        "PublicIpAddress": {
          "IpAddress": [
            "120.25. XX.XXX"
          ]
        },
        "RegionId": "cn-shenzhen",
        "SecurityGroupIds": {
          "SecurityGroupId": [
            "sg-94kd0cyg0"
          ]
        },
        "SerialNumber": "51d1353b-22bf-4567-a176-8b3e12e43135",
        "Status": "Running",
        "VpcAttributes": {
          "PrivateIpAddress": {
            "IpAddress": []
          }
        },
        "ZoneId": "cn-shenzhen-a"
      }
    ]
  },
  "PageNumber": "1",
  "PageSize": "10",
  "RequestId": "14A07460-EBE7-47CA-9757-12CC4761D47A",
  "TotalCount": "1"
}
```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more error codes, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code |Description|
|:---------|:------------|:----------------|:----------|
|InvalidInstanceChargeType.NotFound|The InstanceChargeType does not exist in our records.|404|The specified `InstanceChargeType` does not exist.|
|InvalidInternetChargeType.ValueNotSupported|The specified InternetChargeType is not valid|404|The specified `InternetChargeType` is not legal.|
|InvalidNetworkType.NotFound|The specified InstanceNetworkType is not found|404|The specified `InstanceNetworkType` does not exist.|
|InvalidStatus.NotFound|The specified Status is not found|404|The specified`Status`  does not exist.|
|InvalidTag.Mismatch|The specified Tag.n.Key and Tag.n.Value are not match.|400|`Tag.n.Key` and`Tag.n.Value`specified 必须键值匹配。|
|InvalidTagCount|The specified tags are beyond the permitted range.|400|You can specify a maximum of five tags.|

