# TaskType {#TaskType .reference}

Task type.

## Node  {#section_zdc_2sp_ydb .section}

TaskSetType

## Subnodes {#ResponseParameter .section}

|Name |Type |Description |
|:----|:----|:-----------|
|TaskId|String |Task ID.|
|Action |String |The target method to perform.|
|TaskStatus|String |Task status. Possible values: -   Finished
-   Processing

|
|SupportCancel|Boolean|Whether a task can be canceled. Optional values:-   true
-   false

|
|CreationTime |String |Task creation time, which follows the ISO8601 standard and uses UTC time. It is in the format of YYYY-MM-DDThh:mmZ.|
|FinishedTime|String |Task completion time, which follows the ISO8601 standard and uses UTC time. It is in the format of YYYY-MM-DDThh:mmZ.|

