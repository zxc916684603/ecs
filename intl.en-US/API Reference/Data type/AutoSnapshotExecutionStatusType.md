# AutoSnapshotExecutionStatusType {#AutoSnapshotExecutionStatusType .reference}

Type of the automatic snapshot execution status. Results of the last execution are returned.

## Node Name {#section_t2z_j2p_ydb .section}

Depends on the methods.

## Subnode {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|SystemDiskExecutionStatus|String|Returns the status of the last execution: Standby | Executed | Failed.-   Standby: The setting has just been finished and the execution has not yet started, or the automatic snapshot policy for system disks is disabled.
-   Executed: Execution succeeded.
-   Failed: Execution failed.

|
|DataDiskExecutionStatus|String|Returns the status of the last execution: Standby | Executed | Failed.-   Standby: The setting has just been finished and the execution has not yet started, or the automatic snapshot policy for data disks is disabled.
-   Executed: Execution succeeded.
-   Failed: Execution failed.

|

