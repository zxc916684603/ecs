# CreateLaunchTemplateVersion {#CreateLaunchTemplateVersion .reference}

根据指定的实例启动模板创建一个版本。

## 描述 {#section_hhw_wvn_12b .section}

每个实例启动模板最多创建 30 个版本。我们不提供模板修改接口，但是提供版本迭代接口（CreateLaunchTemplateVersion），使您想修改某个版本的参数时，能通过新建模板版本的方式修改。更多详情，请参阅 CreateLaunchTemplate。

## 请求参数 {#RequestParameter .section}

|名称|类型|是否必需|描述|
|:-|:-|:---|:-|
|Action|String|是|系统规定参数。取值：CreateLaunchTemplateVersion|
|RegionId|String|是|实例所属的地域 ID。您可以调用 [DescribeRegions](intl.zh-CN/API参考/地域/DescribeRegions.md#) 查看最新的阿里云地域列表。|
|LaunchTemplateId|String|是|实例启动模板 ID。更多详情，请调用 [DescribeLaunchTemplates](intl.zh-CN/API参考/启动模板/DescribeLaunchTemplates.md#)。您必须指定 `LaunchTemplateId` 或 `LaunchTemplateName` 以确定模板。|
|LaunchTemplateName|String|是|实例启动模板名称。|
|VersionDescription|String|否|实例启动模板版本的描述。长度为 \[2, 256\] 个字符。不能以 http:// 和 https:// 开头。默认值为空。|
|ImageId|String|否|镜像 ID。|
|InstanceType|String|否|实例类型。更多详情，请调用 [DescribeInstanceTypes](intl.zh-CN/API参考/实例/DescribeInstanceTypes.md#)接口获得最新的规格表。|
|SecurityGroupId|String|否|安全组 ID。|
|NetworkType|String|否|实例网络类型。取值范围：classic | vpc|
|VSwitchId|String|否|创建 VPC 类型实例时需要指定虚拟交换机 ID。|
|InstanceName|String|否|实例名称。长度为\[2, 128\]个英文或中文字符，必须以大小字母或中文开头，可以包含数字、半角冒号（:）、点号（.）、下划线（\_）或短横线（-）。不能以 http:// 和 https:// 开头。|
|Description|String|否|实例描述。|
|InternetMaxBandwidthIn|String|否|公网入带宽最大值，单位为 Mbit/s。取值范围：\[1,200\]|
|InternetMaxBandwidthOut|String|否|公网出带宽最大值，单位为 Mbit/s。取值范围：\[0, 100\]|
|HostName|String|否|实例主机名。-   点号（.）和短横线（-）不能作为 HostName 的首尾字符，不能连续使用。
-   Windows 实例：字符长度为\[2, 15\]，支持字母、数字和短横线（-），不支持点号（.），不能全是数字。
-   其他类型（Linux 等）实例：字符长度为 \[2, 128\]，支持多个点号，点之间为一段，每段允许字母、数字和短横线（-）组成。

|
|ZoneId|String|否|实例所属的可用区 ID。|
|SystemDisk.Category|String|否|系统盘的磁盘种类。取值范围：-   cloud：普通云盘
-   cloud\_efficiency：高效云盘
-   cloud\_ssd：SSD 云盘
-   ephemeral\_ssd：本地 SSD 盘

|
|SystemDisk.Size|Integer|否|系统盘大小，单位为 GB。取值范围：\[20, 500\]|
|SystemDisk.DiskName|String|否|系统盘名称。长度为 \[2, 128\] 个英文或中文字符，必须以大小字母或中文开头，可以包含数字、半角冒号（:）、点号（.）、下划线（\_）或短横线（-）。不能以 http:// 和 https:// 开头。|
|SystemDisk.Description|String|否|系统盘描述。长度为 \[2, 256\] 个字符。不能以 http:// 和 https:// 开头。|
|DataDisk.n.Category|String|否|数据盘的磁盘种类，`n` 的取值范围为 \[1, 16\]。取值范围：-   cloud：普通云盘
-   cloud\_efficiency：高效云盘
-   cloud\_ssd：SSD 云盘
-   ephemeral\_ssd：本地 SSD 盘

|
|DataDisk.n.Size|Integer|否|数据盘的容量大小，`n` 的取值范围为 \[1, 16\]。取值范围：-   cloud：\[5, 2000\]
-   cloud\_efficiency：\[20, 32768\]
-   cloud\_ssd：\[20, 32768\]
-   ephemeral\_ssd：\[5, 800\]

|
|DataDisk.n.SnapshotId|String|否|创建数据盘使用的快照，`n` 的取值范围为 \[1, 16\]。|
|DataDisk.n.Encrypted|Boolean|否|是否加密数据盘，`n` 的取值范围为 \[1, 16\]。|
|DataDisk.n.DiskName|String|否|数据盘名称，`n` 的取值范围为 \[1, 16\]。|
|DataDisk.n.Description|String|否|数据盘描述，`n` 的取值范围为 \[1, 16\]。|
|DataDisk.n.DeleteWithInstance|String|否|数据盘是否随实例释放而释放，`n` 的取值范围为 \[1, 16\]。|
|IoOptimized|String|否|是否为 I/O 优化实例。取值范围：-   none：非 I/O 优化
-   optimized：I/O 优化

|
|NetworkInterface.n.PrimaryIpAddress|String|否|第 `n` 个弹性网卡的主私有 IP 地址。`n` 的取值范围参阅实例规格族。|
|NetworkInterface.n.VSwitchId|String|否|第 `n` 个弹性网卡所属的虚拟交换机 ID。实例与弹性网卡必须在同一VPC的同一可用区中，可以分属于不同交换机。`n` 的取值范围参阅实例规格族。|
|NetworkInterface.n.SecurityGroupId|String|否|第 `n` 个所属的安全组 ID 必须是同一个 VPC 下的安全组。`n` 的取值范围参阅实例规格族。|
|NetworkInterface.n.NetworkInterfaceName|String|否|第 `n` 个弹性网卡名称。`n` 的取值范围参阅实例规格族。|
|NetworkInterface.n.Description|String|否|第 `n` 个弹性网卡描述信息。`n` 的取值范围参阅实例规格族。|
|InternetChargeType|String|否|公网带宽计费类型。取值范围：PayByTraffic|
|UserData|String|否|实例自定义数据，需要以 Base64 方式编码，原始数据最多为 16 KB。|
|KeyPairName|String|否|密钥对名称。-   Windows 实例，忽略该参数。默认为空。即使填写了该参数，仍旧只执行 `Password` 的内容。
-   Linux 实例的密码登录方式会被初始化成禁止。

|
|RamRoleName|String|否|实例 RAM 角色名称。您可以使用 *RAM* API [ListRoles](../../../../intl.zh-CN/API参考/API 参考（RAM）/角色管理接口/ListRoles.md#) 查询实例RAM角色名称。|
|AutoReleaseTime|String|否|实例自动释放时间。按照 [ISO8601](intl.zh-CN/API参考/附录/时间格式.md#) 标准表示，并需要使用 UTC 时间。格式为 YYYY-MM-DDTHH:mm:ssZ。|
|SpotStrategy|String|否|后付费实例的抢占策略。当参数 `InstanceChargeType` 取值为 `PostPaid` 时为生效。取值范围：-   NoSpot：正常按量付费实例
-   SpotWithPriceLimit：设置上限价格的抢占式实例
-   SpotAsPriceGo：系统自动出价，最高按量付费价格。

|
|SpotPriceLimit|Float|否|设置实例的每小时最高价格。支持最大 3 位小数。|
|SecurityEnhancementStrategy|String|否|是否开启安全加固。取值范围：Active | Deactive|
|Tag.n.Key|String|否|实例的标签键。`n` 的取值范围：\[1, 5\]。 最多支持 64 个字符。不能以 aliyun、acs:、http:// 或者 https:// 开头。|
|Tag.n.Value|Float|否|实例的标签值。`n` 的取值范围：\[1, 5\]。最多支持 128 个字符。不能以 aliyun、http:// 或者 https:// 开头。|

## 返回参数 {#ResponseParameter .section}

|名称|类型|描述|
|:-|:-|:-|
|LaunchTemplateVersionNumber|Long|实例启动模板版本号|

## 示例 { .section}

**请求示例** 

```
https://ecs.aliyuncs.com/?Action=CreateLaunchTemplateVersion
&RegionId=cn-hangzhou
&LaunchTemplateName=lt-name1
&InstanceType=ecs.cm4.6xlarge
&SecurityGroupId=sg-securitygroupid
&<公共请求参数>
```

**返回示例** 

**XML 格式**

```
<CreateLaunchTemplateVersionResponse>
    <RequestId>04F0F334-1335-436C-A1D7-6C044FExxxxx</RequestId>
    <LaunchTemplateVersionNumber>2</LaunchTemplateVersionNumber>
</CreateLaunchTemplateVersionResponse>
```

 **JSON 格式** 

```
{
    "RequestId": "04F0F334-1335-436C-A1D7-6C044FExxxxx",
    "LaunchTemplateVersionNumber": 2
}
```

## 错误码 {#ErrorCode .section}

以下为本接口特有的错误码。更多错误码，请访问 [API 错误中心](https://error-center.alibabacloud.com/status/product/Ecs)。

|错误代码|错误信息|HTTP 状态码|说明|
|:---|:---|:-------|:-|
|InvalidLaunchTemplate.NotFound|The specified LaunchTemplateId “\{0\}” LaunchTemplateName “\{1\}” is not found.|400|指定的 `LaunchTemplateId` 或 `LaunchTemplateName`不存在。|
|MissingParameter|The input parameter “\{0\}” that is mandatory for processing this request is not supplied.|400|缺失必需参数。|
|InvalidParameter|the parameter\(s\) “\{0\}” provided is\(are\) invalid.|400|指定的参数不合法。|
|InvalidDescription.Malformed|The specified parameter “VersionDescription” is not valid.|400|指定的 `VersionDescription`不合法。|
|InvalidUserData.SizeExceeded|The specified parameter UserData exceeds the size.|400|`UserData` 原始数据最多为 16 KB。|
|InvalidUserData.Base64FormatInvalid|The specified parameter UserData must be base64 encoded.|400|`UserData` 必须经过 Base64 编码。|
|LaunchTemplateVersionLimitExceed|The maximum number of template’s versions is exceeded.|403|一个实例启动模板最多能创建 30 个版本。|
|InnerServiceFailed|call inner service failed|403|服务器内部错误。|

