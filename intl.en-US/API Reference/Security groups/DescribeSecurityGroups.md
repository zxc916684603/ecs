# DescribeSecurityGroups {#DescribeSecurityGroups .reference}

Describes the basic information about your security groups, such as the security group ID and description. We return and display your security groups in a descending order by the security group ID.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DescribeSecurityGroups.|
|RegionId|String|Yes|Regional ID. For more information, call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|VpcId|String|No|The ID of the VPC to which the security groups belong.|
|SecurityGroupIds|Array|No|Security group ID set. A maximum of 100 ID are supported, in the format of \["sg-Id1", "sg-Id2",  "sg-Id3"…\].|
|Tag.n.Key|String|No|The key of a tag of which n is from 1 to 20. Once you use this parameter, it cannot be a null string. It can be up to 64 characters in length. It cannot begin with "aliyun", "acs:", "http://", or "https://".|
|Tag.n.Value|String|No|The value of a tag of which n is a number from 1 to 20. Once you use this parameter, it can be a null string. It can be up to 128 characters in length. It cannot begin with "aliyun", "acs:", "http://", or "https://".|
|PageNumber|Integer|No|Displays the security groups on several pages. Initial value: 1.Default value: 1.

|
|PageSize|Integer|No|The maximum entries on a page. Maximum value: 50.Default value: 10.

|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|TotalCount|Integer|The total number of security groups.|
|PageNumber|Integer|Current page number.|
|PageSize|Integer|The number of entries on each page.|
|RegionId|String|The region ID.|
|SecurityGroups|[SecurityGroupItemType](intl.en-US/API Reference/Data type/Securitygroupitemtype.md#)|The security group information, composed by a SecurityGroupItemType collection.|

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DescribeSecurityGroups
&RegionId=cn-hangzhou
&<Common Request Parameters>
```

**Return example** 

**XML format**

```
<DescribeSecurityGroupsResponse>
    <RequestId>94D38899-626D-434A-891F-7E1F77A81525</RequestId>
    <TotalCount>4</TotalCount>
    <PageNumber>1</PageNumber>
    <PageSize>10</PageSize>
    <RegionId>cn-hangzhou</RegionId>
    <SecurityGroups>
        <SecurityGroup>
            <SecurityGroupId>sg-F876FF7BA</SecurityGroupId>
            <Description>Test</Description>
        </SecurityGroup>
        <SecurityGroup>
            <SecurityGroupId>sg-086FFC27A</SecurityGroupId>
            <Description>test00212</Description>
        </SecurityGroup>
        <SecurityGroup>
            <SecurityGroupId>sg-BA4B7975B</SecurityGroupId>
            <Description>cn-hangzhou test group</Description>
        </SecurityGroup>
        <SecurityGroup>
            <SecurityGroupId>sg-35F20777C</SecurityGroupId>
            <Description>cn-hangzhou test group</Description>
        </SecurityGroup>
    </SecurityGroups>
</DescribeSecurityGroupsResponse>
```

 **JSON format** 

```
{
    "RequestId": "94D38899-626D-434A-891F-7E1F77A81525",
    "TotalCount": 4,
    "PageSize": "10",
    "RegionId": "cn-hangzhou",
    "PageNumber": "1",
    "SecurityGroups": {
        "SecurityGroup": [{
            "SecurityGroupId": "sg-F876FF7BA",
            "Description": "TestByXcf"
        },
        {
            "SecurityGroupId": "sg-086FFC27A",
            "Description": "test00212"
        },
        {
            "SecurityGroupId": "sg-BA4B7975B",
            "Description": "cn-hangzhou test group"
        },
        {
            "SecurityGroupId": "sg-35F20777C",
            "Description": "cn-hangzhou test group"
        }]
    }
}
```

## Error codes {#ErrorCode .section}

All are common response parameters. See [Common response parameters](../intl.en-US/API Reference/Call methods/Common parameters.md#commonResponseParameters).

