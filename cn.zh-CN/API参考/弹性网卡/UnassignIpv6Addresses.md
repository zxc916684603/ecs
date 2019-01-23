# UnassignIpv6Addresses {#reference_npc_4hp_yfb .reference}

若弹性网卡已被分配了 IPv6 地址，UnassignIpv6Addresses 可以回收一个或多个 IPv6 地址。

## 描述 {#section_nsk_rhp_yfb .section}

**说明：** ECS 支持 IPv6 地址目前处于公测阶段，您可以提交 [公测申请](https://page.aliyun.com/form/act608662110/index.htm)。

调用该接口时，您需要注意：

-   弹性网卡必须处于 **可用**（`Available`） 或 **已挂载**（`InUse`） 状态。
-   主网卡关联的 ECS 实例必须处于 **运行中**（`Running`）或 **已停止**（`Stopped`） 状态。

## 请求参数 {#section_pqw_zhp_yfb .section}

|名称|类型|是否必需|描述|
|:-|:-|:---|:-|
|Action|String|是|系统规定参数。取值：UnassignIpv6Addresses。|
|RegionId|String|是|弹性网卡所在地域的 ID。您可以调用[DescribeRegions](../cn.zh-CN/API参考/地域/DescribeRegions.md#)查看最新的阿里云地域列表。 |
|NetworkInterfaceId|String|是|弹性网卡 ID。|
|Ipv6Address.N|String|否|一个或多个 IPv6 地址。取值示例: `Ipv6Address.1=2001:db8:1234:1a00::4XX`。|

## 返回参数 {#section_ecw_clp_yfb .section}

全是公共返回参数。参见 [公共返回参数](cn.zh-CN/API参考/HTTP调用方式/公共参数.md#)。

## 示例 {#section_yjy_zfq_yfb .section}

**请求示例**

```
https://ecs.aliyuncs.com/?Action=UnassignIpv6Addresses
&NetworkInterfaceId=eni-test
&<公共请求参数>
```

**返回示例**

XML 格式

```
<UnassignIpv6AddressesResponse>
    <RequestId>48285314-3192-47FE-B4C8-9D51E7Fxxxxx</RequestId>
</UnassignIpv6AddressesResponse>
```

JSON 格式

```
{
    "RequestId": "48285314-3192-47FE-B4C8-9D51E7Fxxxxx"
}
```

## 错误码 {#section_mgq_2lp_yfb .section}

以下为本接口特有的错误码。更多错误码，请访问[API错误中心](https://error-center.aliyun.com/status/product/Ecs)。

**说明：** 错误信息里的花括号（`{}`）按实际情况动态返回取值。

|错误代码|错误信息|HTTP状态码|说明|
|:---|:---|:------|:-|
|InvalidOperation.InvalidEcsState|The operation is not allowed in the current ECS state. Expecting status is "\{0\}" while current status is "\{1\}".|400|ECS 实例当前状态不支持分配 IPv6 地址。|
|InvalidOperation.InvalidEniState|The operation is not allowed in the current ENI state. Expecting status is "\{0\}" while current status is "\{1\}".|400|弹性网卡当前状态不支持分配 IPv6 地址。|
|MissingParameter|The input parameter "\{0\}" that is mandatory for processing this request is not supplied.|400|缺少必需参数。|
|InvalidIp.IpRepeated|The specified ipAddress "\{0\}" is\(are\) repeated.|403|指定的 IP 已存在。|
|InvalidEniId.NotFound|The specified EniId "\{0\}" is not found.|404|指定的弹性网卡 ID 不存在。|

