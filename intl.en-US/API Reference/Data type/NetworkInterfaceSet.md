# NetworkInterfaceSet {#NetworkInterfaceSet .reference}

This data type is used when you call related APIs of the ENI.

## Node {#section_r2k_5tp_ydb .section}

Determined by the interface.

## Subnodes {#ResponseParameter .section}

|Name |Type |Description |
|:----|:----|:-----------|
|NetworkInterfaceId|String|ENI ID.|
|Status|String |Status of an ENI.|
|Type|String |Category of an ENI.|
|VpcId|String |VPC ID.|
|VSwitchId|String | ID of the VSwitch that you specify in the VPC.|
|ZoneId|String |ID of the zone.|
|AssociatedPublicIp|[AssociatedPublicIp](intl.en-US/API Reference/Data type/AssociatedPublicIp.md#)|Public IP of an ENI..|
|PrivateIpAddress|String |Primary private IP of an ENI.|
|PrivateIpSet|[PrivateIpSet](intl.en-US/API Reference/Data type/PrivateIpSet.md#)|A data set made up of the information of PrivateIp.|
|MacAddress|String | MAC address of an ENI.|
|SecurityGroupIds|[SecurityGroupIdSetType](intl.en-US/API Reference/Data type/SecurityGroupIdSetType.md#)|ID of the security group to which that an ENI belongs.|
|NetworkInterfaceName|String |Name of an ENI.|
|Description |String |Description of an ENI.|
|InstanceId |String |ID of the ECS instance to which an ENI is attached.|
|CreationTime |String |The time when you create an ENI. It must comply with the standard of [ISO8601](intl.en-US/API Reference/Appendix/ISO 8601 time format.md#), and UTC time is a must. Valid format: YYYY-MM-DDThh:mmZ|

