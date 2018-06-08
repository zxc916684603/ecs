# BandwidthPackageItemType {#BandwidthPackageItemType .reference}

Description of a shared bandwidth package.

## Node name {#section_qvm_tfp_ydb .section}

Depends on the interface.

## Subnodes {#ResponseParameter .section}

|Name |Type |Description |
|:----|:----|:-----------|
|BandwidthPackageId |String |ID of a bandwidth package, for example, bwp-xxoo123|
|RegionId |String |Region |
|Name |String | Display name of an instance, which is a string of two to 128 English or Chinese characters. It must start with an uppercase/lowercase letter or a Chinese character and can contain numbers, “.”,  ":", “\_”, or “-“.  It cannot start with “http://“ or “https://“.|
|Description |String | Custom description of an instance, which is a string of two to 256 characters. This parameter is null if not specified. The default value is “null”.  It cannot start with “http://“ or “https://“.|
|ZoneId |String |Zone |
|GatewayId |String |ID of the NAT gateway associated with a bandwidth package.|
|BandWidth |String |Bandwidth value; value range: 5 to 5,000, in Mbps.|
|InstanceChargeType |String |Instance billing method. Currently, only Pay-As-You-Go is supported.  Value: PostPaid, applicable to Pay-As-You-Go instances.|
|InternetChargeType |String | Internet billing method. Optional values:  PayByTraffic Currently, only PayByBandwidth is supported.PayByTraffic

|
|ISP |String | Currently, only BGP is supported. |
|PublicIpAddresses |PublicIpAddressSetType |IP address list. Each IP address has a globally unique AllocatedId attribute and an IP address attribute.|
|BusinessStatus |String | Optional values: Normal \(normal \).FinancialLocked \(locked due to overdue payment\).

SecurityLocked \(locked by security risk control\).|
|CreationTime |String |Creation time Formatted according to the ISO8601 standard, and uses UTC time. Format: YYYY-MM-DDThh:mmZ.|

