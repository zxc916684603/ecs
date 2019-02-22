# CreateAutoSnapshotPolicy {#doc_api_999636 .reference}

创建一条自动快照策略。创建的自动快照策略可以应用到任一磁盘（ApplyAutoSnapshotPolicy），成功创建的自动快照策略可以后续修改策略内容（ModifyAutoSnapshotPolicyEx）。

## 描述 {#description .section}

调用该接口时，您需要注意：

-   一个阿里云账户在一个地域最多能创建 100 条自动快照策略。
-   如果磁盘数据较多，单次创建自动快照的时长超过两个时间点间隔，则自动跳过下一时间点。 示例：您设置了 09:00、10:00、11:00 和 12:00 为自动快照时间点。由于磁盘数据较多，09:00 开始创建快照，10:20 完成创建快照，实际耗时 80 分钟。系统会跳过 10:00 时间点，等到 11:00 继续为您创建自动快照。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ecs&api=CreateAutoSnapshotPolicy)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|regionId|String|是|cn-hangzhou|自动快照策略所属的地域。您可以调用 [DescribeRegions](~~25609~~) 查看最新的阿里云地域列表。

 |
|repeatWeekdays|String|是|"1"|自动快照的重复日期，单位为天，周期为星期。取值范围：1~7，如 1 表示周一。当一星期内需要创建多次自动快照时，可以传入多个时间点：

 -   最多传入 7 个时间点。
-   多个时间点用一个格式类似 "1", "2", … "7" 的 JSON 数组表示，时间点之间用半角逗号（,）隔开。

 |
|retentionDays|Integer|是|30|自动快照的保留时间，单位为天。取值范围：

 -   -1：永久保存。
-   1~65536：指定保存天数。

 默认值：-1

 |
|timePoints|String|是|\["0", "1", … "23"\]|自动快照的创建时间点，单位为小时。取值范围：0~23，代表 00:00 至 23:00 共 24 个时间点，如 1 表示 01:00。当一天内需要创建多次自动快照时，可以传入多个时间点，最多传入 24 个时间点。

 |
|Action|String|否|CreateAutoSnapshotPolicy|系统规定参数。取值：CreateAutoSnapshotPolicy

 |
|autoSnapshotPolicyName|String|否|FinanceJoshua|自动快照策略的名称。

 -   长度为 2~128 个英文或中文字符。
-   必须以大小字母或中文开头，可包含数字、半角冒号（:）、下划线（\_）或连字符（-）。
-   不能以 http:// 和 https:// 开头。

 默认值：空

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|AutoSnapshotPolicyId|String|p-233e6ylv0|自动快照策略 ID

 |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|请求 ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ecs.aliyuncs.com/?Action=CreateAutoSnapshotPolicy
&regionId=cn-hangzhou
&repeatWeekdays=["1"]
&retentionDays=30
&timePoints=["0", "19"]
&autoSnapshotPolicyName=FinanceJoshua
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<CreateAutoSnapshotPolicyResponse>
  <RequestId>F3CD6886-D8D0-4FEE-B93E-1B73239673DE</RequestId>
  <AutoSnapshotPolicyId>p-233e6ylv0</AutoSnapshotPolicyId>
</CreateAutoSnapshotPolicyResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"F3CD6886-D8D0-4FEE-B93E-1B73239673DE",
	"AutoSnapshotPolicyId":"p-233e6ylv0"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|403|ParameterInvalid|The specified RegionId parameter is invalid.|指定的地域 ID 无效，请您检查该地域是否正确。|
|403|ParameterInvalid|The specified RepeatWeekDays parameter is invalid.|指定的日期无效，请您检查该日期是否正确。|
|403|ParameterInvalid|The specified TimePoints parameter is invalid.|指定的时间点不合法，请您查看该时间点是否填写正确。|
|403|ParameterInvalid|The specified RetentionDays parameter is invalid.|指定的保持天数 ID 不合法。|
|403|InvalidAccountStatus.NotEnoughBalance|Your account does not have enough balance.|账号余额不足，请您先充值再进行该操作。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ecs)

