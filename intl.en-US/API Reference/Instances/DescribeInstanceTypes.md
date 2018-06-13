# DescribeInstanceTypes {#DescribeInstanceTypes .reference}

Describes the resources list of instance types provided by Alibaba Cloud ECS. For more information, see [Instance type families](../../../../intl.en-US/Product Introduction/Instance type families.md#).

## Description {#section_c31_xmt_xdb .section}

The DescribeInstanceTypes returns the list of instance types that are the same as the list of the Pay-As-You-Go instances on the instance creation webpage.  For more information, see [Pay-As-You-Go](../../../../intl.en-US/Pricing/Pay-As-You-Go.md#) and  [Limits](../../../../intl.en-US/User Guide/Limits.md#).

If you want to create instances that are not available to you, [open a ticket](https://workorder-intl.console.aliyun.com/#/ticket/createIndex) to make them available.

## Request parameters {#RequestParameter .section}

|Name|Type|Required| Description|
|:---|:---|:-------|:-----------|
|Action|String|Yes|The name of this interface.  Value: DescribeInstanceTypes.|
|InstanceTypeFamily|String|No|The family of the instance type. For more information, see [Instance type families](../../../../intl.en-US/Product Introduction/Instance type families.md#).|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|InstanceTypes|[InstanceTypeItemType](intl.en-US/API Reference/Data type/InstanceTypeItemType.md#)|A collection composed of `InstanceTypeItemType`.|

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DescribeInstanceTypes
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<DescribeInstanceTypesResponse>
    <RequestId>1651FBB6-4FBF-49FF-A9F5-DF5D696C7EC6</RequestId>
    <InstanceTypes>
        <InstanceType>
            <InstanceTypeId>ecs.t1.xsmall</InstanceTypeId>
            <CpuCoreCount>1</CpuCoreCount>
            <MemorySize>0.5</MemorySize>
        </InstanceType>
        <InstanceType>
            <InstanceTypeId>ecs.t1.small</InstanceTypeId>
            <CpuCoreCount>1</CpuCoreCount>
            <MemorySize>1</MemorySize>
        </InstanceType>
    </InstanceTypes>
</DescribeInstanceTypesResponse>
```

 **JSON format** 

```

    "RequestId": "1651FBB6-4FBF-49FF-A9F5-DF5D696C7EC6",
    "InstanceTypes": {
        "InstanceType": [{
            "InstanceTypeId": "ecs.t1.xsmall",
            "CpuCoreCount": 1,
            "MemorySize": 0.5
        
        
            "InstanceTypeId": "ecs.t1.small",
            "CpuCoreCount": 1,
            "MemorySize": 1
        
    }

```

## Error codes {#ErrorCode .section}

All are common error codes. For more information, see [Common error codes](https://error-center.alibabacloud.com/status/product/Ecs).

