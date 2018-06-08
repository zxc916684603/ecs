# EipAddressAssociateType {#EipAddressAssociateType .reference}

Describes the EIP binding information.

## Node {#section_tvf_sjp_ydb .section}

Depends on the methods.

## Subnodes {#ResponseParameter .section}

|Name |Type |Description |
|:----|:----|:-----------|
|AllocationId |String |Instance ID with an EIP address.|
|IpAddress |String |EIP address.|
|BandWidth |Integer |Peak Internet bandwidth speed of the EIP, the unit of measurement is Mbps.Default: 5.

|
|InternetChargeType |String |Billing method of the EIP.|
|IsSupportUnassociate |Boolean |Whether the EIP can be unbound from the instance or not.|

