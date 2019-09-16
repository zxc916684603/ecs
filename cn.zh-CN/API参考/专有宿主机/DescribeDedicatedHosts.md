# DescribeDedicatedHosts {#doc_api_Ecs_DescribeDedicatedHosts .reference}

调用DescribeDedicatedHosts查询一台或多台专有宿主机的详细信息，包括专有宿主机的物理性能指标、虚拟机器码、使用状态和已创建的ECS实例列表等。

## 调试 {#api_explorer .section}

[您可以在OpenAPI Explorer中直接运行该接口，免去您计算签名的困扰。运行成功后，OpenAPI Explorer可以自动生成SDK代码示例。](https://api.aliyun.com/#product=Ecs&api=DescribeDedicatedHosts&type=RPC&version=2014-05-26)

## 请求参数 {#parameters .section}

|名称|类型|是否必选|示例值|描述|
|--|--|----|---|--|
|RegionId|String|是|cn-hangzhou|专有宿主机所属的地域ID。您可以调用[DescribeRegions](~~25609~~)查看最新的阿里云地域列表。

 |
|Action|String|否|DescribeDedicatedHosts|系统规定参数。取值：DescribeDedicatedHosts

 |
|DedicatedHostIds|String|否|dh-xxxxxxxxxxxxxxxxx|专有宿主机ID列表。单次最多支持100个ID ，多个ID用一个格式类似“dh- xxxxxxxxx”, “dh- yyyyyyyyy”, … “dh- zzzzzzzzz”的JSON数组表示，ID之间用半角逗号（,）隔开。

 |
|DedicatedHostName|String|否|myDDH|专有宿主机的名称。

 |
|DedicatedHostType|String|否|ddh.g5|专有宿主机的规格类型。

 |
|PageNumber|Integer|否|1|响应信息的页码数。

 默认值：1

 |
|PageSize|Integer|否|10|响应信息的每页行数。最大值：100。

 默认值：10

 |
|Status|String|否|Available|专有宿主机的使用状态。取值范围：

 -   Available（默认）：可用状态。
-   Under-Assessment：故障潜伏期，专有宿主机可能会出故障。
-   Permanent-Failure：永久性故障，专有宿主机不可用。

 |
|Tag.N.Key|String|否|usage|专有宿主机的标签键。n的取值范围：1~20。一旦传入该值，则不允许为空字符串。最多支持64个字符，不能以aliyun、acs:、http://或者https://开头。

 |
|Tag.N.Value|String|否|test|专有宿主机的标签值。n的取值范围：1~20。一旦传入该值，可以为空字符串。最多支持128个字符，不能以aliyun、acs:、http://或者https://开头。

 |
|ZoneId|String|否|cn-hangzhou-g|可用区ID。

 |

## 返回数据 {#resultMapping .section}

|名称|类型|示例值|描述|
|--|--|---|--|
|DedicatedHosts| | |专有宿主机的详细信息集合。

 |
|DedicatedHost| | |专有宿主机的详细信息集合。

 |
|ActionOnMaintenance|String|Migrate|当专有宿主机发生故障或者在线修复时，为其所宿实例设置迁移方案。取值范围：

 -   Migrate：迁移实例到其他物理机并重新启动实例。

默认值：Migrate（当专有宿主机上挂载云盘存储时）

-   Stop：在当前专有宿主机上停止实例，确认无法修复专有宿主机后，迁移实例到其他物理机并重新启动实例。

默认值：Stop（当专有宿主机上挂载本地盘存储时）


 |
|AutoPlacement|String|on|专有宿主机是否加入自动部署资源池。取值范围：

 -   on：加入自动部署资源池。
-   off：不加入自动部署资源池。

 自动部署详情，请参见[自动部署功能介绍](~~118938~~)。

 |
|Capacity| | |专有宿主机性能指标集合。

 |
|AvailableLocalStorage|Integer|65|剩余的本地盘容量。单位：GiB。

 |
|AvailableMemory|Float|25|剩余的内存容量，单位：GiB。

 |
|AvailableVcpus|Integer|5|剩余的vCPU核数。

 |
|LocalStorageCategory|String|i2|本地盘类型。

 |
|TotalLocalStorage|Integer|512|本地盘总容量，单位：GiB。

 |
|TotalMemory|Float|1024|内存总容量，单位：GiB。

 |
|TotalVcpus|Integer|56|vCPU总核数。

 |
|ChargeType|String|Prepaid|专有宿主机的计费方式。

 |
|Cores|Integer|3|单个CPU的核数。

 |
|CreationTime|String|2018-01-01T12:00:00Z|专有宿主机的创建时间。按照[ISO8601](~~25696~~)标准表示，并需要使用UTC+0时间，格式为yyyy-MM-ddTHH:mm:ssZ。

 |
|DedicatedHostId|String|dh-xxxxxxxxxxxxxxxxxxxxxx|专有宿主机ID。

 |
|DedicatedHostName|String|myDDH|专有宿主机的名称。

 |
|DedicatedHostType|String|ddh.g5|专有宿主机的规格类型。

 |
|Description|String|this-is-my-DDH|专有宿主机的描述信息。

 |
|ExpiredTime|String|2019-01-01T12:00:00Z|包年包月专有宿主机的到期时间。按照[ISO8601](~~25696~~)标准表示，并需要使用UTC+0时间，格式为yyyy-MM-ddTHH:mm:ssZ。

 |
|Instances| | |专有宿主机上创建的ECS实例。

 |
|Instance| | |专有宿主机上创建的ECS实例。

 |
|InstanceId|String|i-xxxxxxxxxxxxxxxxxxxxxx|专有宿主机上创建的ECS实例ID。

 |
|InstanceType|String|ecs.g5|专有宿主机上创建的ECS实例类型。

 |
|MachineId|String|d7a1xxxxxxxxxxxxxx1bbdb|专有宿主机虚拟机器码。

 |
|NetworkAttributes| | |专有宿主机的网络属性值。

 |
|OperationLocks| | |专有宿主机资源被锁定原因。

 |
|OperationLock| | |专有宿主机资源被锁定原因。

 |
|LockReason|String|financial|资源锁定原因。可能取值：financial（因账号欠费被锁定）。

 |
|RegionId|String|cn-hangzhou|专有宿主机所在地域ID。

 |
|ResourceGroupId|String|rg-xxxxxxxxxxxxxxxxxxxxx|专有宿主机所在资源组ID。

 |
|Sockets|Integer|5|物理处理器（CPU）数量。

 |
|Status|String|Available|专有宿主机的使用状态。取值范围：Available | Under-Assessment | Permanent-Failure

 |
|SupportedInstanceTypeFamilies| |ecs.g5|专有宿主机支持的ECS实例规格族。

 |
|SupportedInstanceTypeFamily| | |专有宿主机支持的ECS实例规格族。

 |
|SupportedInstanceTypesList| |ecs.g5|专有宿主机支持的ECS实例规格族。

 |
|SupportedInstanceTypesList| | |专有宿主机支持的ECS实例规格族。

 |
|Tags| | |专有宿主机的标签。

 |
|Tag| | |专有宿主机的标签。

 |
|ZoneId|String|cn-hangzhou-g|可用区ID。

 |
|PageNumber|Integer|5|专有宿主机列表的页码。

 |
|PageSize|Integer|1|输入时设置的每页行数。

 |
|RequestId|String|C9E9EA51-6B74-409E-BA40-107126A200D4|请求ID。

 |
|TotalCount|Integer|3|专有宿主机总数。

 |

## 示例 {#demo .section}

请求示例

``` {#request_demo}

https://ecs.aliyuncs.com/?Action=DescribeDedicatedHosts
&RegionId=cn-hangzhou
&<公共请求参数>

```

正常返回示例

`XML` 格式

``` {#xml_return_success_demo}
<DescribeDedicatedHostsResponse>
	  <PageNumber>1</PageNumber>
	  <DedicatedHosts>
		    <DedicatedHost>
			      <AutoPlacement>on</AutoPlacement>
			      <Instances></Instances>
			      <ZoneId>cn-hangzhou-g</ZoneId>
			      <Sockets>2</Sockets>
			      <Cores>48</Cores>
			      <DedicatedHostType>ddh.v5</DedicatedHostType>
			      <PhysicalGpus>0</PhysicalGpus>
			      <DedicatedHostName>ddh-1</DedicatedHostName>
			      <SaleCycle></SaleCycle>
			      <AutoReleaseTime></AutoReleaseTime>
			      <SupportedInstanceTypeFamilies>
				        <SupportedInstanceTypeFamily>ecs.v5</SupportedInstanceTypeFamily>
			      </SupportedInstanceTypeFamilies>
			      <NetworkAttributes></NetworkAttributes>
			      <DedicatedHostId>dh-bp1xxxxxxxxxxxxxg</DedicatedHostId>
			      <ChargeType>PostPaid</ChargeType>
			      <Description></Description>
			      <ResourceGroupId></ResourceGroupId>
			      <CreationTime>2019-08-06T07:40Z</CreationTime>
			      <Status>Available</Status>
			      <RegionId>cn-hangzhou</RegionId>
			      <GPUSpec></GPUSpec>
			      <ActionOnMaintenance>Migrate</ActionOnMaintenance>
			      <Capacity>
				        <AvailableVcpus>336</AvailableVcpus>
				        <TotalMemory>672</TotalMemory>
				        <AvailableVgpus>0</AvailableVgpus>
				        <TotalVgpus>0</TotalVgpus>
				        <TotalVcpus>336</TotalVcpus>
				        <AvailableLocalStorage>0</AvailableLocalStorage>
				        <TotalLocalStorage>0</TotalLocalStorage>
				        <LocalStorageCategory></LocalStorageCategory>
				        <AvailableMemory>672</AvailableMemory>
			      </Capacity>
			      <OperationLocks></OperationLocks>
			      <MachineId>3e4xxxxxxxxxxxxxxxx16</MachineId>
			      <SupportedInstanceTypesList>
				        <SupportedInstanceTypesList>ecs.v5-c1m1.large</SupportedInstanceTypesList>
				        <SupportedInstanceTypesList>ecs.v5-c1m1.xlarge</SupportedInstanceTypesList>
				        <SupportedInstanceTypesList>ecs.v5-c1m1.2xlarge</SupportedInstanceTypesList>
				        <SupportedInstanceTypesList>ecs.v5-c1m1.3xlarge</SupportedInstanceTypesList>
				        <SupportedInstanceTypesList>ecs.v5-c1m1.4xlarge</SupportedInstanceTypesList>
				        <SupportedInstanceTypesList>ecs.v5-c1m2.xlarge</SupportedInstanceTypesList>
				        <SupportedInstanceTypesList>ecs.v5-c1m2.large</SupportedInstanceTypesList>
				        <SupportedInstanceTypesList>ecs.v5-c1m1.8xlarge</SupportedInstanceTypesList>
				        <SupportedInstanceTypesList>ecs.v5-c1m2.2xlarge</SupportedInstanceTypesList>
				        <SupportedInstanceTypesList>ecs.v5-c1m2.3xlarge</SupportedInstanceTypesList>
				        <SupportedInstanceTypesList>ecs.v5-c1m2.4xlarge</SupportedInstanceTypesList>
				        <SupportedInstanceTypesList>ecs.v5-c1m2.8xlarge</SupportedInstanceTypesList>
				        <SupportedInstanceTypesList>ecs.v5-c1m4.4xlarge</SupportedInstanceTypesList>
				        <SupportedInstanceTypesList>ecs.v5-c1m4.3xlarge</SupportedInstanceTypesList>
				        <SupportedInstanceTypesList>ecs.v5-c1m4.2xlarge</SupportedInstanceTypesList>
				        <SupportedInstanceTypesList>ecs.v5-c1m4.xlarge</SupportedInstanceTypesList>
				        <SupportedInstanceTypesList>ecs.v5-c1m4.large</SupportedInstanceTypesList>
				        <SupportedInstanceTypesList>ecs.v5-c1m4.8xlarge</SupportedInstanceTypesList>
				        <SupportedInstanceTypesList>ecs.v5-c1m8.large</SupportedInstanceTypesList>
				        <SupportedInstanceTypesList>ecs.v5-c1m8.xlarge</SupportedInstanceTypesList>
				        <SupportedInstanceTypesList>ecs.v5-c1m8.2xlarge</SupportedInstanceTypesList>
				        <SupportedInstanceTypesList>ecs.v5-c1m8.3xlarge</SupportedInstanceTypesList>
				        <SupportedInstanceTypesList>ecs.v5-c1m8.4xlarge</SupportedInstanceTypesList>
				        <SupportedInstanceTypesList>ecs.v5-c1m8.8xlarge</SupportedInstanceTypesList>
			      </SupportedInstanceTypesList>
			      <ExpiredTime>2999-09-08T16:00Z</ExpiredTime>
		    </DedicatedHost>
		    <DedicatedHost>
			      <AutoPlacement>on</AutoPlacement>
			      <Instances></Instances>
			      <ZoneId>cn-hangzhou-f</ZoneId>
			      <Sockets>2</Sockets>
			      <Cores>32</Cores>
			      <DedicatedHostType>ddh.sn1ne</DedicatedHostType>
			      <PhysicalGpus>0</PhysicalGpus>
			      <DedicatedHostName>ddh-2</DedicatedHostName>
			      <SaleCycle></SaleCycle>
			      <AutoReleaseTime></AutoReleaseTime>
			      <SupportedInstanceTypeFamilies>
				        <SupportedInstanceTypeFamily>ecs.sn1ne</SupportedInstanceTypeFamily>
			      </SupportedInstanceTypeFamilies>
			      <NetworkAttributes></NetworkAttributes>
			      <DedicatedHostId>dh-bpxxxxxxxxxxxxx</DedicatedHostId>
			      <ChargeType>PrePaid</ChargeType>
			      <Description></Description>
			      <ResourceGroupId></ResourceGroupId>
			      <CreationTime>2019-07-03T07:07Z</CreationTime>
			      <Status>Available</Status>
			      <RegionId>cn-hangzhou</RegionId>
			      <GPUSpec></GPUSpec>
			      <ActionOnMaintenance>Migrate</ActionOnMaintenance>
			      <Capacity>
				        <AvailableVcpus>56</AvailableVcpus>
				        <TotalMemory>112</TotalMemory>
				        <AvailableVgpus>0</AvailableVgpus>
				        <TotalVgpus>0</TotalVgpus>
				        <TotalVcpus>56</TotalVcpus>
				        <AvailableLocalStorage>0</AvailableLocalStorage>
				        <TotalLocalStorage>0</TotalLocalStorage>
				        <LocalStorageCategory></LocalStorageCategory>
				        <AvailableMemory>112</AvailableMemory>
			      </Capacity>
			      <OperationLocks></OperationLocks>
			      <MachineId>78cxxxxxxxxxxxxxxx8006d</MachineId>
			      <SupportedInstanceTypesList>
				        <SupportedInstanceTypesList>ecs.sn1ne.large</SupportedInstanceTypesList>
				        <SupportedInstanceTypesList>ecs.sn1ne.xlarge</SupportedInstanceTypesList>
				        <SupportedInstanceTypesList>ecs.sn1ne.2xlarge</SupportedInstanceTypesList>
				        <SupportedInstanceTypesList>ecs.sn1ne.4xlarge</SupportedInstanceTypesList>
				        <SupportedInstanceTypesList>ecs.sn1ne.8xlarge</SupportedInstanceTypesList>
				        <SupportedInstanceTypesList>ecs.sn1ne.3xlarge</SupportedInstanceTypesList>
				        <SupportedInstanceTypesList>ecs.sn1ne.6xlarge</SupportedInstanceTypesList>
				        <SupportedInstanceTypesList>ecs.sn1ne.22xlarge</SupportedInstanceTypesList>
			      </SupportedInstanceTypesList>
			      <ExpiredTime>2999-09-08T16:00Z</ExpiredTime>
		    </DedicatedHost>
	  </DedicatedHosts>
	  <TotalCount>2</TotalCount>
	  <PageSize>10</PageSize>
	  <RequestId>FCED4B7A-53D5-4C04-ABE3-26D4F3890D57</RequestId>
</DescribeDedicatedHostsResponse>
```

`JSON` 格式

``` {#json_return_success_demo}
{
	"PageNumber":1,
	"DedicatedHosts":{
		"DedicatedHost":[
			{
				"DedicatedHostId":"dh-dedicatedhost1",
				"ChargeType":"PostPaid",
				"Description":"",
				"ResourceGroupId":"",
				"SupportInstanceTypeFamilies":{
					"SupportInstanceTypeFamily":[
						"ecs.se1ne"
					]
				},
				"Instances":{
					"Instance":[]
				},
				"ZoneId":"cn-beijing-c",
				"CreationTime":"2018-08-13T07:59Z",
				"Sockets":2,
				"Status":"Available",
				"Cores":32,
				"DedicatedHostType":"ddh.se1ne",
				"RegionId":"cn-beijing",
				"DedicatedHostName":"ddh-1",
				"SaleCycle":"",
				"Capacity":{
					"AvailableVcpus":56,
					"TotalMemory":448,
					"TotalVcpus":56,
					"TotalLocalStorage":0,
					"AvailableLocalStorage":0,
					"AvailableMemory":448,
					"LocalStorageCategory":""
				},
				"AutoReleaseTime":"",
				"MachineId":"xxxx",
				"OperationLocks":{
					"OperationLock":[]
				},
				"ExpiredTime":"2999-09-08T16:00Z"
			},
			{
				"DedicatedHostId":"dh-dedicatedhost2",
				"ChargeType":"PostPaid",
				"Description":"",
				"ResourceGroupId":"",
				"SupportInstanceTypeFamilies":{
					"SupportInstanceTypeFamily":[
						"ecs.se1ne"
					]
				},
				"Instances":{
					"Instance":[]
				},
				"ZoneId":"cn-beijing-c",
				"CreationTime":"2018-08-13T07:59Z",
				"Sockets":2,
				"Status":"Available",
				"Cores":32,
				"DedicatedHostType":"ddh.se1ne",
				"RegionId":"cn-beijing",
				"DedicatedHostName":"ddh-2",
				"SaleCycle":"",
				"Capacity":{
					"AvailableVcpus":56,
					"TotalMemory":448,
					"TotalVcpus":56,
					"TotalLocalStorage":0,
					"AvailableLocalStorage":0,
					"AvailableMemory":448,
					"LocalStorageCategory":""
				},
				"AutoReleaseTime":"",
				"MachineId":"f9b97axxxxxxxxxxxxxxxxx",
				"OperationLocks":{
					"OperationLock":[]
				},
				"ExpiredTime":"2999-09-08T16:00Z"
			}
		]
	},
	"TotalCount":2,
	"PageSize":10,
	"RequestId":"9D5CC4F5-921A-4E02-B971-0DAF703407BE"
}
```

## 错误码 { .section}

|HttpCode|错误码|错误信息|描述|
|--------|---|----|--|
|400|InvalidStatus.ValueNotSupported|The pecified dedicated host status is not supported.|当前宿主机状态不支持此操作。|
|400|MissingParamter.RegionId|The regionId should not be null.|参数 RegionId 不得为空。|
|403|InvalidDedicatedHostIds.Malformed|The amount of specified dedicatedHostIds exceeds the limit.|DedicatedHostIds参数超过最多个数，最多100。|
|400|InvalidParameter.DedicatedHostIds|The specified parameter dedicatedHostIds is not valid.|DedicatedHostIds参数无效。|
|400|InvalidRegion.NotFound|The specified parameter RegionId is not valid.|RegionId参数不合法|
|400|InvalidZone.NotFound|The specified parameter ZoneId is not valid.|指定的 ZoneId 不合法。|
|404|InvalidLockReason.NotFound|The specified LockReason is not found|指定的锁定类型不存在。|

访问[错误中心](https://error-center.aliyun.com/status/product/Ecs)查看更多错误码。

