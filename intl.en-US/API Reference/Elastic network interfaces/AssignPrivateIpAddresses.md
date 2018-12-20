# AssignPrivateIpAddresses {#reference_hlp_yrc_n2b .reference}

This API allows you to assign one or more secondary private IP addresses to an ENI. Specifically, you can set a private IP addresses within the CIDR block of the VSwitch to which an ENI belongs. Alternatively, you can specify the number of private IP addresses for ECS to assign them automatically.

## Description {#section_eq4_qvc_n2b .section}

-   This API applies only to ENIs in the **Available** \(`Available`\) or **Bound** \(`InUse`\) status.
-   For primary ENIs, the relevant instance must be in the **Running** \(`Running`\) or **Stopped** \(`Stopped`\) status.
-   When an ENI is in the **Available** \(`Available`\) status, you can assign up to 10 secondary private IP addresses to the ENI. However, once an ENI is attached to an instance, the quota of private IP addresses for the ENI is limited by the instance type. For more information, see [Instance type families](../reseller.en-US/Product Introduction/Instance type families.md#).

## Request parameters {#RequestParameter .section}

|Parameter|Type|Required or not|Description|
|:--------|:---|:--------------|:----------|
|Action|String|Yes|A parameter required by the system. Value: AssignPrivateIpAddresses.|
|RegionId|String|Yes|The region ID of an ENI. For more information, call [DescribeRegions](../reseller.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|NetworkInterfaceId|String|Yes|ENI ID.|
|PrivateIpAddress.N|Array|No|Select one or more secondary private IP addresses from the CIDR block of the VSwitch to which an ENI belongs. Value range of `N`:-   When an ENI is in the **Available** \(`Available`\) status: \[1, 10\].
-   When an ENI is in the **Bound** \(`InUse`\) status: Limited by instance types. For more information, see [Instance type families](../reseller.en-US/Product Introduction/Instance type families.md#).

To assign a secondary private IP address, you can either specify the parameter `PrivateIpAddress.N` or the parameter `SecondaryPrivateIpAddressCount`.

|
|SecondaryPrivateIpAddressCount|Integer|No|You can specify the number of private IP addresses for ECS to assign them automatically.|

## Response parameters {#ResponseParameter .section}

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=AssignPrivateIpAddresses
&NetworkInterfaceId=eni-m5e709m1ytxc4wx7wXXX
&PrivateIpAddress. 1=192.168.0.1
&PrivateIpAddress. 2=192.168.10.1
&<Common request parameters>
```

**Response examples** 

**In XML format**

```
<AssignPrivateIpAddressesResponse>
    <RequestId>04F0F334-1335-436C-A1D7-6C044FE70008</RequestId>
</AssignPrivateIpAddressesResponse>
```

**In JSON format** 

```
{
    "RequestId": "04F0F334-1335-436C-A1D7-6C044FE70008"
}
```

## Error codes {#ErrorCode .section}

|Error code|Error message|HTTP status code|Description|
|:---------|:------------|:---------------|:----------|
|InValidParameter|the parameter\(s\) “\{0\}” provided is\(are\) invalid.|400|The specified parameter is invalid.|
|MissingParameter|The input parameter “\{0\}” that is mandatory for processing this request is not supplied.|400|You must specify this required parameters.|
|InvalidOperation.InvalidEniState|The operation is not allowed in the current ENI state. Expecting status is “\{0\}” while current status is “\{1\}”.|400|This operation only supports ENIs in the ****`Available` or ****`InUse` status.|
|InvalidIp.IpUnassigned|The specified IP “\{0\}” is not assigned on this ENI.|403|The specified secondary private IP address was not assigned to this ENI.|
|InvalidVSwitchId.IpInvalid|The specified IpAddress “\{0\}” is not valid in VSwitch CIDR block “\{1\}”.|403|You must select secondary IP addresses from the VSwitch's CIDR block.|
|Operation.Conflict|ecs task is conflicted.|403|The specified ENI is processing another task. Please try again later.|
|InvalidEniId.NotFound|The specified EniId “\{0\}” is not found.|404|The specified `NetworkInterfaceId` does not exist.|
|InvalidVSwitchId.NotFound|The specified VSwitchId “\{0\}” is not found.|404|The specified VSwitch does not exist.|

