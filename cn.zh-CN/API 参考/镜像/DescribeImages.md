# DescribeImages {#DescribeImages .reference}

查询您可以使用的镜像资源。

## 描述 {#section_jgn_1fz_xdb .section}

调用该接口时，您需要注意：

-   您可以查询的镜像资源包括您的自定义镜像、阿里云提供的公共镜像、云市场的镜像以及其他阿里云用户主动共享给您的共享镜像。

-   该接口支持分页查询，查询结果包括可使用的镜像资源的总数和当前页的镜像资源。每页的数量默认为 10 条。


## 请求参数 {#RequestParameter .section}

|名称|类型|是否必需|描述|
|:-|:-|:---|:-|
|Action|String|是|系统规定参数。取值：DescribeImages|
|RegionId|String|是|实例所属的地域 ID。您可以调用 [DescribeRegions](intl.zh-CN/API参考/地域/DescribeRegions.md#) 查看最新的阿里云地域列表。|
|ImageId|String|否|镜像 ID。单次最多查询 100 条 ID，ID 之间用半角逗号字符 `,`隔开。|
|Status|String|否|查询某种状态下的镜像。取值范围：-   Creating：镜像正在创建中。
-   Available：您可以使用的镜像。
-   UnAvailable：您不能使用的镜像。
-   CreateFailed：创建失败的镜像。

默认值：Available支持同时取多个值，值之间以半角逗号 `,` 隔开。|
|SnapshotId|String|否|根据某一快照 ID 创建的自定义镜像。|
|ImageName|String|否|镜像名称。|
|ImageOwnerAlias|string|否|镜像来源。取值范围：-   system：阿里云提供的公共镜像。
-   self：您创建的自定义镜像。
-   others：其他阿里云用户共享给您的镜像。
-   marketplace：[镜像市场](https://market.aliyun.com/)[云市场](https://marketplace.alibabacloud.com/) 提供的镜像。 您查询到的云市场镜像可以直接使用，无需提前订阅。您需要自行留意云市场镜像的收费详情。

默认值：空，空表示返回取值为 `system`、`self` 以及 `others` 的结果。|
|Usage|String|否|镜像是否已经运行在 ECS 实例中。取值范围：-   instance：镜像处于运行状态，有 ECS 实例使用。
-   none：镜像处于闲置状态，暂无 ECS 实例使用。

|
|Tag.n.Key|String|否|标签键。`n` 的取值范围：\[1, 5\]若您根据标签查询镜像资源，标签键不允许为空字符串。|
|Tag.n.Value|String|否|标签值。`n` 的取值范围：\[1, 5\]若您根据标签查询镜像资源，标签值允许为空字符串。|
|PageNumber|Integer|否|镜像资源列表的页码。起始值：1默认值：1

|
|PageSize|Integer|否|分页查询时设置的每页行数。最大值：50默认值：10

|

## 返回参数 {#ResponseParameter .section}

|名称|类型|描述|
|:-|:-|:-|
|RegionId|String|镜像所属地域 ID|
|TotalCount|Integer|镜像资源总数|
|PageNumber|Integer|当前页码|
|PageSize|Integer|当前分页包含多少条目|
|Images|Array|镜像信息 [ImageType](intl.zh-CN/API参考/数据类型/ImageType.md#) 组成的集合。|

## 示例 { .section}

**请求示例** 

```
https://ecs.aliyuncs.com/?Action=DescribeImages
&RegionId=cn-hangzhou
&<公共请求参数>
```

**返回示例** 

**XML 格式**

```
<DescribeImagesResponse>
    <Images>
        <Image>
            <Architecture>i386</Architecture>
            <CreationTime>2014-07-22T09:53:44Z</CreationTime>
            <Description></Description>
            <DiskDeviceMappings>
                <DiskDeviceMapping>
                    <Device>/dev/xvda</Device>
                    <Size>20</Size>
                    <SnapshotId></SnapshotId>
                </DiskDeviceMapping>
            </DiskDeviceMappings>
            <ImageId>suse11sp3_64_20G_aliaegis_20150428.vhd</ImageId>            
            <ImageName>suse11sp3_64_20G_aliaegis_20150428.vhd</ImageName>
            <ImageOwnerAlias>system</ImageOwnerAlias>
            <ImageVersion>1.0</ImageVersion>
            <IsCopied>false</IsCopied>
            <IsSubscribed>false</IsSubscribed>
            <OSName>SUSE Linux  Enterprise Server 11 SP3 64位</OSName>
            <ProductCode></ProductCode>
            <OSType>linux</OSType>
            <Platform>SUSE</Platform>
            <Progress>100</Progress>
            <Size>20</Size>
            <Status>Available</Status>
            <Usage>instance</Usage>
        </Image>
    </Images>
    <PageNumber>1</PageNumber>
    <PageSize>2</PageSize>
    <RegionId>cn-hangzhou</RegionId>
    <TotalCount>24</TotalCount>
    <RequestId>7871BB26-3002-4950-B2E6-98D333077EA5</RequestId>
</DescribeImagesResponse>
```

 **JSON 格式** 

```
{
  "Images": {
    "Image": [
      {
        "Architecture": "x86_64",
        "CreationTime": "2015-05-06T09:01:32Z",
        "DiskDeviceMappings": {
          "DiskDeviceMapping": [
            {
              "Device": "/dev/xvda",
              "Size": "20"
            }
          ]
        },
        "ImageId": "suse11sp3_64_20G_aliaegis_20150428.vhd",
        "ImageName": "suse11sp3_64_20G_aliaegis_20150428.vhd",
        "ImageOwnerAlias": "system",
        "ImageVersion": "1",
        "IsCopied": false,
        "IsSubscribed": false,
        "OSName": "SUSE Linux  Enterprise Server 11 SP3 64位",
        "OSType": "linux",
        "Platform": "SUSE",
        "Progress": "100%",
        "Size": 20,
        "Status": "Available",
        "Usage": "instance"
      }
    ]
  }
  "PageNumber": 1,
  "PageSize": 1,
  "RegionId": "cn-hangzhou",
  "RequestId": "49CBCED4-C9B9-4851-BEB5-8FB5E5169E30",
  "TotalCount": 24
}
```

## 错误码 {#ErrorCode .section}

以下为本接口特有的错误码。更多错误码，请访问 [API 错误中心](https://error-center.alibabacloud.com/status/product/Ecs)。

|错误代码|错误信息|HTTP 状态码|说明|
|:---|:---|:-------|:-|
|InvalidImageOwnerAlias.ValueNotSupported|The specified ImageOwnerAlias value is not supported.|400|参数 `ImageOwnerAlias`取值不合法。|
|InvalidTag.Mismatch|The specified Tag.n.Key and Tag.n.Value are not match.|400|指定的 `Tag.n.Key`和 `Tag.n.Value` 必须键值匹配。|
|InvalidTagCount|The specified tags are beyond the permitted range.|400|指定的标签数不能超过五个。|
|InvalidUsage|The specifed Usage is not valid|404|指定的 `Usage` 不合法。|

