# API FAQ {#concept_761256 .concept}

-   [什么是ECS API？](#section_2mf_wov_wfu)
-   [创建ECS实例时报错：InvalidDataDiskCategory.NotSupported](#section_rqe_51b_fkf)
-   [如何创建有公网IP地址的ECS实例？](#section_iop_1gx_4ub)
-   [通过API创建的ECS实例，为什么无法Ping通ECS实例？](#section_2pr_bjo_kqj)
-   [ECS API绑定公网IP报错：The specified IP is already in use.](#section_qxl_ubh_cso)
-   [ECS API修改实例带宽可以指定时间范围吗？](#section_opz_hdk_3ab)
-   [通过API或SDK查询安全组规则，为什么无法显示所有的规则？](#section_0gg_gvb_36g)
-   [为什么API、SDK和阿里云CLI只返回十条信息？](#section_vto_62a_f45)

## 什么是ECS API？ {#section_2mf_wov_wfu .section}

ECS API是RPC风格的开放式API，为阿里云用户提供API服务。您可以基于ECS API管理和使用云服务器ECS。下图为您在使用API时，API请求的转发路径。有关如何调用ECS API，请参见[ECS API快速入门](intl.zh-CN/API参考/ECS API快速入门.md#)。

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/614896/156394043549776_zh-CN.png)

## 创建ECS实例时报错：InvalidDataDiskCategory.NotSupported {#section_rqe_51b_fkf .section}

-   问题现象：您在调用[RunInstances](intl.zh-CN/API参考/实例/RunInstances.md#)创建ECS实例时，返回如下错误信息。

    ``` {#codeblock_dgs_3nb_dh9}
    {
        "Code": "InvalidDataDiskCategory.NotSupported",
        "Message": "Specified disk category is not supported."
    }
    ```

-   问题原因：该错误是由于所在可用区不支持相应的云盘类型导致的。
-   解决方法：建议您在创建ECS实例前，调用[DescribeAvailableResource](intl.zh-CN/API参考/地域/DescribeAvailableResource.md#)查看具体可用区中的库存与产品规格供应情况，避免因资源供应原因引起报错。您也可以重新设置ZoneId取值，在其他可用区中尝试创建ECS实例。

    ``` {#codeblock_70q_r18_4zf}
    aliyun ecs RunInstances --ImageId win2008_64_ent_r2_cn_40G_alibase_20150429.vhd --InstanceType ecs.g5.large --SecurityGroupId <TheSecuriytyGroupId> --SystemDiskCategory cloud_efficiency --ZoneId cn-hangzhou-c
    ```


## 如何创建有公网IP地址的ECS实例？ {#section_iop_1gx_4ub .section}

-   方法一：调用[RunInstances](intl.zh-CN/API参考/实例/RunInstances.md#)，并将参数InternetMaxBandwidthOut设置为大于0的取值，系统自动为ECS实例分配公网IP。
-   方法二：调用[CreateInstance](intl.zh-CN/API参考/实例/CreateInstance.md#)后，再调用[AllocatePublicIpAddress](intl.zh-CN/API参考/网络/AllocatePublicIpAddress.md#)接口为ECS实例分配公网IP地址。

## 通过API创建的ECS实例，为什么无法Ping通ECS实例？ {#section_2pr_bjo_kqj .section}

-   问题现象：通过API新建的实例断网，内部无法访问外网，您也无法Ping通ECS实例的公网IP地址。
-   问题原因：您没有在ECS实例加入的安全组中添加相应的访问规则，导致出现无法访问的现象。
-   解决方法：调用[AuthorizeSecurityGroup](intl.zh-CN/API参考/安全组/AuthorizeSecurityGroup.md#)为相应安全组添加入方向访问规则即可。以ICMP协议为例，您可以添加以下安全组规则，允许任何IP地址发起Ping访问请求。

    ``` {#codeblock_x29_ll1_ix9}
    https://ecs.aliyuncs.com/?Action=AuthorizeSecurityGroup
    &SecurityGroupId=sg-bp15ed6xe1yxeycg7***
    &SourceCidrIp=0.0.0.0/0
    &IpProtocol=ICMP
    &PortRange=-1/-1
    &<公共请求参数>
    ```


## ECS API绑定公网IP报错：The specified IP is already in use. {#section_qxl_ubh_cso .section}

-   问题现象：您在调用[AllocatePublicIpAddress](intl.zh-CN/API参考/网络/AllocatePublicIpAddress.md#)设定IpAddress为一台ECS实例分配一个公网IP地址时，提示如下错误。

    ``` {#codeblock_kep_mrx_ifa}
    {
        "Code": "IpInUse",
        "Message": "The specified IP is already in use."
    }
    ```

-   问题原因：指定的IP地址已被占用。
-   解决方法：您可以查询该IP是否被占用再分配IP地址。

## ECS API修改实例带宽可以指定时间范围吗？ {#section_opz_hdk_3ab .section}

您可以调用[ModifyInstanceNetworkSpec](intl.zh-CN/API参考/网络/ModifyInstanceNetworkSpec.md#)修改ECS实例的公网带宽上下限，设置后直接生效。如果您需要在一段时间内变更公网带宽，可以设置StartTime和EndTime指定时间段。

如果您使用的是弹性公网IP（EIP），可以调用[ModifyEipAddressAttribute](../../../../intl.zh-CN/API参考/弹性公网IP/ModifyEipAddressAttribute.md#)，但无法指定生效时间段。

## 通过API或SDK查询安全组规则，为什么无法显示所有的规则？ {#section_0gg_gvb_36g .section}

安全组规则区分网卡类型，支持公网网卡（internet）和私网网卡（intranet）。您在使用[DescribeSecurityGroupAttribute](intl.zh-CN/API参考/安全组/DescribeSecurityGroupAttribute.md#)查询安全组时，NIC不是必需参数，但其默认值为internet。因此，以下阿里云CLI请求方法只显示公网网卡相关的安全组规则，不会返回所有安全组规则。

``` {#codeblock_tpl_qvr_rxl}
aliyun ecs DescribeSecurityGroupAttribute --SecurityGroupId <TheSecurityGroupId> --RegionId <TheRegionId>
```

若您需要查看内网方面的安全组规则，如内网互相打通、金融云VPN防火墙的规则等内网网卡安全组规则时，需要您设置NicType参数为intranet。

``` {#codeblock_na2_bjq_8yl}
aliyun ecs DescribeSecurityGroupAttribute --SecurityGroupId <TheSecurityGroupId> --RegionId <TheRegionId> --NicType intranet
```

## 为什么API、SDK和阿里云CLI只返回十条信息？ {#section_vto_62a_f45 .section}

详情请参见[为什么API、SDK和阿里云CLI只返回十条信息](intl.zh-CN/API参考/附录/为什么API、SDK和阿里云CLI只返回十条信息.md#)。

