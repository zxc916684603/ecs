# DetachClassicLinkVpc {#DetachClassicLinkVpc .reference}

Unlinks a classic network-connected instance from the VPC. For more information, see *VPC* topic [ClassicLink overview](../../../../reseller.en-US/User Guide/ClassicLink/ClassicLink overview.md#). After the ClassicLink is disabled, the classic network-connected instance cannot access the VPC.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DetachClassicLinkVpc.|
|RegionId|String|Yes|Region ID of the instance. For more information, call [DescribeRegions](reseller.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|InstanceId|String|Yes|ID of the classic network-connected instance.|
|VpcId|String|Yes|The ID of a VPC to which the instance is linked.|

## Response parameters {#section_f54_lk5_xdb .section}

All are common response parameters. For more information, see [Common parameters](reseller.en-US/API Reference/Getting started/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DetachClassicLinkVpc
&RegionId=cn-hangzhou
&VpcId=vpc-test
&InstanceId=i-test
&<Common Request Parameters>
```

**Response example** 

**XML format** 

```
<DetachClassicLinkVpcResponse>
    <RequestId>C0003E8B-B930-4F59-ADC0-0E209A9012A8</RequestId>
</DetachClassicLinkVpcResponse>
```

**JSON format** 

```
{
    "RequestId": "C0003E8B-B930-4F59-ADC0-0E209A9012A8"
}
```

## Error codes {#ErrorCode .section}

|Error code|Error message|HTTP status code|Meaning|
|:---------|:------------|:---------------|:------|
|InvalidInstanceId.MalFormed|The specified instance is not a classic network type instance.|400|The specified instance is not of the classic network type.|
|InvalidRegionId.Malformed|The specified RegionId is invalid.|400|The specified `RegionId` does not exist. Or you are not authorized to access the specified region.|
|InvalidVpcId.Malformed|The specified VpcId is invalid.|400|The specified `VpcId` is invalid.|
|InvalidInstanceId.NotBelong|The user does not own the specified instance.|403|The specified instance does not belong to you.|
|InvalidStatus.InstanceLocked|The specified instance is in another process list.|403|The specified instance is processing other procedures.|
|InvalidStatus.InstanceStatus|Only the Running or Stopped InstanceStatus is allowed.|403|The specified instance must be **Running** \(`Running`\) or **Stopped** \(`Stopped`\).|
|InvalidInstanceId.NotFound|The specified InstanceId does not exist.|404|The specified `InstanceId` does not exist.|

