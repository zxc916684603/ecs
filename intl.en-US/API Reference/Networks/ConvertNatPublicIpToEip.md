# ConvertNatPublicIpToEip {#ConvertNatPublicIpToEip .reference}

ConvertNatPublicIpToEip changes the public IP \(NatPublicIp\) of a Virtual Private Cloud \(VPC\) connected instance to an Elastic IP \(EIP\).

## Description {#section_o52_y3n_ydb .section}

When using this operation, consider the following:

-   The network type of the specified instance must be VPC.
-   The status of the specified instance must be **Stopped** \(`Stopped`\) or **Running** \(`Running`\).
-   The outbound bandwidth of an ECS instance must be greater than 0 Mbps, in case the ECS instance does not have a public IP `NatPublicIp`.
-   This action fails if you have already bound an EIP to the specified instance.
-   This action fails if ongoing configuration changes exist for the specified ECS instance.
-   This action fails if the specified instance expires in the next 24 hours.
-   Once the public IP `NatPublicIp` is changed to an EIP, you are billed for using the EIP service. For more information, see EIP document .

## Request parameters {#RequestParameter .section}

|Name |Type|Required|Description|
|:----|:---|:-------|:----------|
|Action|String|Yes|The operation that you want to perform. Value: ConvertNatPublicIpToEip.|
|RegionId|String|Yes|The region ID. For more information, use the [DescribeRegions](reseller.en-US/API Reference/Regions/DescribeRegions.md#) API to obtain the latest region list.|
|InstanceId|String|Yes|Identifier of the target ECS instance.|

## Response parameters {#ResponseParameter .section}

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=ConvertNatPublicIpToEip
&RegionId=cn-hangzhou
&InstanceId=i-test
&<Common Request Parameters> 
```

**Response example** 

**XML format**

```
<ConvertNatPublicIpToEipResponse>
    <RequestId>B154D309-F3E1-4AB7-BA94-FEFCA8B89001</RequestId>
</ConvertNatPublicIpToEipResponse>
```

**JSON format** 

```
{
   "RequestId":"B154D309-F3E1-4AB7-BA94-FEFCA8B89001"
}
```

## Error codes {#ErrorCode .section}

|Error code|Error message|HTTP status code|Description|
|:---------|:------------|:---------------|:----------|
|InvalidRegionId.Malformed|The specified RegionId is invalid.|400|The specified `RegionId` does not exist, or you are not authorized to access the specified region.|
|InvalidEndTime.Malformed|The specified instance expires in the next 24 hours.|403|The specified instance expires in the next 24 hours.|
|InvalidInstanceId.PlanedChange|The instance has incomplete changes.|403|Ongoing configuration changes exist for the specified ECS instance.|
|InvalidInstanceStatus.Released|The specified instance has been released.|403|The specified instance has been released.|
|IncorrectInstanceStatus|The instance status does not support this operation. The instance may be expired, upgrading, starting, or locked.|404|The specified instance must be in the **Stopped** \(`Stopped`\) or **Running** \(`Running`\) status.|
|InstanceTypeNotSupported|The specified instance is a subscription instance with a specified bandwidth.|404|The specified instance is a subscription instance with a specified bandwidth.|
|InvalidInstance.ZeroBandwidth|The public network bandwidth for the specified instance is zero. That is, this instance does not have a public IP.|404|The outbound bandwidth of an ECS instance must be greater than 0 Mbps.|
|InvalidInstanceId.NotFound|The specified instance does not exist, or does not belong to you.|404|The specified instance does not exist or does not belong to you.|
|OperationDenied|The network type of the specified instance is not VPC.|404|The specified instance must be VPC-Connected.|

