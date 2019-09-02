# InstallCloudAssistant {#doc_api_Ecs_InstallCloudAssistant .reference}

调用InstallCloudAssistant为一台或多台实例安装云助手客户端。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ecs&api=InstallCloudAssistant&type=RPC&version=2014-05-26)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|InstanceId.N|RepeatList|是|i-bp1iudwa5b1tqa\*\*\*\*\*\*|实例ID，N的取值范围为1~50。

 |
|RegionId|String|是|cn-hangzhou|实例所在地域ID。您可以调用[DescribeRegions](~~25609~~)查看最新的阿里云地域列表。

 |
|Action|String|否|InstallCloudAssistant|系统规定参数。取值：InstallCloudAssistant

 **说明：** 调用InstallCloudAssistant后再调用[RebootInstance](~~25502~~)，云助手客户端即可生效。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|请求ID。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}
https://ecs.aliyuncs.com/?Action=InstallCloudAssistant
&InstanceId.1=i-bp11f7trr4hbi1******
&InstanceId.2=i-bp1iudwa5b1tqa******
&RegionId=cn-hangzhou
&<公共请求参数>
```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DeleteInstanceResponse>
      <RequestId>928E2273-5715-46B9-A730-238DC996A533</RequestId>
</DeleteInstanceResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RequestId":"928E2273-5715-46B9-A730-238DC996A533"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|500|InternalError.Dispatch|An error occurred when you dispatched the request.|发生未知错误。|
|404|InvalidInstance.NotFound|The specified instance does not exist.|指定的实例不存在。|

访问[错误中心](https://error-center.aliyun.com/status/product/Ecs)查看更多错误码。

