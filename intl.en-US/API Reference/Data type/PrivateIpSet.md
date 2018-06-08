# PrivateIpSet {#PrivateIpSet .reference}

This data type is used when the private IP of an ENI is queried.

## Node {#section_dl1_5x5_ydb .section}

It depends on the interface.

## Subnode {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|PrivateIpAddress|String|Private IP of an ENI|
|Primary|Boolean|Whether the private IP of an ENI is the primary private IP or not.|
|AssociatedPublicIp |[AssociatedPublicIp](intl.en-US/API Reference/Data type/AssociatedPublicIp.md#)|Public IP of an ENI|

