# DescribeSecurityGroups {#doc_api_1049674 .reference}

Queries the basic information of your security groups, such as IDs and descriptions of the security groups. The security groups are displayed in descending order by security group ID.

## Debugging {#apiExplorer .section}

You can use [API Explorer](https://api.aliyun.com/#product=Ecs&api=DescribeSecurityGroups) to perform debugging. API Explorer allows you to perform various operations to simplify API usage. For example, you can retrieve APIs, call APIs, and dynamically generate SDK example code.

## Request parameters {#parameters .section}

|Name|Type|Required|Example|Description|
|----|----|--------|-------|-----------|
|RegionId|String|Yes|cn-hangzhou| The ID of the region where your security group resides. You can call [DescribeRegions](~~25609~~) to view the latest regions of Alibaba Cloud.

 |
|Action|String|No|DescribeSecurityGroups| The operation that you want to perform. Set the value to DescribeSecurityGroups.

 |
|DryRun|Boolean|No|false| Whether the system performs a permission check only.

 -   true: A check request is sent without querying resource status. The system checks whether your AccessKey is valid, whether RAM users are authorized, and whether the required parameters are set. For a failed check, the corresponding error message is returned. For a successful check, the DryRunOperation error code is returned.
-   false: A request is sent and then the resource status is queried if the 2XX HTTP status code is returned.

 Default value: false.

 |
|NetworkType|String|No|VPC| The network type.

 |
|PageNumber|Integer|No|1| The page numbers of the security group list. Starting value: 1.

 Default value: 1.

 |
|PageSize|Integer|No|10| The number of entries to be displayed per page. Maximum value: 50.

 Default value: 10.

 |
|ResourceGroupId|String|No|rg-resourcegroupid1| The ID of the resource group to which a security group belongs.

 |
|SecurityGroupId|String|No|sg-securitygroupid| The ID of the security group.

 |
|SecurityGroupIds|String|No|\["sg-id1", "sg-id2", "sg-id2",...\]| The list of security group IDs. A list can have a maximum of 100 security group IDs, which are separated by commas \(,\) in the format of JSON array.

 |
|SecurityGroupName|String|No|test1| The name of a security group.

 |
|Tag.N.Key|String|No|FinanceDept| The tag key of the security group. Valid values of N: 1 to 20.

 |
|Tag.N.Value|String|No|FinanceJoshua| The tag values of the security group. Valid values of N: 1 to 20.

 |
|Tag.N.key|String|No|FinanceDept| The tag key of the security group.

 **Note:** This parameter will be removed in the future. We recommend that you use Tag.N.Key to enhance compatibility.

 |
|Tag.N.value|String|No|FinanceJoshua| The tag values of the security group.

 **Note:** This parameter will be removed in the future. We recommend that you use Tag.N.Value to ensure compatibility.

 |
|VpcId|String|No|v-vpcid1| The ID of the VPC to which the security group belongs.

 |

## Response parameters {#resultMapping .section}

|Name|Type|Example|Description|
|----|----|-------|-----------|
|PageNumber|Integer|1| The current page number.

 |
|PageSize|Integer|10| The number of entries per page.

 |
|RegionId|String|cn-hangzhou| The ID of the region where a security group resides.

 |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E| The ID of the request.

 |
|SecurityGroups| | | The information of security groups.

 |
|└CreationTime|String|2017-12-05T22:40:00Z| The time at which a security group is created. The time follows the [ISO8601](~~25696~~) standard and uses UTC time. The format is yyyy-MM-ddThh:mmZ.

 |
|└Description|String|FinanceDept| Description

 |
|└ResourceGroupId|String|rg-resourcegroupid1| The ID of the resource group to which a security group belongs.

 |
|└SecurityGroupId|String|sg-securitygroupid1| The ID of a security group.

 |
|└SecurityGroupName|String|FinanceJoshua| The name of a security group.

 |
|└Tags| | | The tags of the security group.

 |
|└TagKey|String|FinanceDept| The tag key of the security group.

 |
|└TagValue|String|FinanceJoshua| The tag values of the security group.

 |
|└VpcId|String|vpc-vpcid1| The ID of the VPC to which the security group belongs.

 |
|TotalCount|Integer|4| The total number of security groups.

 |

## Examples {#demo .section}

Sample requests

``` {#request_demo}
https://ecs.aliyuncs.com/?Action=DescribeSecurityGroups
&RegionId=cn-hangzhou 
&<Common request parameters>
```

Successful response examples

`XML` format

``` {#xml_return_success_demo}
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

`JSON` format

``` {#json_return_success_demo}
{
	"PageNumber":"1",
	"TotalCount":4,
	"PageSize":"10",
	"RegionId":"cn-hangzhou",
	"RequestId": "94D38899-626D-434A-891F-7E1F77A81525",
	"SecurityGroups": {
		"SecurityGroup": [
			{
				"SecurityGroupId": "sg-F876FF7BA",
				"Description": "TestByXcf"
			},
			{
				"SecurityGroupId":"sg-086FFC27A",
				"Description":"test00212"
			},
			{
				"SecurityGroupId": "sg-BA4B7975B",
				"Description":"cn-hangzhou test group"
			},
			{
				"SecurityGroupId": "sg-35F20777C",
				"Description":"cn-hangzhou test group"
			}
		]
	}
}
```

## Error codes {#section_nzo_2u0_jjc .section}

[View error codes](https://error-center.aliyun.com/status/product/Ecs)

