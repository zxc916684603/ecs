# DeleteAutoSnapshotPolicy {#doc_api_999638 .reference}

删除一条自动快照策略。如果目标自动快照策略已经被应用到磁盘上，删除自动快照策略后，这些磁盘不再执行该策略。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ecs&api=DeleteAutoSnapshotPolicy)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|autoSnapshotPolicyId|String|是|p-233e6ylv0|自动快照策略的 ID。您可以调用 [DescribeAutoSnapshotPolicyEx](~~25530~~) 查看您可用的自动快照策略。

 |
|regionId|String|是|cn-hangzhou|自动快照所属的地域 ID。您可以调用 [DescribeRegions](~~25609~~) 查看最新的阿里云地域列表。

 |
|Action|String|否|DeleteAutoSnapshotPolicy|系统规定参数。取值：DeleteAutoSnapshotPolicy

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|请求 ID。无论调用接口成功与否，我们都会返回请求 ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ecs.aliyuncs.com/?Action=DeleteAutoSnapshotPolicy
&autoSnapshotPolicyId=p-233e6ylv0
&regionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteAutoSnapshotPolicyResponse>
  <RequestId>F3CD6886-D8D0-4FEE-B93E-1B73239673DE</RequestId>
</DeleteAutoSnapshotPolicyResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"F3CD6886-D8D0-4FEE-B93E-1B73239673DE"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|404|ParameterInvalid|The specified automatic snapshot policy does not exist.|指定的自动快照策略不存在，请您检查自动快照策略是否正确。|
|404|ParameterInvalid|The specified automatic snapshot policy does not exist in the region.|指定的自动快照策略不存在，请您检查自动快照策略是否正确。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ecs)

