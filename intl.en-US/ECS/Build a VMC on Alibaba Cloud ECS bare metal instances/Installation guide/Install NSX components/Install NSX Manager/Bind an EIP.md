# Bind an EIP {#concept_int_1z1_hgb .concept}

This topic describes how to attach an Elastic IP \(EIP\) to the NSX Manager to send data packets to the Internet flexibly.

## Procedure {#section_jvz_5th_kgb .section}

1.  Log on to the [Alibaba Cloud ECS console](https://ecs.console.aliyun.com/).
2.  Navigate the [OpenAPI Explorer DescribeNetworkInterfaces](https://api.aliyun.com/new#/?product=Ecs&api=DescribeNetworkInterfaces), specify the RegionId \(where the ESXi host is located\) and InstanceId \(the ID of the ESXi host\), send the query request, and record the NetworkInterfaceId.
3.  In the [EIP console](https://ip.console.aliyun.com/), create an EIP. For more information, see [Create an EIP](../../../../../intl.en-US/User Guide/Create an EIP.md#).
4.  Bind the EIP to the ESXi host. For more information, see [Bind an EIP to an ENI](../../../../../intl.en-US/User Guide/Bind EIP to an ENI.md#).

