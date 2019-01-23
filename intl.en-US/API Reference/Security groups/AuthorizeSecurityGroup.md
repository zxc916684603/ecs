# AuthorizeSecurityGroup {#AuthorizeSecurityGroup .reference}

Adds an inbound rule to a security group. This action permits or declines the inbound traffic from other devices to the instances that are in a specified security group.

## Description {#Description .section}

We define the beginning of the traffic as the source, and the terminal of the traffic as the destination, see the following picture.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9917/15458188613983_en-US.png)

When you call this interface, consider the following:

-   You can add up to 100 authorization rules to one security group.

-   You can set the authorization policies to `accept` or `drop`.

-   The `Priority` of a security group ranges from 1 to 100. Here, smaller the number, higher the priority is.

-   If the priorities of several authorization rules are the same, `drop` rules take the precedence.

-   The source device can be an instance with the specified IP address range \(`SourceCidrIp`\) or an instance in another security group \(`SourceGroupId`\).

-   Use the following two sets of parameters to add a security group rule. If one rule already exists according to the two sets of parameters, the `AuthorizeSecurityGroup` fails.

    -   To set the access permission of an IP address range, for example, [Request example 1](#): `IpProtocol`, `PortRange`, \(Optional\) `SourcePortRange`, `NicType`, `Policy`, \(Optional\) `DestCidrIp` and  `SourceCidrIp`.

    -   To set the access permission of instances that are in another security group, for example, [Request example 2](#): `IpProtocol`, `PortRange`, \(Optional\) `SourcePortRange`, `NicType`, `Policy`, \(Optional\) `DestCidrIp`, `SourceGroupOwnerAccount`, `and SourceGroupId.`


## Request parameters {#RequestParameter .section}

|Name|Type|Required|Description|
|:---|:---|:-------|:----------|
|Action|String|Yes| The name of this interface. Value: AuthorizeSecurityGroup.|
|RegionId|String|Yes|The region ID. For more information, see Regions and zones, or call [DescribeRegions](reseller.en-US/API Reference/Regions/DescribeRegions.md#) to obtain the latest region list.|
|SecurityGroupId|String|Yes|The ID of the destination security group.|
|IpProtocol|String|Yes|The transport layer protocol. These values are case-insensitive. Optional values:-   tcp
-   udp
-   icmp
-   gre
-   all

|
|PortRange|String|Yes|The range of destination port relevant to the transport layer protocol. Optional values:-   For TCP/UDP protocol, \[1, 65535\]. You can use a forward slash \(/\) to separate the port range, expected sample: `1/200`, incorrect sample: `200/1`.
-   For ICMP protocol, -1/-1.
-   For GRE protocol, -1/-1.
-   If the `IpProtocol` is set to `all`, the value is -1/-1.

|
|SourcePortRange|String|No|The range of source port relevant to the transport layer protocol Optional values:-   For TCP/UDP protocol, \[1, 65535\] . You can use a forward slash \(/\) to separate the port range, expected sample: `1/200`, incorrect sample: `200/1`.
-   For ICMP protocol, -1/-1.
-   For GRE protocol, -1/-1.
-   If the `IpProtocol` is set to `all`, the value is -1/-1.

|
|NicType|String|No|The network interface type. Optional values:-   internet: Internet network interface.
-   intranet: Internet network interface.

In mutual security group authorization, while `SourceGroupId` is specified and `SourceCidrIp` is not specified, you must specify `NicType` as `intranet`. Default value: internet.|
|Policy|String|No|The access permission. Optional values:-   accept: Allows the access.
-   drop: Declines the access, and sends no response to the source device.

Default value: accept.|
|DestCidrIp|String|No|The destination IP address range. Only CIDR and IPv4 format are supported. Default value: Null.|
|SourceCidrIp|String|No|The source IP address range. Only CIDR and IPv4 format are supported. Default value: Null.|
|SourceGroupId|String|No|The source security group ID. Either the `SourceGroupId` or `SourceCidrIp` parameter must be set.If the `SourceGroupId` is specified and `SourceCidrIp` is not specified, the `NicType` must be set to `intranet`.

If both the `SourceGroupId` and `SourceCidrIp` parameters are set, `SourceCidrIp` is authorized by default.

|
|SourceGroupOwnerAccount|String|No|The Alibaba Cloud account of the source security group.-   If the `SourceGroupOwnerAccount` and `SourceGroupOwnerID` are not set, authorization is performed for your other security groups.
-   If the `SourceCidrIp` is already set, the `SourceGroupOwnerAccount` is invalid.

|
|SourceGroupOwnerId|String|No|The Alibaba Cloud account ID of the source security group.-   If the `SourceGroupOwnerId` and `SourceGroupOwnerAccount` are not set, authorization is performed for security groups of the same account.
-   If the `SourceCidrIp` is already is set, the `SourceGroupOwnerId` is invalid.

|
|Priority|String|No|The authorization policy priority. Value range: \[1, 100\]. Default value: 1.

|
|Description|String|No|The security group rule description, which can contain up to 512 characters.|

## Response parameters {#section_px3_2g1_ydb .section}

All are common response parameters. See [Common response parameters](../reseller.en-US/API Reference/Getting started/Common parameters.md#commonResponseParameters).

## Examples { .section}

**Request example 1** 

Grant access permission to a specified IP address range. You can set the`NicType` for a classic network-connected security group to `internet` or `intranet`. The `NicType` of a VPC-Connected security group can be set to `intranet` only.

```
https://ecs.aliyuncs.com/?Action=AuthorizeSecurityGroup
&SecurityGroupId=sg-F876FF7BA
&SourceCidrIp=0.0.0.0/0
&IpProtocol=tcp
&PortRange=1/65535
&NicType=intranet
&Policy=Allow
&<Common Request Parameters>
```

**Request example 2**

Grant the access permission of another security group. The `NicType` can be set to `intranet` only. For mutual accesses between classic network-connected security groups, you can set the permission for another security group in the same region to access your security group. This security group can be yours or belong to other `SourceGroupOwnerAccount`. For mutual accesses between VPC-Connected security groups, you can set the permission for another security group in the same VPC to access your security group.

```
https://ecs.aliyuncs.com/?Action=AuthorizeSecurityGroup
&SecurityGroupId=sg-F876FF7BA
&SourceGroupId=sg-1651FBB64
&SourceGroupOwnerAccount=test@aliyun.com
&IpProtocol=tcp
&PortRange=1/65535
&NicType=intranet
&Policy=Drop
&<Common Request Parameters>
```

**Response example** 

**XML format**

```
<AuthorizeSecurityGroupResponse>
    <RequestId>CEF72CEB-54B6-4AE8-B225-F876FF7BA984</RequestId>
</AuthorizeSecurityGroupResponse>
```

 **JSON format** 

```
{
    "RequestId":"CEF72CEB-54B6-4AE8-B225-F876FF7BA984"
}
```

## Error codes {#ErrorCode .section}

|Error code|Error message|HTTP status code|Meaning|
|:---------|:------------|:---------------|:------|
|InvalidIpProtocol.Malformed|The specified parameter “PortRange” is not valid.|400|The specified `IpProtocol` is invalid.|
|InvalidPriority.Malformed|The specified parameter “Priority” is not valid.|400|The specified `Priority` is invalid.|
|InvalidSourceCidrIp.Malformed|The specified parameter “SourceCidrIp” is not valid.|400|The specified `SourceCidrIp` is invalid.|
|InvalidDestCidrIp.Malformed|The specified parameter “SignatureVersion” is not valid.|400|The specified `DestCidrIp` is invalid.|
|InvalidPolicy.Malformed|The specified parameter “Policy” is not valid.|400|The specified `Policy` is invalid.|
|InvalidNicType.ValueNotSupported|The specified NicType does not exist.|400|The specified `NicType` does not exist.|
|InvalidSourceGroupId.Mismatch|Specified security group and source group are not in the same VPC.|400|The network type of the specified destination security group is VPC, so the source security group must be VPC-connected.|
|InvalidNicType.Mismatch|Specified nic type conflicts with the authorization record.|400|The specified `NicType` is invalid.|
|InvalidSourceGroup.NotFound|The specified SourceGroupId does not exist.|400|The specified `SourceGroupId` does not exist.|
|InvalidPriority.ValueNotSupported|The specified Priority is invalid.|400|The specified `Priority` is invalid|
|InvalidSecurityGroupDiscription.Malformed|The specified security group rule description is not valid.|400|The specified `Description` is invalid.|
|OperationDenied|The specified IpProtocol does not exist or IpProtocol and PortRange do not match.|400|The specified `IpProtocol` does not exist. Or the specified IP protocol and port range do not match.|
|AuthorizationLimitExceed|The maximum number of authorization rules in the security group is exceeded.|403|You cannot add more than 100 authorization rules to one security group.|
|InvalidSourceGroupId.Mismatch|NicType is required or NicType expects intranet.|403|You must specify `NicType`. Or the `NicType` must be set to `intranet`.|
|InvalidNetworkType.Mismatch|The specified SecurityGroup network type should be same with SourceGroup network type \(vpc or classic\).|403|The network type of the security group must be the same.|
|InvalidParamter.Conflict|The specified SecurityGroupId should be different from the SourceGroupId.|403|The `SecurityGroupId` and `SourceGroupId` cannot be the same security group.|
|MissingParameter|The input parameter “SourceGroupId” or “SourceCidrIp” cannot be both blank.|403|You must specify `SourceGroupId` or `SourceCidrIp`.|
|InvalidSourceGroupId.NotFound|The SourceGroupId provided does not exist in our records.|404|The specified `SourceGroup` does not exist.|
|InvalidSecurityGroupId.NotFound|The specified SecurityGroupId does not exist.|404|The specified `SecurityGroupId` does not exist.|
|InvalidRegionId.NotFound|The specified RegionId does not exist.|404|The specified `RegionId` does not exist.|

