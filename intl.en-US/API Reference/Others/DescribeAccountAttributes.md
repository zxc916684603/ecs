# DescribeAccountAttributes {#DescribeAccountAttributes .reference}

Queries the maximum number of ECS resources that you can create in a region. Specifically, you can use this interface to query the numbers of security groups, elastic network interfaces \(ENIs\), Pay-As-You-Go vCPU cores, preemptible instance vCPU cores, and dedicated hosts, local network type, and whether your account has been authenticated by real name.

## Description {#section_awr_p1k_b2b .section}

After registering with an Alibaba Cloud account, you can create a certain number of ECS resources in different regions. For more information, see [Limitations](../../../../reseller.en-US/User Guide/Limitations.md#). To expand the resource capacity, you can open a ticket as needed.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|Name of this interface. Value: DescribeAccountAttributes.|
|RegionId|String|Yes|Region ID. You can call [DescribeRegions](reseller.en-US/API Reference/Regions/DescribeRegions.md#) to query the latest region list.|
|ZoneId|String|No|Zone ID.|
|AttributeName.N|String|No|Resource usage limit. `N` ranges from 1 to 8. Value range:-   instance-network-type: Available network types in the current region.
-   max-security-groups: The number of security groups.
-   max-elastic-network-interfaces: Number of ENIs in the current region.
-   max-postpaid-instance-vcpu-count: Number of Pay-As-You-Go instance vCPU cores in the current region.
-   max-spot-instance-vcpu-count: Number of preemptible instance vCPU cores in the current region.
-   max-delicated-hosts: Number of dedicated hosts in the current region.
-   supported-postpaid-instance-types: Pay-As-You-Go I/O optimization instance types in the current region.
-   real-name-authentication: Whether your account has been authenticated by real name.

Default value: null.|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|AccountAttributeItem|Array of [AccountAttributeItems](#)|A collection of information about account privileges in a specified region.|

**AccountAttributeItems** 

|Name|Type|Description|
|:---|:---|:----------|
|AttributeName|String|Resource usage limit. Value range:-   instance-network-type: Available network types in the current region.
-   max-security-groups: Number of security groups.
-   max-elastic-network-interfaces: Number of ENIs in the current region.
-   max-postpaid-instance-vcpu-count: Number of Pay-As-You-Go instance vCPU cores in the current region.
-   max-spot-instance-vcpu-count: Number of preemptible instance vCPU cores in the current region.
-   max-delicated-hosts: Number of dedicated hosts in the current region.
-   supported-postpay-instance-types: Pay-As-You-Go I/O optimization instance types in the current region.
-   real-name-authentication: Whether your account has been authenticated by real name.

|
|AttributeValues|[ValueItem](#)|Resource usage limit.|

 **ValueItem** 

|Name|Type|Description|
|:---|:---|:----------|
|Value|String|Resource usage limit in the current region or all regions. Value range:-   The value of 0 or a positive integer is returned when the value is `max-security-groups`, `max-elastic-network-interfaces`, `max-postpaid-instance-vcpu-count`, `max-delicated-hosts`, or `max-spot-instance-vcpu-count`.
-   A possible value of instance types is returned when the value is `supported-postpay-instance-types` For more information, see [Instance type families](../../../../reseller.en-US/Product Introduction/Instance type families.md#).
-   The value of yes, none, or unnecessary is returned when the value is `real-name-authentications`.
-   The value of vpc or classic is returned when the value is `instance-network-type`.

|

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DescribeAccountAttributes
&RegionId=cn-hangzhou&
&<Common Request Parameters>
```

**Response example** 

**XML format** 

```
<DescribeAccountAttributesResponse>
    <AccountAttributeItems>
        <AccountAttributeItem>
            <AttributeName>max-security-groups</AttributeName>
            <AttributeValues>
                <ValueItem>
                    <Value>800</Value>
                <ValueItem>
            </AttributeValues>
        </AccountAttributeItem>
          <AccountAttributeItem>
            <AttributeName>instance-network-type</AttributeName>
            <AttributeValues>
                <ValueItem>
                    <Value>vpc</Value>
                    <Value>classic</Value>
                <ValueItem>
            </AttributeValues>
        </AccountAttributeItem>
     </AccountAttributeItems>
    <RequestId>675B6D89-A3EB-4987-BAF3-610591E0D019</RequestId>
</DescribeAccountAttributesResponse>
```

**JSON format** 

```
{
    "AccountAttributeItems": {
        "AccountAttributeItem": [
            {
                "AttributeValues": {
                    "ValueItem": [
                        {
                            "Value": "100"
                        }
                    ]
                },
                "AttributeName": "max-security-groups"
            },
            {
                "AttributeValues": {
                    "ValueItem": [
                        {
                            "Value": "2"
                        }
                    ]
                },
                "AttributeName": "max-dedicated-hosts"
            },
            {
                "AttributeValues": {
                    "ValueItem": [
                        {
                            "Value": "1000"
                        }
                    ]
                },
                "AttributeName": "max-postpaid-instance-vcpu-count"
            },
            {
                "AttributeValues": {
                    "ValueItem": [
                        {
                            "Value": "1000"
                        }
                    ]
                },
                "AttributeName": "max-spot-instance-vcpu-count"
            },
            {
                "AttributeValues": {
                    "ValueItem": [
                        {
                            "Value": "5000"
                        }
                    ]
                },
                "AttributeName": "max-elastic-network-interfaces"
            },
            {
                "AttributeValues": {
                    "ValueItem": [
                        {
                            "Value": "yes"
                        }
                    ]
                },
                "AttributeName": "real-name-authentication"
            },
            {
                "AttributeValues": {
                    "ValueItem": [
                        {
                            "Value": "vpc"
                        }
                    ]
                },
                "AttributeName": "instance-network-type"
            },
            {
                "AttributeValues": {
                    "ValueItem": [
                        {
                            "Value": "ecs.f3-c16f1.4xlarge"
                        },
                        {
                            "Value": "ecs.g5.2xlarge"
                        }
                    ]
                },
                "AttributeName": "supported-postpaid-instance-types"
            }
        ]
    },
    "RequestId": "8CE45CD5-31FB-47C2-959D-CA8144CE9F42"
}
```

## Error codes {#ErrorCode .section}

|Error code|Error message|HTTP status code|Meaning|
|:---------|:------------|:---------------|:------|
|InvalidRegionId.NotFound|The specified RegionId does not exist.|404|The specified `RegionId` does not exist.|

