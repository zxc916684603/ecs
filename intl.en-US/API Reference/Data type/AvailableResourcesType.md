# AvailableResourcesType {#AvailableResourcesType .reference}

Available resource types.

## Node {#section_qyr_mfp_ydb .section}

It depends on the interface.

## Subnode {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|IoOptimized|String|Whether a resource is I/O optimized or not.|
|supportedNetworkCategory|String|Available network types.|
|supportedInstanceGeneration|Array|Available instance generations.|
|supportedInstanceTypeFamily|Array|Available instance type families.|
|supportedSystemDiskCategory|Array|Categories of system disks that can be created. The return value is an array.|
|supportedDataDiskCategory|Array|Categories of data disks that can be created. The return value is an array.|
|supportedInstanceType|Array|Types of instances that can be created. The return value is an array.|

