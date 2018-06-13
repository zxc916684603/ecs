# AuthorizeSecurityGroupEgress {#AuthorizeSecurityGroupEgress .reference}

Adds an outbound rule to a security group. This action permits or declines the outbound traffic from the instances that are in a specified security group to other devices. 

## Description {#section_ytt_yl1_ydb .section}

We define the beginning of the traffic as the source, and the terminal of the traffic as the destination, see the following figure.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9918/6061_en-US.png)

When you call this interface, consider the following:

-   You can add up to 100 authorization rules to one security group.

-   You can set the authorization policies to `accept` or `drop`.

-   The `Priority` of a security group ranges from 1 to 100. Here, a smaller number means a higher priority.

-   If the priorities of several authorization rules are the same. The `drop` rules take the priority by default.

-   The destination device can be an IP address range \(`DestCidrIp`\) or the instances that are in another security group \(`DestGroupId`\).

-   Use the following two sets of parameters to add a security group rule. If one rule already exists according to the two sets of parameters, the `AuthorizeSecurityGroupEgress` fails.

    -   Sets the access rights for the specified IP address segment, such as [request Example 1](#Sample1): `IpProtocol`, `PortRange`, \(optional\) `SourcePortRange`, `NicType`, `Policy`, `DestCiderIp` \(Optional\)`SourceCidrIp`.

    -   Sets the access rights for other security groups, such as [request Example 2](#Sample2): `IpProtocol`, `PortRange`, \(optional\) `SourcePortRange`, `NicType`, `Policy`, `DestCiderIp`, `DestGroupOwnerAccount` and `DestGroupId`.


## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes|The name of this interface. Value: AuthorizeSecurityGroupEgress.|
|RegionId|String|Yes|The ID of the region to which the source security group belongs. For more information, call [DescribeRegions](intl.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|SecurityGroupId|String|Yes|The source security group ID.|
|IpProtocol|String|Yes|The transport layer protocol. Not case sensitive. Optional values:-   icmp
-   gre
-   tcp
-   udp
-   all: Supports all protocols at the same time

|
|PortRange|String|Yes|The range of destination port relevant to the transport layer protocol. Value range:-   For TCP/UDP protocol, \[1, 65535\] . Use the slash \(/\) to separate the starting and ending ports. Demonstration: `1/200`; error Demonstration: `200/1`.
-   ICMP protocol:-1/-1.
-   For GRE protocol, -1/-1.
-   For all the protocols, -1/-1.

|
|SourcePortRange|String|No|The range of source port relevant to the transport layer protocol. Value range:-   TCP/UDP protocol: \[1, 65535\] . Use the slash \(/\) to separate the starting and ending ports. Demonstration: `1/200`; error Demonstration: `200/1`.
-   ICMP protocol:-1/-1.
-   GRE Protocol:-1/-1.
-   All:-1/-1.

|
|NicType|String|No|The network interface type. Value range:-   internet: internet network card
-   intranet: intranet network card

In mutual security group authorization, `DestGroupId` is specified,  while `DestCidrIp`  is not specified, you must specify the `NicType` as `intranet`. Default value: internet|
|Policy|String|No|The access permission. Value range:-   accept: access accepted
-   drop: access denied

Default value: accept|
|DestCidrIp|String|No|The destination IP address range. Only CIDR and IPv4 format are supported. Default: 0.0.0.0/0|
|SourceCidrIp|String|No|The source IP address range. Only CIDR and IPv4 format are supported. Default value: 0.0.0.0/0|
|DestGroupId|String|No|The destination security group ID. Either the `DestGroupId` or  `DestCidrIp` parameter  must be set. If `DestGroupId` is specified and `DestCidrIp` is not specified, `NicType` must be set to `intranet`. If `DestGroupId` and  `DestCidrIp` are specified,  `DestCidrIp`  by default.|
|DestGroupOwnerAccount|String|No|The Alibaba Cloud account of the destination security group. -   If the  `DestGroupOwnerAccount` `DestGroupOwnerId` are not set, authorization is performed for security groups of the same account.
-   If the `DestCidrIp` is already set, the `DestGroupOwnerAccount` is invalid.

|
|DestGroupOwnerId|String|No|The Alibaba Cloud account ID of the destination security group.-   If the `DestGroupOwnerAccount` and `Destgroupowneraccount` are not set, it is considered to be setting access rights for your other security groups.
-   If you have already set the `DestCidrIp` parameter, the parameter `DestGroupOwnerId` is invalid.

|
|Priority|String|No|Authorization policy priority. Value range: \[1, 100\]. Default value: 1.

|
|Description|String|No|The security group rule description,  which can contain up to 512 characters.|

## Return parameters {#section_y5t_yl1_ydb .section}

All are common parameters. See [Common parameters](intl.en-US/API Reference/Call methods/Common parameters.md#commonResponseParameters).

## Example { .section}

**Request example 1** 

Grant access permission to a specified IP to a specified IP address range. Then, you can set the network interface \(`NicType`\) of a classic network-connected security group to Internet interface \(`internet`\) or  [intranet](../../../../intl.en-US/Product Introduction/Network and security/Intranet.md#) \(`intranet`\). VPC `NicType` of a VPC-Connected security group can be set to `intranet` only.

```
https://ecs.aliyuncs.com/?Action=AuthorizeSecurityGroupEgress
&SecurityGroupId=sg-94n63e80l
&IpProtocol=icmp
&DestCidrIp=10.0.0.0/8
&PortRange=-1/-1
&NicType=intranet
&Policy=Allow
&<Common request parameters>
```

**Request example 2**

Grant the access permission of another security group. Then, you can only set the network interface \(`NicType`\) to Internet interface \(`intranet`\). For mutual accesses between classic network-connected security groups, you can set the permission for another security group in the same region to access your security group. it can be yours or created by other Alibaba Cloud accounts\(`DestGroupOwnerAccount`\). VPC it must be in the same VPC of the source security group.

```
https://ecs.aliyuncs.com/?Action=AuthorizeSecurityGroupEgress
&SecurityGroupId=sg-F876FF7BA
&DestGroupId=sg-1651FBB64
&DestGroupOwnerAccount=test@aliyun.com
&IpProtocol=tcp
&PortRange=22/22
&NicType=intranet
&Policy=Drop
&<Common request parameters>
```

**Response sample** 

**XML format**

```
<AuthorizeSecurityGroupEgressResponse>
    <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
</AuthorizeSecurityGroupEgressResponse>
```

 **JSON format** 

```
{
    "RequestId":"CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
}
```

## Error codes {#ErrorCode .section}

Error codes specific to this interface are as follows. For more error codes, visit the [API error center](https://error-center.alibabacloud.com/status/product/Ecs).

|Error code|Error message|HTTP status code|Note|
|:---------|:------------|:---------------|:---|
|InvalidDestCidrIp.Malformed|The specified parameter “DestCidrIp” is not valid.|400|The specified `DestCidrIp` is invalid.|
|Invaliddestcidrip. Malformed|The specified parameter DestCidrIp is not valid.|400|The specified `DestCidrIp` is not valid.|
|InvalidDestGroup.NotFound|Specified destination security group does not exist.|400|The specified `DestGroupId` is invalid.|
|InvalidDestGroupId.Mismatch|Specified security group and destination group are not in the same VPC.|400|The network type of the specified destination security group is VPC, so the destination security group must be VPC-connected.|
|InvalidNicType.Mismatch|Specified nic type conflicts with the authorization record.|400|The specified  `NicType` is invalid.|
|InvalidNicType.ValueNotSupported|The specified NicType does not exist.|400|The specified `NicType` does not exist.|
|InvalidPolicy.Malformed|The specified parameter “Policy” is not valid.|400|The specified `Policy` is invalid.|
|InvalidPortRange.Malformed|The specified parameter “PortRange” is not valid.|400|The specified `PortRange` is invalid.|
|InvalidPriority.Malformed|The specified parameter “Priority” is not valid.|400|The specified `Priority` is invalid.|
|InvalidPriority.ValueNotSupported|The specified Priority is invalid.|400|The specified `Priority` is invalid.|
|InvalidSecurityGroupDiscription.Malformed|The specified security group rule description is not valid.|400|The specified `Description` is invalid.|
|InvalidSourceCidrIp.Malformed|The specified parameter “SourceCidrIp” is not valid.|400|The specified `SourceCidrIp` is invalid.|
|InvalidSourcePortRange.Malformed|The specified parameter “SourcePortRange” is not valid.|400|The specified `SourcePortRange` is invalid.|
|OperationDenied|The specified IpProtocol does not exist or IpProtocol and PortRange, SourcePortRange do not match.|400|The specified `IpProtocol` does not exist. Or the IpProtocol and the PortRange are incorrectly matched|
|AuthorizationLimitExceed|The maximum number of authorization rules in the security group is exceeded.|403|You cannot add more than 100 authorization rules to one security group.|
|InvalidDestGroupId.Mismatch|NicType is required or NicType expects intranet.|403|You must specify the `NicType`. Or the `NicType` must be `intranet`.|
|InvalidNetworkType.Conflict|The specified SecurityGroup network type should be same with SourceGroup network type \(VPC or classic\).|403|The network type of the security group must be the same.|
|InvalidParamter.Conflict|The specified SecurityGroupId should be different from the DestGroupId.|403|The `SecurityGroupId` and `DestGroupId` cannot indicate the same security group.|
|InvalidSecurityGroup.IsSame|The authorized SecurityGroupId should be different from the DestGroupId.|403|Parameters `SecurityGroupId` and `DestGroupId` Cannot be the same.|
|MissingParameter|The input parameter “DestGroupId” or “DestCidrIp” cannot be both blank.|403|Either the `DestGroupId` or `DestCidrIp` must be specified.|
|InvalidDestGroupId.NotFound|The DestGroupId provided does not exist in our records.|404|The specified `DestGroupId` does not exist.|
|InvalidRegionId.NotFound|The specified RegionId does not exist.|404|The specified `RegionId` does not exist.|
|InvalidSecurityGroupId.NotFound|The specified SecurityGroupId does not exist.|404|The specified `SecurityGroupId` does not exist.|

