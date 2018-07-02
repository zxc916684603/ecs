# DescribeNetworkInterfaces {#DescribeNetworkInterfaces .reference}

查看弹性网卡（ENI）列表。

## 描述 {#section_l24_yj4_ydb .section}

-   查询时，我们通过您指定属性值过滤结果。
-   不指定属性值就不过滤该属性，返回所有类目结果。
-   一次最多查看 100 个弹性网卡。

## 请求参数 {#RequestParameter .section}

|名称|类型|是否必需|描述|
|:-|:-|:---|:-|
|Action|String|是|系统规定参数。取值：DescribeNetworkInterfaces|
|RegionId|String|是|所在地域 ID。您可以调用 [DescribeRegions](intl.zh-CN/API 参考/地域/DescribeRegions.md#) 查看最新的阿里云地域列表。|
|VpcId|String|否|查询您的一个 VPC 里所有辅助网卡。|
|VSwitchId|String|否|VPC 的虚拟交换机 ID。|
|PrimaryIpAddress|String|否|弹性网卡主私有 IP 地址。|
|SecurityGroupId|String|否|安全组 ID。|
|NetworkInterfaceName|String|否|弹性网卡的名称。|
|Type|String|否|弹性网卡类型。取值范围：-   Primary
-   Secondary

|
|InstanceId|String|否|弹性网卡当前关联的实例 ID。|
|NetworkInterfaceId.N|String|否|弹性网卡 ID。一次最多查看 100 个。|
|PageNumber|Integer|否|查询结果的页码。取值为正整数。默认值：1

|
|PageSize|Integer|否|查询结果的分页大小。取值范围：\[1,100\]默认值：10

|

## 返回参数 {#ResponseParameter .section}

|名称|类型|描述|
|:-|:-|:-|
|NetworkInterfaceSet|[NetworkInterfaceSet](intl.zh-CN/API 参考/数据类型/NetworkInterfaceSet.md#)|弹性网卡信息组成的集合|
|TotalCount|Integer|实例总个数|
|PageNumber|Integer|实例列表的页码|
|PageSize|Integer|输入时设置的每页行数|

## 示例 { .section}

**请求示例** 

```
https://ecs.aliyuncs.com/?Action=DescribeNetworkInterfaces
&RegionId=cn-hangzhou
&<公共请求参数>
```

**返回示例** 

**XML 格式**

```
<DescribeNetworkInterfacesResponse>
    <NetworkInterfaceSets>
        <NetworkInterfaceSet>
            <AssociatedPublicIp />
            <CreationTime>2017-11-24T06:14:22Z</CreationTime>
            <InstanceId>AY121018033933eaxxxxx</InstanceId>
            <MacAddress>00:16:3e:0f:XX:XX</MacAddress>
            <NetworkInterfaceId>eni-bp17pdijfczaxZZZZxxxxx</NetworkInterfaceId>
            <PrivateIpAddress>XXX.XXX.XX.XX</PrivateIpAddress>
            <PrivateIpSets>
                <PrivateIpSet>
                    <AssociatedPublicIp />
                    <Primary>true</Primary>
                    <PrivateIpAddress>XXX.XXX.XX.XX</PrivateIpAddress>
                </PrivateIpSet>
            </PrivateIpSets>
            <SecurityGroupIds>
                <SecurityGroupId>sg-bp144yr32sx6ndwxxxxx</SecurityGroupId>
            </SecurityGroupIds>
            <Status>Available</Status>
            <Type>Secondary</Type>
            <VpcId>vpc-bp1j7w3gc1cexjqdxxxxx</VpcId>
            <VSwitchId>vsw-bp16usj2p27htro3xxxxx</VSwitchId>
            <ZoneId>cn-hangzhou-e</ZoneId>
        </NetworkInterfaceSet>
    </NetworkInterfaceSets>
    <PageNumber>1</PageNumber>
    <PageSize>100</PageSize>
    <RequestId>CEE5C347-0B64-4535-A061-95BE95Axxxxx</RequestId>
    <TotalCount>1</TotalCount>
</DescribeNetworkInterfacesResponse>
```

 **JSON 格式** 

```
{
    "NetworkInterfaceSets": {
        "NetworkInterfaceSet": [
            {
                "AssociatedPublicIp": {
                },
                "CreationTime": "2017-11-24T06:14:22Z",
                "InstanceId": "AY121018033933eaxxxxx",
                "MacAddress": "00:16:3e:0f:XX:XX",
                "NetworkInterfaceId": "eni-bp17pdijfczaxZZZZxxxxx",
                "PrivateIpAddress": "XXX.XXX.XX.XX",
                "PrivateIpSets": {
                    "PrivateIpSet": [
                        {
                            "AssociatedPublicIp": {
                            },
                            "Primary": true,
                            "PrivateIpAddress": "XXX.XXX.XX.XX"
                        }
                    ]
                },
                "SecurityGroupIds": {
                    "SecurityGroupId": [
                        "sg-bp144yr32sx6ndwxxxxx"
                    ]
                },
                "Status": "Available",
                "Type": "Secondary",
                "VpcId": "vpc-bp1j7w3gc1cexjqdxxxxx",
                "VSwitchId": "vsw-bp16usj2p27htro3xxxxx",
                "ZoneId": "cn-hangzhou-e"
            }
        ]
    },
    "PageNumber": 1,
    "PageSize": 100,
    "RequestId": "CEE5C347-0B64-4535-A061-95BE95Axxxxx",
    "TotalCount": 1
}
```

## 错误码 {#ErrorCode .section}

以下为本接口特有的错误码。更多错误码，请访问 [API 错误中心](https://error-center.alibabacloud.com/status/product/Ecs)。

|错误代码|错误信息|HTTP 状态码|说明|
|:---|:---|:-------|:-|
|Abs.InvalidAccount.NotFound|The Account is not found or ak is expired.|403|您的阿里云账号不存在，或者您的 AccessKey 已经过期。|
|UnsupportedParameter|The parameters is unsupported.|400|该参数不存在，或者不支持该参数。|
|MissingParameter|The input parameter that is mandatory for processing this request is not supplied.|400|缺少必需参数。|
|InvalidEcsId.NotFound|The specified EcsId is not found.|404|指定的实例 ID 不存在。|
|InvalidVSwitchId.NotFound|The specified VSwitchId is not found.|404|指定的交换机 ID 不存在。|
|InvalidSecurityGroupId.NotFound|The specified SecurityGroupId is not found.|404|指定的安全组 ID 不存在。|
|InvalidOperation.AvailabilityZoneMismatch|The VPC VSwitch of the specified ENI and ECS instance are not in the same availability zone.|403|指定的 VPC 交换机 ID、弹性网卡和实例 ID 不在同一个可用区。|
|InvalidOperation.VpcMismatch|The VPC of the specified ENI and security group are not in the same VPC.|403|指定的弹性网卡和安全组 ID 不在同一个 VPC。|
|InvalidSecurityGroupId.NotVpc|The specified SecurityGroupId not in VPC.|403|指定的安全组 ID 不是 VPC 类型。|

