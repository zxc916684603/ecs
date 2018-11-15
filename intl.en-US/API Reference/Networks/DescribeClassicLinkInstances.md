# DescribeClassicLinkInstances {#DescribeClassicLinkInstances .reference}

Describes one or more of your classic network-connected instances that have established ClassicLink with a VPC.

## Description {#section_b3w_mmn_ydb .section}

When you call this interface, consider the following:

-   Only applicable to the classic network-connected instances.

-   You can query at most 100 instances each time.

-   Either the parameter `VpcId` or `InstanceId` must be specified.


## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DescribeClassicLinkInstances.|
|RegionId|String|Yes|The region ID of the instance. You can call [DescribeRegions](reseller.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|InstanceId|String|No|The instance ID. It must be classic network-connected instances that are linked to a VPC by using ClassicLink. At most 100 instance IDs can be specified. IDs are separated by commas \(,\). Sample: `InstanceId=i-XXX, i-XXX, i-XXX, i-XXX, ...`.|
|VpcId|String|No|VPC ID. The  [ClassicLink](../../../../reseller.en-US/User Guide/ClassicLink/Build a ClassicLink connection.md#) service must be enabled for the specified VPC.|
|PageNumber|Integer|No|Displays the information of the classic network-connected instances on several pages. Start value: 1.Default value: 1.

|
|PageSize|Integer|No|The number of the classic network-connected instances on each page. Value range: \[1, 100\].Default value: 10.

|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|TotalCount|Integer|Total number of ClassicLinks|
|PageNumber|Integer|Page number of the connection list|
|PageSize|Integer|Number of lines per page set during input|
|Links|[Link](reseller.en-US/API Reference/Data type/Link.md#)|An information set consists of VPC ID and classic network-connected instance ID.|

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DescribeClassicLinkInstances
&RegionId=cn-hangzhou
&VpcId=vpc-test
&InstanceId=i-test, i-test1
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<DescribeClassicLinkInstancesResponse>
    <RequestId>B154D309-F3E1-4AB7-BA94-FEFCA8B89001</RequestId>
    <TotalCount>2</TotalCount>
    <PageNumber>1</PageNumber>
    <PageSize>10</PageSize>
    <Links>
        <Link>
            <InstanceId>i-test</InstanceId>
            <VpcId>vpc-test</VpcId>
        </Link>
        <Link>
            <InstanceId>i-test1</InstanceId>
            <VpcId>vpc-test</VpcId>
        </Link>
    </Links>
</DescribeClassicLinkInstancesResponse>
```

 **JSON format** 

```

    "PageNumber":1,
    "Links":{
        "Link":[{
            "InstanceId":"i-test",
            "VpcId":"vpc-test"
            
           
           "InstanceId": "i-test1",
           "VpcId": "vpc-test"
           
    
    "TotalCount":2,
    "PageSize":10,
    "RequestId":"B154D309-F3E1-4AB7-BA94-FEFCA8B89001"

```

## Error codes {#ErrorCode .section}

|Error code|Error message|HTTP status code|Meaning|
|:---------|:------------|:---------------|:------|
|InvalidRegionId.Malformed|The specified RegionId is invalid.|400|The specified `RegionId` does not exist. Or you are unauthorized to access the specified region.|
|InvalidInstanceId.NotBelong|The user does not own the specified instance.|403|The specified instance does not belong to you.|
|InvalidParameter.InvalidInstanceIdAndVpcId|Either InstanceId or VpcId must be specified.|403|Either `InstanceId` or `VpcId` must be specified.|
|InvalidParameter.ToManyInstanceIds|The maximum number of specified InstanceIds is exceeded.|403|The number of `InstanceId` must be less than 100.|
|InvalidVpc.NotBelong|The user do not own the specified VPC.|403|The specified VPC does not belong to you.|
|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|404|The specified `InstanceId` does not exist.|

