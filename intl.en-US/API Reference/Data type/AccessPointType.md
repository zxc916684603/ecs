# AccessPointType {#AccessPointType .reference}

Type of access point \(AP\) information.

## Node {#section_vk3_ldp_ydb .section}

It depends on the interface.

## Subnode {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|AccessPointId|String|AP ID|
|Type|String|Type of a physical connection AP; optional value:-   VPC: VPC AP, which can be connected to a physical connection accessing a VPC network.

|
|Status|String|Status of a physical connection AP; optional values:-   Recommended: The status is good, and connection is recommended.
-   Hot: The status is normal, and the number of connected users is large.
-   Full: The number of connected users reaches the upper limit, and no more users can be connected.

|
|Name|String|Name of a physical connection AP|
|Description|String|Description of a physical connection AP|
|AttachedRegionId|String|Physical region ID of an AP. If this region ID is empty, the AP does not belong to any region physically.|
|Location|String|Physical location of a physical connection AP|
|HostOperator|String|Data center carrier of a physical connection AP|

