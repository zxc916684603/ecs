# VpcAttributesType {#VpcAttributesType .reference}

Presents the VPC related attributes of an ECS instance.

## Node {#section_ajc_1tp_ydb .section}

Depends on the interface.

## Subnodes {#ResponseParameter .section}

|Name |Type |Description |
|:----|:----|:-----------|
|VpcId |String | ID of the VPC.|
|VSwitchId |String |ID of the VSwitch.|
|PrivateIpAddress |[IpAddressSetType](intl.en-US/API Reference/Data type/IpAddressSetType.md#)|Collection of private IP addresses.|
|NatIpAddress|String | IP address of the Alibaba Cloud product to facilitate interwork between products.|

