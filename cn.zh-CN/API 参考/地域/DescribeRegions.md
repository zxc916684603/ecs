# DescribeRegions {#DescribeRegions .reference}

查询您可以使用的阿里云地域。更多详情，请参阅 [地域与可用区](https://www.alibabacloud.com/help/doc-detail/40654.htm)。

## 请求参数 {#RequestParameter .section}

|名称|类型|是否必需|描述|
|:-|:-|:---|:-|
|Action|String|是|系统规定参数。取值：DescribeRegions|

## 返回参数 {#ResponseParameter .section}

|名称|类型|描述|
|:-|:-|:-|
|Regions|[RegionType](intl.zh-CN/API 参考/数据类型/RegionType.md#)|地域信息集合|

## 示例 { .section}

**请求示例** 

```
https://ecs.aliyuncs.com/?Action=DescribeRegions
&<公共请求参数>
```

**返回示例** 

**XML 格式**

```
<DescribeRegionsResponse>
    <RequestId>611CB80C-B6A9-43DB-9E38-0B0AC3D9B58F</RequestId>
    <Regions>
        <Region>
            <RegionId>cn-hangzhou </RegionId>
        </Region>
        <Region>
            <RegionId>cn-qingdao</RegionId>
        </Region>
    </Regions>
</DescribeRegionsResponse>
```

 **JSON 格式** 

```
{
    "RequestId": "611CB80C-B6A9-43DB-9E38-0B0AC3D9B58F",
    "Regions": {
        "Region": [{
            "RegionId": "cn-hangzhou "
        },
        {
            "RegionId": "cn-qingdao"
        }]
    }
}
```

## 错误码 {#ErrorCode .section}

全是公共错误码。更多错误码，请访问 [API 错误中心](https://error-center.alibabacloud.com/status/product/Ecs)。

