# AssignIpv6Addresses {#reference_ywv_mbp_yfb .reference}

使用 AssignIpv6Addresses 为弹性网卡分配一个或多个 IPv6 地址。

## 描述 {#section_vbz_dcp_yfb .section}

**说明：** ECS 支持 IPv6 地址目前处于公测阶段，您可以提交 [公测申请](https://page.aliyun.com/form/act608662110/index.htm)。

您可以指定弹性网卡所属交换机下 CIDR 的 IPv6 地址，也可以指定IPv6地址数量自动创建 IPv6 地址。

-   弹性网卡必须处于 **可用**（`Available`） 或 **已挂载**（`InUse`） 状态。
-   主网卡关联的 ECS 实例必须处于 **运行中**（`Running`）或 **已停止**（`Stopped`） 状态。
-   单个网卡能够分配的 IPv6 地址数量和网卡附加的实例规格有关。
    -   如果弹性网卡处于 **Available** 状态，最多可以分配 10 个 IPv6 地址。
    -   如果弹性网卡挂载到实例上，能够分配的 IPv6 地址数将受到实例规格限制。更多详情，请参阅 [实例规格族](../cn.zh-CN/产品简介/实例规格族.md#)。

## 请求参数 {#section_l3z_12p_yfb .section}

|名称|类型|是否必需|描述|
|:-|:-|:---|:-|
|Action|String|是|系统规定参数。取值：AssignIpv6Addresses|
|RegionId|String|是|弹性网卡所在地域的 ID。您可以调用[DescribeRegions](../cn.zh-CN/API参考/地域/DescribeRegions.md#)查看最新的阿里云地域列表。 |
|NetworkInterfaceId|String|是|弹性网卡 ID。|
|Ipv6Address.N|String|否|为弹性网卡指定一个或多个 IPv6 地址。目前，N 的取值范围仅支持 1。取值示例：`Ipv6Address.1=2001:db8:1234:1a00::XXX`

**说明：** 您不能同时指定参数 Ipv6Addresses.N 和 Ipv6AddressCount。

|
|Ipv6AddressCount|Integer|否|为弹性网卡指定随机生成的 IPv6 地址数量。**说明：** 您不能同时指定参数 Ipv6Addresses.N 和 Ipv6AddressCount。

|

## 返回参数 {#section_ec3_kfp_yfb .section}

全是公共返回参数。参见 [公共返回参数](cn.zh-CN/API参考/HTTP调用方式/公共参数.md#)。

## 示例 {#section_uxt_x2q_yfb .section}

**请求示例**

```
https://ecs.aliyuncs.com/?Action=AssignIpv6Addresses 
&NetworkInterfaceId=eni-test
&<公共请求参数>
```

**返回示例**

XML 格式

```
<AssignIpv6AddressesResponse>
    <RequestId>A94E0C9F-B39E-4A87-BFFC-6DC7840xxxxx</RequestId>
</AssignIpv6AddressesResponse>
```

JSON 格式

```
{
    "RequestId": "A94E0C9F-B39E-4A87-BFFC-6DC7840xxxxx"
}
```

## 错误码 {#section_y4m_lfp_yfb .section}

以下为本接口特有的错误码。更多错误码，请访问[API错误中心](https://error-center.aliyun.com/status/product/Ecs)。

**说明：** 错误信息里的花括号（`{}`）按实际情况动态返回取值。

|错误代码|错误信息|HTTP 状态码|说明|
|:---|:---|:-------|:-|
|InvalidOperation.InvalidEcsState|The operation is not allowed in the current ECS state. Expecting status is "\{0\}" while current status is "\{1\}".|400|ECS 实例当前状态不支持分配 IPv6 地址。|
|InvalidOperation.InvalidEniState|The operation is not allowed in the current ENI state. Expecting status is "\{0\}" while current status is "\{1\}".|400|弹性网卡当前状态不支持分配 IPv6 地址。|
|MissingParameter|The input parameter "\{0\}" that is mandatory for processing this request is not supplied.|400|缺少必填参数。|
|InvalidOperation.InvalidEniType|The operation is not allowed in the current ENI type. Expecting type is "\{0\}" while current type is "\{1\}".|403|当前网卡类型不支持此操作。|
|InvalidIp.IpRepeated|The specified ipAddress "\{0\}" is\(are\) repeated.|403|指定的IP重复。|
|InvalidIp.Address|The specified ipAddress "\{0\}" is invalid.|403|指定的IPv6地址不合法。|
|InvalidOperation.Ipv6CountExceeded|The number of eni \{0\} ipv6 address exceeds the limit\(\{1\}\). target instanceType \{2\}. Assigned:\{3\}. Expecting assign:\{4\}.|403|IPv6 个数达到上限。|
|InvalidOperation.Ipv6NotSupport|The instanceType of \{0\} not support ipv6.|403|实例规格不支持 IPv6。|
|InvalidVSwitch.Ipv6NotTurnOn|The specified VSwitch "\{0\}" ipv6 function not turn on.|403|交换机没有打开 IPv6 功能。|
|InvalidEniId.NotFound|The specified EniId "\{0\}" is not found.|404|指定的弹性网卡 ID 不存在。|

