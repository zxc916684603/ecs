# DescribeSnapshotPackage {#DescribeSnapshotPackage .reference}

Queries your purchased OSS storage plans in your specified Alibaba Cloud region. These storage plans can be used for snapshot storage.

## Request parameters {#RequestParameter .section}

|Parameter|Type|Required|Description|
|:--------|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DescribeSnapshotPackage.|
|RegionId|String|Yes|The ID of the region where the snapshot is stored.For more information, call [DescribeRegions](../reseller.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|PageNumber|Integer|No|The page number of the OSS storage plans list. Initial value: 1.Default value: 1.

|
|PageSize|Integer|No|The maximum number of entries on a page. Maximum value: 100.Default value: 10.

|

## Response parameters {#ResponseParameter .section}

|Parameter|Type|Description|
|:--------|:---|:----------|
|TotalCount|Integer|The total number of OSS storage plans.|
|PageNumber|Integer|The page number of the OSS storage plans list.|
|PageSize|Integer|The maximum number of entries on a page.|
|SnapshotPackages|Array of [SnapshotPackage](#)|An array of OSS storage plan parameters.|

|Parameter|Type|Description|
|:--------|:---|:----------|
|StartTime|String|The time when the OSS storage plan was purchased.The time format follows the [ISO8601](../reseller.en-US/API Reference/Appendix/ISO 8601 Time Format.md#) standard, and the UTC time is used. The format is yyyy-MM-ddTHH:mm:ssZ.|
|EndTime|String|The time when the OSS storage plan expires.The time format follows the [ISO8601](../reseller.en-US/API Reference/Appendix/ISO 8601 Time Format.md#) standard, and the UTC time is used. The format is yyyy-MM-ddTHH:mm:ssZ.|
|InitCapacity|Long|The storage space offered by the OSS storage plan.|
|DisplayName|String|The name of the OSS storage plan.|

## Examples {#Samples .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DescribeSnapshotPackage
&RegionId=cn-hangzhou
&<Common Request Parameters>
```

**Response examples**

**XML format**

```
<DescribeSnapshotPackageResponse>
	<TotalCount>1</TotalCount>
	<PageNumber>1</PageNumber>
	<PageSize>5</PageSize>
	<SnapshotPackages>
		<SnapshotPackage>
			<StartTime>2017-11-30T06:32:31Z</StartTime>
			<EndTime>2018-11-30T06:32:31Z</EndTime>
			<InitCapacity>500</InitCapacity>
			<DisplayName>sp-snapshotpackage1</DisplayName>
		</SnapshotPackage>
	</SnapshotPackages>
	<RequestId>ACD9BBB0-A9D1-46D7-9630-B7A69889E110</RequestId>
</DescribeSnapshotPackageResponse>
```

**JSON format**

```
{
	"TotalCount": "1",
	"PageNumber": "1",
	"PageSize": "5",
	"SnapshotPackages": {
		"SnapshotPackage": [
			"StartTime": "2017-11-30T06:32:31Z",
			"EndTime": "2018-11-30T06:32:31Z",
			"InitCapacity": "500",
			"DisplayName": "sp-snapshotpackage1"
		]
	},
	"RequestId": "ACD9BBB0-A9D1-46D7-9630-B7A69889E110"
}
```

## Error codes {#ErrorCode .section}

All are common error codes. For more information, see [Common error codes](../reseller.en-US/API Reference/Getting started/Response results.md#commonErrorCodes).

