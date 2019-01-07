# DescribeNetworkInterfaces {#DescribeNetworkInterfaces .reference}

Describes the list of elastic network interfaces \(ENI\).

## Description {#section_l24_yj4_ydb .section}

-   You can filter the results by specifying the parameters.
-   If no parameter is specified, a list containing all ENIs is returned.
-   You can view a maximum of 100 ENIs at a time.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DescribeNetworkInterfaces|
|RegionId|String|Yes|Region ID. For more information, call [DescribeRegions](../reseller.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|VSwitchId|String|No|Virtual Switch ID for the VPC.|
|PrimaryIpAddress|String|No|The primary private IP address of the ENI.|
|SecurityGroupId|String|No|Security group ID.|
|NetworkInterfaceName|String|No|ENI name.|
|Type|String|No|ENI type. Value range:-   Primary
-   Secondary

|
|InstanceId|String|No|ID of the instance currently associated with the ENI.|
|NetworkInterfaceId.N|String|No|ENI ID. You can view a maximum of 100 ENIs at a time.|
|PageNumber|Integer|No|Page number of the query result. The value is a positive integer.Default value: 1.

|
|PageSize|Integer|No|Page size of the query result.  Value range: \[1, 100\].Default value: 10.

|
|Tag.n.Key|String|Yes|The key of a tag of which n is from 1 to 20. Once you use this parameter, it cannot be a null string. It can be up to 64 characters in length. It cannot begin with "aliyun", "acs:", "http://", or "https://".|
|Tag.n.Value|String|Yes|The value of a tag of which n is a number from 1 to 20. Once you use this parameter, it can be a null string. It can be up to 128 characters in length. It cannot begin with "aliyun", "acs:", "http://", or "https://".|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|NetworkInterfaceSet|[NetworkInterfaceSet](reseller.en-US/API Reference/Data type/NetworkInterfaceSet.md#)|Information about a network interface|
|TotalCount|Integer|Total number of instances|
|PageNumber|Integer|Page number of the instance list|
|PageSize|Integer|Number of lines per page set during input|

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DescribeNetworkInterfaces
&RegionId=cn-hangzhou
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<DescribeNetworkInterfacesResponse>
    <NetworkInterfaceSets>
        <NetworkInterfaceSet>
            <AssociatedPublicIp />
            <CreationTime>2017-11-24T06:14:22Z</CreationTime>
            <InstanceId>AY121018033933eaxxxxx</InstanceId>
            <MacAddress>00:16:3e:0f:XX:XX</MacAddress>
            <NetworkInterfaceId>eni-bp17pdijfczaxZZZZxxxxx</NetworkInterfaceId>
            XXX. XXX. xx. xx
            <PrivateIpSets>
                <PrivateIpSet>
                    <AssociatedPublicIp />
                    <Primary>true</Primary>
                    <PrivateIpAddress>XXX.XXX.XX.XX</PrivateIpAddress>
                </PrivateIpSet>
            </PrivateIpSets>
            <SecurityGroupIds>
                <SecurityGroupId>sg-bp144yr32sx6ndwxxxxx</SecurityGroupId>
            </SecurityGroupIds>
            <Status>Available</Status>
            <Type>Secondary</Type>
            <VpcId>vpc-bp1j7w3gc1cexjqdxxxxx</VpcId>
            <VSwitchId>vsw-bp16usj2p27htro3xxxxx</VSwitchId>
            <ZoneId>cn-hangzhou-e</ZoneId>
        </NetworkInterfaceSet>
    </NetworkInterfaceSets>
    <PageNumber>1</PageNumber>
    <PageSize>100</PageSize>
    <RequestId>CEE5C347-0B64-4535-A061-95BE95Axxxxx</RequestId>
    <TotalCount>1</TotalCount>
</DescribeNetworkInterfacesResponse>
```

 **JSON format** 

```
{
    "NetworkInterfaceSets": {
        "NetworkInterfaceSet": [
            {
                "AssociatedPublicIp": {
                },
                "CreationTime": "2017-11-24T06:14:22Z",
                "InstanceId": "AY121018033933eaxxxxx",
                "MacAddress": "00:16:3e:0f:XX:XX",
                "NetworkInterfaceId": "eni-bp17pdijfczaxZZZZxxxxx",
                "PrivateIpAddress": "XXX.XXX.XX.XX",
                "PrivateIpSets": {
                    "PrivateIpSet": [
                        {
                            "AssociatedPublicIp": {
                            },
                            "Primary": true,
                            "PrivateIpAddress": "XXX.XXX.XX.XX"
                        }
                    ]
                },
                "SecurityGroupIds": {
                    "SecurityGroupId": [
                        "sg-bp144yr32sx6ndwxxxxx"
                    ]
                },
                "Status": "Available",
                "Type": "Secondary",
                "VpcId": "vpc-bp1j7w3gc1cexjqdxxxxx",
                "VSwitchId": "vsw-bp16usj2p27htro3xxxxx",
                "ZoneId": "cn-hangzhou-e"
            }
        ]
    },
    "PageNumber": 1,
    "PageSize": 100,
    "RequestId": "CEE5C347-0B64-4535-A061-95BE95Axxxxx",
    "TotalCount": 1
}
```

## Error codes {#ErrorCode .section}

|Error code|Error message|HTTP status code|Description|
|:---------|:------------|:---------------|:----------|
|Abs.InvalidAccount.NotFound|The Account is not found or AK is expired.|403|The specified Alibaba Cloud account does not exist. Alternatively, your AccessKey expired.|
|UnsupportedParameter|The parameters is unsupported.|400|The specified parameter does not exist. Alternatively, the specified parameter is not supported.|
|MissingParameter|The input parameter that is required for processing this request is not supplied.|400|You must specify the required parameter.|
|InvalidEcsId.NotFound|The specified EcsId is not found.|404|The specified instance ID does not exist.|
|InvalidVSwitchId.NotFound|The specified VSwitchId is not found.|404|The specified VSwitch ID does not exist.|
|InvalidSecurityGroupId.NotFound|The specified SecurityGroupId is not found.|404|The specified security group ID does not exist.|
|InvalidOperation.AvailabilityZoneMismatch|The VPC VSwitch of the specified ENI and ECS instance are not in the same availability zone.|403|The specified VPC VSwitch ID, ENI and instance ID are not in the same availability zone.|
|InvalidOperation.VpcMismatch|The VPC of the specified ENI and security group are not in the same VPC.|403|The specified ENI and security group ID are not in the same VPC.|
|InvalidSecurityGroupId.NotVpc|The specified SecurityGroupId not in VPC.|403|The specified security group ID is not of Type VPC.|

