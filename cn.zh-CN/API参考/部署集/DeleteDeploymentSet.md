# DeleteDeploymentSet {#DeleteDeploymentSet .reference}

删除一个部署集。

## 请求参数 {#RequestParameter .section}

|名称|类型|是否必需|描述|
|:-|:-|:---|:-|
|Action|String|是|系统规定参数，取值：DeleteDeploymentSet|
|RegionId|String|是|部署集所属地域ID。您可以调用[DescribeRegions](../cn.zh-CN/API参考/地域/DescribeRegions.md#)查看最新的阿里云地域列表。|
|DeploymentSetId|String|是|部署集ID。如果部署集中仍有实例存在，则无法删除。|

## 返回参数 {#ResponseParameter .section}

全是公共返回参数。参阅[公共返回参数](../cn.zh-CN/API参考/HTTP调用方式/公共参数.md#commonResponseParameters)。

## 示例 { .section}

**请求示例** 

```
https://ecs.aliyuncs.com/?Action=DeleteDeploymentSet
&RegionId=cn-hangzhou
&DeploymentSetId=ds-bp1frxuzdg87zh4pzqkc
&<公共请求参数>
```

```
https://ecs.example.com/?Action=DeleteDeploymentSet
&RegionId=cn-hangzhou
&DeploymentSetId=ds-bp1frxuzdg87zh4pzqkc
&<公共请求参数>
```

**返回示例**

**XML 格式**

```
<DeleteDeploymentSetResponse>
	<RequestId>04F0F334-1335-436C-A1D7-6C044FE73368</RequestId>
</DeleteDeploymentSetResponse>
```

**JSON 格式**

```
{
	"RequestId": "04F0F334-1335-436C-A1D7-6C044FE73368"
}
```

## 错误码 {#ErrorCode .section}

以下为本接口特有的错误码。更多错误码，请访问[API错误中心](https://error-center.aliyun.com/status/product/Ecs)。

|错误代码|错误信息|HTTP状态码|说明|
|:---|:---|:------|:-|
|MissingParameter|The input parameter “DeploymentSetId” that is mandatory for processing this request is not supplied.|400|您需要指定DeploymentSetId值。|
|DependencyViolation.NotEmpty|There are still instance\(s\) in the specified DeploymentSetId.|403|指定的部署集中不能有实例。|
|InvalidRegionId.NotFound|The RegionId provided does not exist in our records.|404|指定的地域不存在。|

