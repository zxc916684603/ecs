# PermissionType {#PermissionType .reference}

Type of a security group rule.

## Node Name {#section_gq4_b4p_ydb .section}

Permission

## Subnode {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|IpProtocol|String|IP protocol.|
|PortRange|String|Port range.|
|SourceCidrIp|String|Source IP address segment for inbound authorization.|
|Sourcegroupid| tring|Source security group for inbound authorization.|
|SourceGroupOwnerAccount| String|Alibaba Cloud account of the source security group.|
|DestCidrIp|String|Target IP address segment for egress authorization.|
|Fatgroupid|String|Target security group for outbound authorization.|
|DestGroupOwnerAccount|String|Alibaba Cloud account of the target security group.|
|Policy|String|Authorization policy.|
|NicType|String|Network interface type.|
|Priority|String|Rule priority. |
|Direction|String|Inbound or outbound authorization.|
|Description|String|Rule description.|
|CreateTime|String|The UTC creation time of the security group rule.|

