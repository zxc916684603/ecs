# RevokeSecurityGroup {#RevokeSecurityGroup .reference}

Deletes an inbound rule from a security group. This action withdraws the access policy of the inbound traffic from the instances that are in a specified security group to other devices.

## Description {#section_xwx_cp1_ydb .section}

We define the beginning of the traffic as the source, and the terminal of the traffic as the destination. For more information, see [AuthorizeSecurityGroupEgress](intl.en-US/API Reference/Security groups/AuthorizeSecurityGroupEgress.md#).

Any of the following groups of parameters can determine a Security Group Entry direction rule. Specifying only one parameter cannot determine a security group rule.

-   To withdraw the access policy of an IP address range:  `IpProtocol`, `PortRange`, \(Optional\) `SourcePortRange`, `NicType`, `Policy`, `DestCiderIp` and \(optional\) `SourceCidrIp`

-   To withdraw the access policy of instances that are in another security group: `IpProtocol`, `PortRange`, \(Optional\) `SourcePortRange`, `NicType`, `Policy`, \(Optional\) `DestCiderIp`, `DestGroupOwnerAccount`  and `DestGroupId`


## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: RevokeSecurityGroup|
|RegionId|String|Yes|The ID of the region to which the source security group belongs. For more information, call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|SecurityGroupId|String|Yes|The destination security group ID.|
|IpProtocol|String|Yes|The transport layer protocol. These values are case-insensitive. Optional values:-   icmp
-   gre
-   tcp
-   udp
-   all: Support all protocols at the same time

|
|PortRange|String|Yes|The range of destination port relevant to the transport layer protocol. Value range:-   For TCP/UDP protocol, \[1, 65535\] . Use the slash \(/\) to separate the starting and ending ports. Demonstration: `1/200`; error Demonstration: `200/1`.
-   ICMP protocol:-1/-1.
-   For GRE protocol, -1/-1.
-   For all the protocols, -1/-1.

|
|SourcePortRange|String|No|The range of the source port relevant to the transport layer protocol. Value range:-   For TCP/UDP protocol, \[1, 65535\] . Use the slash \(/\) to separate the starting and ending ports. Demonstration: `1/200`; error Demonstration: `200/1`.
-   ICMP protocol:-1/-1.
-   GRE Protocol:-1/-1.
-   All:-1/-1.

|
|NicType|String|No|The network interface type. Value range:-   internet: Internet network card.
-   intranet: intranet network card.

In mutual security group authorization, `DestGroupId` is specified, while `SourceCidrIp` is not specified, you must specify `NicType` as `intranet`. Default value: internet|
|Policy|String|No|The access permission. Value range:-   accept: access accepted
-   drop: access denied

Default value: accept|
|DestCidrIp|String|No|The destination IP address range. Only CIDR and IPv4 format are supported. Default: 0.0.0.0/0|
|SourceCidrIp|String|No|The source IP address range. Only CIDR and IPv4 format are supported. Default value: 0.0.0.0/0|
|SourceGroupId|String|No|The source security group ID. Either the `SourceGroupId` or  `SourceCidrIp` parameter must be set.  If `SourceGroupId` is specified and  `SourceCidrIp`, you can only set `NicType` to `intranet`. If both `SourceGroupId`  and `SourceCidrIp` are set, `SourceCidrIp` is authenticated  by default.|
|SourceGroupOwnerAccount|String|No|The Alibaba Cloud account of the source security group.-   If the `SourceGroupOwnerAccount` and `SourceGroupOwnerId` are not set, access policy withdrawal is performed for security groups of the same account.
-   If `SourceCidrIp` is specified. the `SourceGroupOwnerAccount` is invalid.

|
|SourceGroupOwnerId|String|No|The Alibaba Cloud account ID of the source security group.-   If neither `SourceGroupOwnerAccount` nor  `Sourcegroupowneraccount` are configured, it is considered to be a revocation of the access rights of your other security groups.
-   If the `SourceCidrIp` is already is set, the `SourceGroupOwnerId` is invalid.

|
|Priority|String|No|Authorization policy priority. Value range: \[1, 100\]. Default value: 1.

|

## Return parameters {#section_vxx_cp1_ydb .section}

All are common parameters. See [Common parameters](intl.en-US/API Reference/Call methods/Common parameters.md#commonResponseParameters).

## Example { .section}

**Request example**

```
https://ecs.aliyuncs.com/?Action=RevokeSecurityGroup
&SecurityGroupId=C0003E8B-B930-4F59-ADC0-0E209A9012B0
&SourceGroupId=sg-F876FF7BA
&SourceGroupOwnerAccount=test@aliyun.com
&IpProtocol=tcp
&PortRange=1/65535
&Priority=1
&<Common request parameters>
```

**Response sample** 

**XML format**

```
<RevokeSecurityGroupResponse>
     <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
</RevokeSecurityGroupResponse>
```

 **JSON format** 

```
{
    "RequestId":"CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
}
```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more error codes, see [API Error Center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code|Note|
|:---------|:------------|:---------------|:---|
|InvalidIpPortRange.Malformed|The specified parameter “PortRange” is not valid.|400|The specified `PortRange` is invalid.|
|InvalidIpProtocol.ValueNotSupported|The specified IpProtocol does not exist.|400|The specified `IpProtocol` does not exist.|
|InvalidNicType.ValueNotSupported|The specified NicType does not exist. |400|The specified `NicType` does not exist.|
|InvalidPolicy.Malformed|The specified parameter “Policy” is not valid.|400|The specified `Policy` is invalid.|
|InvalidSourceCidrIp.Malformed|The specified parameter “SourceCidrIp” is not valid.|400|The specified `SourceCidrIp`  is invalid.|
|InvalidSourceGroupId.Mismatch|Specified security group and source group are not in the same VPC.|400|The network type of the specified destination security group is VPC, so the destination security group must be in the same VPC.|
|MissingParameter|The input parameter “SourceGroupId” or “SourceCidrIp” cannot be both blank.|400| `SourceGroupId` or  `SourceCidrIp`.|
|InvalidGroupAuthItem.NotFound|Specified group authorized item does not exist in our records.|403|The specified outbound security group rule does not exist.|
|InvalidNicType.Mismatch|Specified nic type conflicts with the authorization record.|403|The specified `NicType` does not match the security group rule.|
|InvalidRegionId.NotFound|The specified RegionId does not exist.|404|The specified `RegionId` does not exist.|
|InvalidSecurityGroupId.NotFound|The specified SecurityGroupId does not exist.|404|The specified `SecurityGroupId` is invalid.|
|InvalidSourceGroupId.NotFound|The SourceGroupId provided does not exist in our records.|404|The specified `SourceGroupId` does not exist.|

