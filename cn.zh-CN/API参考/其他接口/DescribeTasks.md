# DescribeTasks {#doc_api_1057995 .reference}

查询一个或多个异步请求的进度。

## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ecs&api=DescribeTasks)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|RegionId|String|是|cn-hangzhou|地域ID。您可以调用 [DescribeRegions](~~25609~~) 查看最新的阿里云地域列表。

 |
|Action|String|否|DescribeTasks|系统规定参数。取值：DescribeTasks

 |
|EndTime|String|否|2015-11-23T15:16:00Z|按创建时间查询，创建时间区间的终止点。按照 [ISO8601](~~25696~~) 标准表示，并需要使用UTC时间，格式为YYYY-MM-DDTHH:mm:ssZ。

 |
|OwnerAccount|String|否|ECSforCloud@Alibaba.com|RAM 用户的账号登录名称。

 |
|PageNumber|Integer|否|1|查询结果的页码，起始值为1，默认值为1。

 |
|PageSize|Integer|否|2|分页查询时设置的每页记录数，最大值100行，默认值为10。

 |
|StartTime|String|否|2015-11-23T15:10:00Z|按创建时间查询，创建时间区间的起始点。按照 [ISO8601](~~25696~~) 标准表示，并需要使用UTC时间，格式为YYYY-MM-DDTHH:mm:ssZ。

 |
|TaskAction|String|否|ImportImage|任务操作的接口名称。取值范围：

 -   ImportImage：导入镜像（ImportImage）
-   ExportImage：导出镜像（ExportImage）

 |
|TaskIds|String|否|t-bp10e8orkpqm0lc74o8X|任务ID，单次最多支持指定100个，ID之间使用半角逗号（,）分隔。

 |
|TaskStatus|String|否|Finished|任务状态。取值范围：

 -   Finished：已完成
-   Processing：运行中
-   Waiting：多任务排队中
-   Deleted：已取消
-   Paused：暂停

 默认值：无

 目前，只支持查询状态为Finished和Processing的任务，填入其他取值将不会生效。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|PageNumber|Integer|1|当前页码

 |
|PageSize|Integer|2|当前分页包含多少条目

 |
|RegionId|String|cn-hangzhou|地域ID

 |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|请求 ID

 |
|TaskSet| | |任务集合

 |
|└CreationTime|String|2015-11-24T12:50Z|创建时间

 |
|└FinishedTime|String|2015-11-24T12:50Z|结束时间

 |
|└SupportCancel|String|true|是否支持取消任务

 |
|└TaskAction|String|IMPORT\_IMAGE|任务名称

 |
|└TaskId|String|t-bp10e8orkpqm0lc74o8X|任务ID

 |
|└TaskStatus|String|Finished|任务状态

 |
|TotalCount|Integer|2|列表条条目数

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ecs.aliyuncs.com/?Action=DescribeTasks
&RegionId=cn-hangzhou
&PageNumber=1
&PageSize=2
&TaskIds=t-bp10e8orkpqm0lc74o8X
&TaskAction=ImportImage
&TaskStatus=Finished
&StartTime=2015-11-23T15:10:00Z
&EndTime=2015-11-23T15:16:00Z
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeTasksResponse>
  <PageNumber>1</PageNumber>
  <TotalCount>2</TotalCount>
  <PageSize>2</PageSize>
  <RegionId>cn-hangzhou</RegionId>
  <RequestId>E5C82807-5588-4661-9A96-350B206A7623</RequestId>
  <TaskSet>
    <Task>
      <CreationTime>2015-11-24T12:50Z</CreationTime>
      <FinishedTime>2015-11-24T12:50Z</FinishedTime>
      <SupportCancel>true</SupportCancel>
      <TaskAction>IMPORT_IMAGE</TaskAction>
      <TaskStatus>Finished</TaskStatus>
      <TaskId>t-bp10e8orkpqm0lc74o8X</TaskId>
    </Task>
    <Task>
      <CreationTime>2015-11-23T15:10Z</CreationTime>
      <FinishedTime>2015-11-23T15:16Z</FinishedTime>
      <SupportCancel>true</SupportCancel>
      <TaskAction>IMPORT_IMAGE</TaskAction>
      <TaskStatus>Finished</TaskStatus>
      <TaskId>t-23sgu0dyj</TaskId>
    </Task>
  </TaskSet>
</DescribeTasksResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"TotalCount":2,
	"TaskSet":[
		{
			"Task":[
				{
					"CreationTime":"2015-11-24T12:50Z",
					"FinishedTime":"2015-11-24T12:50Z",
					"SupportCancel":true,
					"TaskAction":"ImportImage",
					"TaskStatus":"Finished",
					"TaskId":"t-bp10e8orkpqm0lc74o8X"
				},
				{
					"CreationTime":"2015-11-23T15:10Z",
					"FinishedTime":"2015-11-23T15:16Z",
					"SupportCancel":true,
					"TaskAction":"ImportImage",
					"TaskStatus":"Finished",
					"TaskId":"t-23sgu0dyj"
				}
			]
		}
	],
	"PageSize":2,
	"RequestId":"F746C690-D9EA-4F87-AF31-8E1910FAB541",
	"RegionId":"cn-hangzhou"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|MissingParameter|An input parameter "RegionId" that is mandatory for processing the request is not supplied.|参数 RegionId 不得为空。|
|400|InvalidRegionId.NotFound|The specified RegionId does not exist.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ecs)

