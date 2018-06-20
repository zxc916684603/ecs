# SpotPriceType {#SpotPriceType .reference}

The price information of a preemptible instance.

## Node {#section_wky_fk5_ydb .section}

SpotPrices

## Subnodes {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|ZoneId|String|ID of the zone to where the preemptible instance belongs.|
|NetworkType|String|The network type of the preemptible instance.|
|InstanceType|String|The instance type of the preemptible instance.|
|IoOptimized|String|Whether or not the preemptible instance is an I/O optimized instance.|
|SpotPrice|Float|The spot price of the preemptible instance.|
|OriginPrice|Float|The Pay-As-You-Go price of the instance.|
|Timestamp|String|The time when the spot price of a preemptible instance is valid. It is in the format of YYYY-MM-DDTHH:MM:SS.|

