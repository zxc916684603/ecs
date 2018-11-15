# DescribeSecurityGroupAttribute {#DescribeSecurityGroupAttribute .reference}

Describes the authorization rule of a security group.

## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: DescribeSecurityGroupAttribute.|
|RegionId|String|Yes|The ID of the region to which the security group belongs. You can call the [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to view the region list.|
|SecurityGroupId|String|Yes|The security group ID.|
|NicType|String|No|The network interface type. Optional values:-   Internet: Internet network interface.
-   Intranet: Intranet network interface.

Default value: Internet.|
|Direction|String|No|The type of a rule. Optional values:-   Egress: The outbound authorization rules.
-   Ingress: The inbound authorization rules.
-   ALL: Both the outbound and inbound authorization rules.

Default value: all.|

## Response parameters {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|SecurityGroupId|String|Target Security Group ID.|
|SecurityGroupName|String|The security group name.|
|RegionId|String|The region ID.|
|Description|String|The security group description.|
|InnerAccessPolicy|String|Whether the requests from specified clients or security groups are allowed or not. Optional values:-   Accept: The requests are allowed.
-   Drop: The requests are rejected.

|
|Permissions|[PermissionType](intl.en-US/API Reference/Data type/PermissionType.md#)|Composed of a PermissionType collection indicates the permission rules in the security group.|
|VpcId|String| The VPC ID. If a VpcId is returned, the security group is VPC-Connected. If not, it is a classic network-connected security group.|

## Examples { .section}

**Request example** 

```
https://ecs.aliyuncs.com/?Action=DescribeSecurityGroupAttribute
&RegionId=cn-hangzhou
&SecurityGroupId=sg-F876FF7BA
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<DescribeSecurityGroupAttributeResponse>
     <RequestId>1651FBB6-4FBF-49FF-A9F5-DF5D696C7EC6</RequestId>
     <RegionId>cn-hangzhou</RegionId>
     <SecurityGroupId>C0003E8B-B930-4F59-ADC0-0E209A9012B0</SecurityGroupId>
     <Description>for demo</Description>
     <InnerAccessPolicy>Accept</InnerAccessPolicy>
        <Permissions>
         <Permission>
              <IpProtocol>ALL</IpProtocol>
              <PortRange>-1/-1</PortRange>
                <SourceGroupId>8dsmf982</SourceGroupId>
                <SourceGroupOwnerAccount>test@aliyun.com</SourceGroupOwnerAccount>
              <Policy>Accept</Policy>
              <NicType>intranet</NicType>
         </Permission>
          <Permission>
              <IpProtocol>tcp</IpProtocol>
              <PortRange>1/65535</PortRange>
              <SourceCidrIp>0.0.0.0/0</SourceCidrIp>
              <Policy>accept</Policy>
              <NicType>internet</NicType>
         </Permission>
     </Permissions>
</DescribeSecurityGroupAttributeResponse>
```

 **JSON format** 

```
{
    "RequestId": "1651FBB6-4FBF-49FF-A9F5-DF5D696C7EC6",
    "RegionId": "cn-hangzhou",
    "SecurityGroupId": "C0003E8B-B930-4F59-ADC0-0E209A9012B0",
    "Description": "for demo",
    "Permissions": {
        "Permission": [{
            "IpProtocol": "ALL",
            "PortRange": "-1/-1",
            "SourceGroupId": "8dsmf982",
            "SourceGroupOwnerAccount": "test@aliyun.com"
            "Policy": "Accept",
            "NicType": "intranet"
        },
        {
            "IpProtocol": "tcp",
            "PortRange": "1/65535",
            "SourceCidrIp": "0.0.0.0/0",
            "Policy": "accept",
            "NicType": "internet"
        }]
    }
}
```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more information, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code|Meaning|
|:---------|:------------|:---------------|:------|
|InvalidNicType.ValueNotSupported|The specified NicType does not exist.|400|The specified `NicType` does not exist.|
|InvalidRegionId.NotFound|The specified RegionId does not exist.|404|The specified `RegionId` does not exist.|
|InvalidSecurityGroupId.NotFound|The specified SecurityGroupId does not exist.|404|The specified `SecurityGroupId` does not exist.|

