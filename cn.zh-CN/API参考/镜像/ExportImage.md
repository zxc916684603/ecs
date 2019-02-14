# ExportImage {#doc_api_1003489 .reference}

导出您的自定义镜像到与该自定义镜像同一地域的 OSS Bucket 里。

## 描述 {#description .section}

您需要 [提交工单](https://selfservice.console.aliyun.com/ticket/createIndex.htm)联系阿里云，为您开启导出镜像功能。

-   不支持导出使用市场镜像的系统盘快照创建的自定义镜像。
-   支持导出镜像中包括数据盘快照的信息的自定义镜像，其中数据盘数不能超过 4 块，单块数据盘容量最大不能超过 500 GB。
-   需要通过 RAM 授权云服务器 ECS 官方服务账号写入 OSS 的权限：

    1. 创建角色：`AliyunECSImageExportDefaultRole`（其他任何角色名称无效），为该角色设置以下角色策略：

    ```
    
             {
               "Statement": [
                 {
                   "Action": "sts:AssumeRole",
                   "Effect": "Allow",
                   "Principal": {
                     "Service": [
                       "ecs.aliyuncs.com"
                     ]
                   }
                 }
               ],
               "Version": "1"
             }
            
    ```

    2. 在角色 `AliyunECSImageExportDefaultRole` 下加入默认的系统权限策略：`AliyunECSImageExportRolePolicy`，该策略是云服务器 ECS 提供导出镜像的默认策略。用户也可以创建自定义策略，权限需要包含：

    ```
    
             {
               "Version": "1",
               "Statement": [
                 {
                   "Action": [
                     "oss:GetObject",
                     "oss:PutObject",
                     "oss:DeleteObject",
                     "oss:GetBucketLocation",
                     "oss:AbortMultipartUpload",
                     "oss:ListMultipartUploads",
                     "oss:ListParts"
                   ],
                   "Resource": "*",
                   "Effect": "Allow"
                 }
               ]
             }
            
    ```


## 调试 {#apiExplorer .section}

前往【[API Explorer](https://api.aliyun.com/#product=Ecs&api=ExportImage)】在线调试，API Explorer 提供在线调用 API、动态生成 SDK Example 代码和快速检索接口等能力，能显著降低使用云 API 的难度，强烈推荐使用。

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|ImageId|String|是|m-imageid1|自定义镜像 ID。

 |
|OSSBucket|String|是|testexportImage|保存导出镜像的 OSS bucket。

 |
|RegionId|String|是|cn-hangzhou|自定义镜像的地域 ID。您可以调用 [DescribeRegions](~~25609~~) 查看最新的阿里云地域列表。

 |
|Action|String|否|ExportImage|系统规定参数。取值：ExportImage

 |
|ImageFormat|String|否|raw|导出镜像时指定的镜像格式。

 **说明：** 该参数即将下线，为保持兼容性，请您尽量使用其他参数。

 |
|OSSPrefix|String|否|EcsExport|您的 OSS Object 的前缀。可以由数字或者字母组成，字符长度为 1~30。

 |
|RoleName|String|否|FinanceJoshua|导出镜像时的角色名称。

 **说明：** 该参数即将下线，为保持兼容性，请您尽量使用其他参数。

 |

## 返回参数 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|RegionId|String|cn-hangzhou|地域 ID

 |
|RequestId|String|473469C7-AA6F-4DC5-B3DB-A3DC0DE3C83E|请求 ID

 |
|TaskId|String|tsk-231234567|导出镜像任务 ID

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ecs.aliyuncs.com/?Action=ExportImage
&ImageId=m-imageid1
&OSSBucket=testexportImage
&RegionId=cn-hangzhou
&OSSPrefix=EcsExport
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<ExportImageResponse>
  <RequestId>C8B26B44-0189-443E-9816-D951F59623A9</RequestId>
  <ExportTaskId>tsk-231234567</ExportTaskId>
  <RegionId>cn-hangzhou</RegionId>
</ExportImageResponse>

```

`JSON` 格式

``` {#json_return_success_demo}
{
	"RegionId":"cn-hangzhou",
	"RequestId":"C8B26B44-0189-443E-9816-D951F59623A9",
	"ExportTaskId":"tsk-231234567"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|MissingParameter|An input parameter "RegionId" that is mandatory for processing the request is not supplied.|参数 RegionId 不得为空。|
|400|MissingParameter|An input parameter "ImageId" that is mandatory for processing the request is not supplied.|参数 ImageId 不得为空。|
|400|MissingParameter|An input parameter "OSSBucket" that is mandatory for processing the request is not supplied.|参数 OSSBucket 不得为空。|
|400|InvalidRegionId.NotFound|The specified RegionId does not exist.|指定的 RegionId 不存在，请您检查此产品在该地域是否可用。|
|400|InvalidRegion.NotSupport|The specified region does not support image import or export.|指定的地域暂时不支持此操作。|
|404|InvalidImageId.NotFound|The specified ImageId does not exist.|指定的镜像在该用户账号下不存在，请您检查镜像id是否正确。|
|400|IncorrectImageStatus|The specified Image is not available.|指定的源镜像状态不正确。|
|403|ImageNotSupported|The specified image from the image market, do not support export image.|不支持导出镜像市场里的镜像。|
|400|InvalidImageFormat.Malformed|The specified Image Format is wrongly formed.|参数 AssociateInstanceType 格式错误。|
|403|ExportImageFailed|Exporting image is failed, Please contact the administrator.|导出镜像失败，请联系系统管理员。|
|400|InvalidOSSBucket.NotFound|The specified OSS bucket does not exist in this region.|指定的bucket不存在。|
|400|OperationDenied|The specified image contains the snapshot of the data disk,does not support this operation.|指定的镜像包含了数据盘快照的映射，不支持导出。|
|400|InvalidImage.DiskAmountOrSize|The diskSize or diskAmount of the image exceeds the limitation.|磁盘大小和磁盘数量不能超过导出镜像的使用限制。|
|400|ImageNotSupported|The specified Image contains encrypted snapshots, do not support export.|指定的镜像包含了加密快照，不支持导出。|
|400|ImageNotSupported|Image from image market does not support exporting.|不支持导出镜像市场里的镜像。|
|403|ConcurrentQuotaExceed.ExportImage|%s|当前在处理中的任务数已超过配额，请耐心等待前面任务完成。|
|403|WeeklyQuotaExceed.ExportImage|%s|本周提交任务已经超出配额，请耐心等候再次分配可用额度。|

[查看本产品错误码](https://error-center.aliyun.com/status/product/Ecs)

