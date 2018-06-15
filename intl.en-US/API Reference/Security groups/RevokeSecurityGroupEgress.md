# RevokeSecurityGroupEgress {#RevokeSecurityGroupEgress .reference}

Deletes an outbound rule from a security group. This action withdraws the access policy of the outbound traffic from the instances that are in a specified security group to other devices.

## Description {#section_nc5_pq1_ydb .section}

We define the beginning of the traffic as the source, and the terminal of the traffic as the destination. For more information, see [AuthorizeSecurityGroupEgress](intl.en-US/API Reference/Security groups/AuthorizeSecurityGroupEgress.md#).

Use the following two sets of parameters to delete a security group rule. If one rule does not exist according to these two sets of parameters, the RevokeSecurityGroupEgress fails.

-   To withdraw the access policy of an IP address range, for example, [Request example 1](#Sample1): `IpProtocol`, `PortRange`, \(Optional\) `SourcePortRange`, `NicType`, `Policy`, `DestCiderIp`, and \(Optional\) `SourceCidrIp`.

-   To withdraw the access policy of instances that are in another security group, for example, [Request example 2](#Sample2): `IpProtocol`, `PortRange`, \(Optional\) `SourcePortRange`, `NicType`, `Policy`, \(Optional\) `DestCiderIp`, `DestGroupOwnerAccount`, and `DestGroupId`.


## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: RevokeSecurityGroupEgress.|
|RegionId|String|Yes|The ID of the region to which the source security group belongs. For more information, see Regions and zones, or call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|SecurityGroupId|String|Yes| The source security group ID.|
|IpProtocol|String|Yes| The transport layer protocol. These values are case-insensitive. Optional values:-   icmp
-   gre
-   tcp
-   udp
-   all

|
|PortRange|String|Yes|The range of destination port relevant to the transport layer protocol. Optional values:-   For TCP/UDP protocol, \[1, 65535\] . You can use a forward slash \(/\) to separate the port range, expected sample: `1/200`, correct sample: `200/1`.
-   For ICMP protocol, -1/-1.
-   For GRE protocol, -1/-1.
-   For all the protocols, -1/-1.

|
|SourcePortRange|String|No|The range of source port relevant to the transport layer protocol. Optional values:-   For TCP/UDP protocol, \[1, 65535\] . You can use a forward slash \(/\) to separate the port range, expected sample: `1/200`, correct sample: `200/1`.
-   For ICMP protocol, -1/-1.
-   For GRE protocol, -1/-1.
-   For all the protocols, -1/-1.

|
|NicType|String|No| The network type. Optional values:-   internet
-   intranet

In mutual security group authorization, `DestGroupId` is specified, while `DestCidrIp` is not specified, you must specify the `NicType` as `intranet`. Default value: internet.|
|Policy|String|No| The access permission.  Optional values:-   accept: Allows the access.
-   drop: Declines the access, and sends no response to the source device.

Default value: accept.|
|DestCidrIp|String|No| The destination IP address range. Only CIDR and IPv4 format are supported. Default value: 0.0.0.0/0.|
|SourceCidrIp|String|No|The source IP address range.  Only CIDR and IPv4 format are supported. Default value: 0.0.0.0/0.|
|DestGroupId|String|No|The destination security group ID. Either the `DestGroupId` or `DestCidrIp` parameter  must be set. If `DestGroupId` is specified and `DestCidrIp` is not specified, `NicType` must be set to `intranet`. If both `DestGroupId` and `DestCidrIp` are specified,  `DestCidrIp` is authorized by default.|
|DestGroupOwnerAccount|String|No|The Alibaba Cloud account of the destination security group.-   If the `DestGroupOwnerAccount` and `DestGroupOwnerId` are not set, access policy withdrawal is performed for security groups of the same account.
-   If the `DestCidrIp` is already set, the `DestGroupOwnerAccount` is invalid.

|
|DestGroupOwnerId|String|No|The Alibaba Cloud account ID of the destination security group.-   If the `DestGroupOwnerId` and `DestGroupOwnerAccount` are not set, access policy withdrawal is performed for security groups of the same account.
-   If the `DestCidrIp` is already set, the `DestGroupOwnerId` is invalid.

|
|Priority|String|No|The priority of the outbound rule. Value range: \[1, 100\]. Default value: 1.

|

## Response parameters {#section_f54_lk5_xdb .section}

For more information about all the common response parameters, see [Common parameters](intl.en-US/API Reference/Call methods/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example 1** 

To withdraw the access policy of an IP address range.

```
https://ecs.aliyuncs.com/?Action=RevokeSecurityGroupEgress
&SecurityGroupId=sg-94n63e80l
&IpProtocol=all
&DestCidrIp=10.0.0.0/8
&PortRange=-1/-1
&NicType=intranet
&Policy=Allow
&<Common Request Parameters>
```

**Request example 2**

To withdraw the access policy of another security group.

```
https://ecs.aliyuncs.com/?Action=RevokeSecurityGroupEgress
&SecurityGroupId=sg-F876FF7BA
&DestGroupId=sg-1651FBB64
&DestGroupOwnerAccount=test@aliyun.com
&IpProtocol=tcp
&PortRange=22/22
&NicType=intranet
&Policy=Drop
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<RevokeSecurityGroupEgressResponse>
     <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
</RevokeSecurityGroupEgressResponse>
```

 **JSON format** 

```

    "RequestId":"CEF72CEB-54B6-4AE8-B225-F876FF7BA984"

```

## Error codes {#ErrorCode .section}

The following error codes are restricted to this interface. For more error codes, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code|meaning|
|:---------|:------------|:---------------|:------|
|InvalidDestCidrIp.Malformed|The specified parameter “DestCidrIp” is not valid.|400|The specified `DestCidrIp` is invalid.|
|InvalidDestCidrIp.sMalformed|The specified parameter “DestCidrIp” is not valid.|400|The specified `DestCidrIp` is invalid.|
|InvalidDestGroupId.Mismatch|Specified security group and destination group are not in the same VPC.|400|The network type of the specified destination security group is VPC, so the destination security group must be VPC-connected.|
|InvalidIpPortRange.Malformed|The specified parameter “PortRange” is not valid.|400|The specified `PortRange` is invalid.|
|InvalidIpProtocol.ValueNotSupported|The specified IpProtocol does not exist.|400|The specified `IpProtocol` does not exist.|
|InvalidNicType.ValueNotSupported|The specified NicType does not exist.|400|The specified `NicType` does not exist.|
|InvalidPolicy.Malformed|The specified parameter “Policy” is not valid.|400|The specified `Policy` is invalid.|
|MissingParameter|The input parameter “DestGroupId” or “DestCidrIp” cannot be both blank.|400|Either the `DestGroupId` or `DestCidrIp` must be specified.|
|InvalidGroupAuthItem.NotFound|Specified group authorized item does not exist in our records.|403|The specified outbound security group rule does not exist.|
|InvalidNicType.Mismatch|Specified nic type conflicts with the authorization record.|403|The specified NicType is invalid.|
|InvalidSecurityGroup.IsSame|The authorized SecurityGroupId should be different from the DestGroupId.|403|The `SecurityGroupId` and `DestGroupId` cannot indicate the same security group.|
|InvalidDestGroupId.NotFound|The DestGroupId provided does not exist in our records.|404|The specified `DestGroupId` does not exist.|
|InvalidRegionId.NotFound|The specified RegionId does not exist.|404|The specified `RegionId` does not exist.|
|InvalidSecurityGroupId.NotFound|The specified SecurityGroupId does not exist.|404|The specified `SecurityGroupId` does not exist.|

