# SpotPriceType {#SpotPriceType .reference}

The price information of a spot instance.

## Node {#section_wky_fk5_ydb .section}

SpotPrices

## Subnode {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|ZoneId|String| ID of the zone to where the spot instance belongs.|
|NetworkType|String|The network type of the spot instance.|
|InstanceType|String| The instance type of the spot instance.|
|IoOptimized|String|Whether the spot instance is I/O optimized or not.|
|SpotPrice|Float|The price of the spot instance.|
|OriginPrice|Float|The price of a Pay-As-You-Go instance.|
|Timestamp|String|The time when the price of a spot instance is valid. It is in the format of YYYY-MM-DDTHH:MM:SS.|

