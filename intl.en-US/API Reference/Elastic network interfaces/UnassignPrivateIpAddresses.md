# UnassignPrivateIpAddresses {#reference_lnv_bdd_n2b .reference}

This API allows you to delete one or more secondary private IP addresses from an Elastic Network Interface \(ENI\).

## Description {#section_phk_ddd_n2b .section}

-   This API applies only to ENIs in the **Available** \(`Available`\) or **Bound** \(`InUse`\) status.
-   For primary ENIs, the relevant instance must be in the **Running** \(`Running`\) or **Stopped** \(`Stopped`\) status.

## Request parameters {#RequestParameter .section}

|Parameter|Type|Required or not?|Description|
|:--------|:---|:---------------|:----------|
|Action|String|Yes|The name of this interface. Value: UnassignPrivateIpAddresses.|
|RegionId|String|Yes|The region ID of an ENI. For more information, call [DescribeRegions](../reseller.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|NetworkInterfaceId|String|Yes|ENI ID.|
|PrivateIpAddress.N|Array|Yes|One or more secondary private IP addresses to be deleted. The value range of `N`:-   An ENI is in the **Available** \(`Available`\) status: \[1, 10\].
-   An ENI is in the **Bound** \(`InUse` status: limited by instance types.

|

## Response parameters {#ResponseParameter .section}

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=UnassignPrivateIpAddresses
&NetworkInterfaceId=eni-m5e709m1ytxc4wx7wXXX
&PrivateIpAddress. 1=192.168.0.1
&PrivateIpAddress. 2=192.168.10.1
&<Common Request Parameters>
```

**Response example** 

**In XML format**

```
<UnassignPrivateIpAddressesResponse>
    <RequestId>04F0F334-1335-436C-A1D7-6C044FE70008</RequestId>
</UnassignPrivateIpAddressesResponse>
```

**In JSON format** 

```
{
    "RequestId": "04F0F334-1335-436C-A1D7-6C044FE70008"
}
```

## Error code {#ErrorCode .section}

|Error code|Error message|HTTP status code|Description|
|:---------|:------------|:---------------|:----------|
|InvalidParameter|the parameter\(s\) provided is\(are\) invalid.|400|The specified parameter is invalid.|
|MissingParameter|The input parameter that is mandatory for processing this request is not supplied.|400|Required parameters must be specified.|
|InvalidOperation.InvalidEniState|The operation is not allowed in the current ENI state. Expecting status is, while current status is.|400|This operation can only be performed on ENIs in the **Available** \(`Available`\) or **Bound** \(`InUse`\) status.|
|InvalidIp.IpUnassigned|The specified IP is not assigned on this ENI.|403|The specified secondary private IP address is not assigned to this ENI.|
|InvalidVSwitchId.IpInvalid|The specified IpAddress is not valid in VSwitch CIDR block.|403|You must select secondary IP addresses from the VSwitch's CIDR block.|
|Operation.Conflict|ecs task is conflicted.|403|The specified ENI is processing another task. Please try again later.|
|InvalidEniId.NotFound|The specified EniId is not found.|404|The specified `NetworkInterfaceId` does not exist.|
|InvalidVSwitchId.NotFound|The specified VSwitchId is not found.|404|The specified VSwitch does not exist.|

