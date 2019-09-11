# JoinResourceGroup {#JoinResourceGroup .reference}

Adds an ECS resource or service to another resource group. A resource is a cloud service entity created in the Alibaba Cloud, such as an ECS instance, ECS elastic network interface, or ECS image. A resource group is a collection of infrastructure for projects, environments, or stacks. In a resource group, you can manage all resources, monitor and run tasks, without the hassle of switching between multiple Alibaba Cloud services to view resources.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: JoinResourceGroup|
|RegionId|String|Yes|The region ID of the ECS resource.For more information, call [DescribeRegions](../reseller.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|ResourceType|String|Yes|The ECS resource type. Value: instance | disk | snapshot | image | securitygroup | ddh | eni | keypair | launchtemplateThese parameters are case-sensitive.

|
|ResourceId|String|Yes|The identifier of the resource type. For example, if ResourceType is set to `instance`, ResourceId must be set to the `InstanceId` parameter of the instance.|
|ResourceGroupId|String|Yes|The ID of the target resource group.|

## Response parameters {#ResponseParameter .section}

All are common response parameters. See [Common response parameters](../reseller.en-US/API Reference/Getting started/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=JoinResourceGroup
&RegionId=cn-hangzhou
&RsourceType=securitygroup
&SecurityGroupId=sg-securitygroupid
&ResourceGroupId=rg-resourcegrouid
&<Common Request Parameters>
```

**Response example**

**XML format**

```
<JoinResourceGroupResponse>
    <RequestId>C0003E8B-B930-4F59-ADC0-0E20xxxxxxxx</RequestId>
</JoinResourceGroupResponse>
```

**JSON format**

```
{
    "RequestId": "C0003E8B-B930-4F59-ADC0-0E20xxxxxxxx"
}
```

## Error codes {#ErrorCode .section}

|Error code|Error message|HTTP status code|Description|
|:---------|:------------|:---------------|:----------|
|MissingParameter|The required input parameter for processing this request is not provided.|403|The input parameter mandatory for processing this request must be specified.|
|InvalidResourceGroup.NotFound|The SourceGroupId provided does not exist in our records.|404|The specified resource group does not exist.|
|InvalidResourceId.NotFound|The InstanceId provided does not exist in our records.|404|The specified instance ID does not exist.|
|InvalidResourceType.NotFound|The SourceGroupId provided does not exist in our records.|404|Does not support the specified resource type.|

