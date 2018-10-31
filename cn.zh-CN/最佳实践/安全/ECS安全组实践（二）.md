# ECS安全组实践（二） {#concept_51171_zh .concept}

本文将介绍安全组的以下几个内容：

-    [授权](../../../../cn.zh-CN/API 参考/安全组/AuthorizeSecurityGroup.md#) 和 [撤销](../../../../cn.zh-CN/API 参考/安全组/RevokeSecurityGroup.md#) 安全组规则。
-    [加入安全组](../../../../cn.zh-CN/API 参考/安全组/JoinSecurityGroup.md#) 和 [离开安全组](../../../../cn.zh-CN/API 参考/安全组/LeaveSecurityGroup.md#)。

阿里云的网络类型分为 **经典网络** 和 **VPC**，它们对安全组支持不同的设置规则：

-   如果是经典网络，您可以设置以下几个规则：内网入方向、内网出方向、公网入方向和公网出方向。
-   如果是 VPC 网络，您可以设置：入方向 和 出方向。

## 安全组内网通讯的概念 {#section_n13_bp2_2fb .section}

本文开始之前，您应知道以下几个安全组内网通讯的概念：

-   默认只有同一个安全组的 ECS 实例可以网络互通。即使是同一个账户下的 ECS 实例，如果分属不同安全组，内网网络也是不通的。这个对于经典网络和 VPC 网络都适用。所以，经典网络的 ECS 实例也是内网安全的。
-   如果您有两台 ECS 实例，不在同一个安全组，您希望它们内网不互通，但实际上它们却内网互通，那么，您需要检查您的安全组内网规则设置。如果内网协议存在下面的协议，建议您重新设置。
    -   允许所有端口；
    -   授权对象为 CIDR 网段 \(SourceCidrIp\)：0.0.0.0/0 或者 10.0.0.0/8 的规则。 如果是经典网络，上述协议会造成您的内网暴露给其它的访问。
-   如果您想实现在不同安全组的资源之间的网络互通，您应使用安全组方式授权。对于内网访问，您应使用源安全组授权，而不是 CIDR 网段授权。

## 安全规则的属性 {#section_kqd_3p2_2fb .section}

安全规则主要是描述不同的访问权限，包括如下属性:

-   Policy：授权策略，参数值可以是 accept（接受）或 drop（拒绝）。
-   Priority：优先级，根据安全组规则的创建时间降序排序匹配。规则优先级可选范围为 1-100，默认值为 1，即最高优先级。数字越大，代表优先级越低。
-   NicType：网络类型。如果只指定了 SourceGroupId 而没有指定 SourceCidrIp，表示通过安全组方式授权，此时，NicType 必须指定为 intranet。
-   规则描述：
    -   IpProtocol：IP 协议，取值：tcp、udp、icmp、gre 或 all。all 表示所有的协议。
    -   PortRange：IP 协议相关的端口号范围：
        -   IpProtocol 取值为 tcp 或 udp 时，端口号取值范围为 1~65535，格式必须是“起始端口号/终止端口号”，如“1/200”表示端口号范围为1~200。如果输入值为“200/1”，接口调用将报错。
        -   IpProtocol 取值为 icmp、gre 或 all 时，端口号范围值为 -1/-1，表示不限制端口。
    -   如果通过安全组授权，应指定 SourceGroupId，即源安全组 ID。此时，根据是否跨账号授权，您可以选择设置源安全组所属的账号 SourceGroupOwnerAccount；
    -   如果通过 CIDR 授权，应指定 SourceCidrIp，即源 IP 地址段，必须使用 CIDR 格式。

## 授权一条入网请求规则 {#section_ujb_mp2_2fb .section}

在控制台或者通过 API 创建一个安全组时，入网方向默认 deny all，即默认情况下您拒绝所有入网请求。这并不适用于所有的情况，所以您要适度地配置您的入网规则。

比如，如果您需要开启公网的 80 端口对外提供 HTTP 服务，因为是公网访问，您希望入网尽可能多访问，所以在 IP 网段上不应做限制，可以设置为 0.0.0.0/0，具体设置可以参考以下描述，其中，括号外为控制台参数，括号内为 OpenAPI 参数，两者相同就不做区分。

-   网卡类型（NicType）：公网（internet）。如果是 VPC 类型的只需要填写 intranet，通过 EIP 实现公网访问。
-   授权策略（Policy）：允许（accept）。
-   规则方向（NicType）：入网。
-   协议类型（IpProtocol）：TCP（tcp）。
-   端口范围（PortRange）：80/80。
-   授权对象（SourceCidrIp）：0.0.0.0/0。
-   优先级（Priority）: 1。

**说明：** 上面的建议仅对公网有效。内网请求不建议使用 CIDR 网段，请参考 [经典网络的内网安全组规则不要使用 CIDR 或者 IP 授权](#section_plq_zn2_2fb)。

## 禁止一个入网请求规则 {#section_lr5_pp2_2fb .section}

禁止一条规则时，您只需要配置一条拒绝策略，并设置较低的优先级即可。这样，当有需要时，您可以配置其它高优先级的规则覆盖这条规则。例如，您可以采用以下设置拒绝 6379 端口被访问。

-   网卡类型（NicType）：内网（intranet）。
-   授权策略（Policy）：拒绝（drop）。
-   规则方向（NicType）：入网。
-   协议类型（IpProtocol）：TCP（tcp）。
-   端口范围（PortRange）：6379/6379。
-   授权对象（SourceCidrIp）：0.0.0.0/0。
-   优先级（Priority\)：100。

## 经典网络的内网安全组规则不要使用 CIDR 或者 IP 授权 {#section_plq_zn2_2fb .section}

对于经典网络的 ECS 实例，阿里云默认不开启任何内网的入规则。内网的授权一定要谨慎。

**说明：** 为了安全考虑，不建议开启任何基于 CIDR 网段的授权。

对于弹性计算来说，内网的 IP 经常变化，另外，这个 IP 的网段是没有规律的，所以，对于经典网络的内网，建议您通过安全组授权内网的访问。

例如，您在安全组 sg-redis 上构建了一个 redis 的集群，为了只允许特定的机器（如 sg-web）访问这个 redis 的服务器编组，您不需要配置任何 CIDR，只需要添加一条入规则：指定相关的安全组 ID 即可。

-   网卡类型（NicType）：内网（intranet）。
-   授权策略（Policy）：允许（accept）。
-   规则方向（NicType）：入网。
-   协议类型（IpProtocol）：TCP（tcp）。
-   端口范围（PortRange）：6379/6379。
-   授权对象（SourceGroupId）：sg-web。
-   优先级（Priority）：1。

对于 VPC 类型的实例，如果您已经通过多个 VSwitch 规划好自己的 IP 范围，您可以使用 CIDR 设置作为安全组入规则；但是，如果您的 VPC 网段不够清晰，建议您优先考虑使用安全组作为入规则。

## 将需要互相通信的 ECS 实例加入同一个安全组 {#section_bwv_sp2_2fb .section}

一个 ECS 实例最多可以加入 5 个安全组，而同一安全组内的 ECS 实例之间是网络互通的。如果您在规划时已经有多个安全组，而且，直接设置多个安全规则过于复杂的话，您可以新建一个安全组，然后将需要内网通讯的 ECS 实例加入这个新的安全组。

安全组是区分网络类型的，一个经典网络类型的 ECS 实例只能加入经典网络的安全组；一个 VPC 类型的 ECS 实例只能加入本 VPC 的安全组。

这里也不建议您将所有的 ECS 实例都加入一个安全组，这将会使得您的安全组规则设置变成梦魇。对于一个中大型应用来说，每个服务器编组的角色不同，合理地规划每个服务器的入方向请求和出方向请求是非常有必要的。

在控制台上，您可以根据文档 [加入安全组](../../../../cn.zh-CN/用户指南/实例/加入、移出安全组.md#) 的描述将一个实例加入安全组。

如果您对阿里云的 OpenAPI 非常熟悉，您可以参考 [使用 OpenAPI 弹性管理 ECS 实例](https://help.aliyun.com/document_detail/51173.html)，通过 OpenAPI 进行批量操作。对应的 Python 片段如下。

```
def join_sg(sg_id, instance_id):
    request = JoinSecurityGroupRequest()
    request.set_InstanceId(instance_id)
    request.set_SecurityGroupId(sg_id)
    response = _send_request(request)
    return response
# send open api request
def _send_request(request):
    request.set_accept_format('json')
    try:
        response_str = clt.do_action(request)
        logging.info(response_str)
        response_detail = json.loads(response_str)
        return response_detail
    except Exception as e:
        logging.error(e)
```

## 将 ECS 实例移除安全组 {#section_w1t_lq2_2fb .section}

如果 ECS 实例加入不合适的安全组，将会暴露或者 Block 您的服务，这时您可以选择将 ECS 实例从这个安全组中移除。但是在移除安全组之前必须保证您的 ECS 实例已经加入其它安全组。

**说明：** 将 ECS 实例从安全组移出，将会导致这个 ECS 实例和当前安全组内的网络不通，建议您在移出之前做好充分的测试。

对应的 Python 片段如下。

```
def leave_sg(sg_id, instance_id):
    request = LeaveSecurityGroupRequest()
    request.set_InstanceId(instance_id)
    request.set_SecurityGroupId(sg_id)
    response = _send_request(request)
    return response
# send open api request
def _send_request(request):
    request.set_accept_format('json')
    try:
        response_str = clt.do_action(request)
        logging.info(response_str)
        response_detail = json.loads(response_str)
        return response_detail
    except Exception as e:
        logging.error(e)
```

## 定义合理的安全组名称和标签 {#section_dx4_4q2_2fb .section}

合理的安全组名称和描述有助于您快速识别当前复杂的规则组合。您可以通过修改名称和描述来帮助自己识别安全组。

您也可以通过为安全组设置标签分组管理自己的安全组。您可以在控制台直接 [设置标签](../../../../cn.zh-CN/用户指南/标签/绑定标签.md#)，也通过 API 设置标签。

## 删除不需要的安全组 {#section_f3r_tq2_2fb .section}

安全组中的安全规则类似于一条条白名单和黑名单。所以，请不要保留不需要的安全组，以免因为错误加入某个 ECS 实例而造成不必要的麻烦。

