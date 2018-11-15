# OperationProgressType {#OperationProgressType .reference}

Implementation details of an operation task on a resource.

## Node Name {#section_unz_jnp_ydb .section}

OperationProgress

## Subnode {#ResponseParameter .section}

|Name|Type|Description|
|:---|:---|:----------|
|RelatedItemSet|[RelatedItemSetType](intl.en-US/API Reference/Data type/RelatedItemType.md#)|Resource information type.|
|OperationStatus|String|Operation status. Possible values:-   Processing
-   Success
-   Failed

|
|ErrorCode|String|Error code. It is null unless OperationStatus is Failed.|
|ErrorMsg|String|Error message. It is null unless OperationStatus is Failed.|

