# 弹性公网IP {#concept_z4b_mlh_jhb .concept}

阿里云弹性公网IP（Elastic IP Address，简称EIP）是可以独立购买和持有的公网IP地址资源。如果您希望长期使用某个公网IP地址，根据业务需要将它绑定或解绑指定的专有网络VPC类型ECS实例上，您可以选择EIP。

## EIP概述 {#section_bsz_stn_mgb .section}

EIP是一种NAT IP，位于阿里云的公网网关上，通过NAT方式映射到被绑定的ECS实例位于私网的网卡上。因此，绑定了EIP的专有网络类型ECS实例可以直接使用这个IP进行公网通信。但您无法在ECS实例的网卡上看到这个IP地址。

## 产品优势 {#section_mhm_2ws_lgb .section}

相较于通过开启公网带宽为ECS实例分配的公网IP，EIP支持更灵活的购买方式和管理操作，见下表所示。

|比较项|ECS实例公网IP|EIP|
|:--|:--------|:--|
|是否支持单独购买与持有|不支持|支持|
|是否支持在ECS实例自由绑定或解绑|不支持|支持|
|是否支持实时调整带宽值|支持|支持|

## 计费方式 {#section_olw_5cp_mgb .section}

EIP支持包年包月和按量付费计费方式，详情请参见 *EIP文档* [计费概述](../../../../cn.zh-CN/产品定价/计费概述.md#)。

## 使用限制 {#section_xaq_jol_qya .section}

EIP绑定ECS实例上时，ECS实例有以下限制条件：

-   网络类型必须是专有网络VPC。
-   地域必须和EIP的地域相同。
-   必须处于**运行中**或**已停止**状态。
-   没有配置固定公网IP或绑定其他EIP。

## 申请EIP {#section_8ub_nya_yuf .section}

一台专有网络VPC类型的ECS实例可以关联多个公网IP地址，可以是系统分配的公网IP地址或者是弹性公网IP。

您可以单独申请EIP地址，并绑定到未分配公网IP地址的专有网络VPC类型ECS实例上。详情请参见[申请EIP](../../../../cn.zh-CN/用户指南/申请EIP/申请新EIP.md#)。

## 续费EIP {#section_vh2_y34_vtb .section}

如果您采用的是包年包月计费方式，可以续费EIP。具体步骤，请参见 *EIP文档* [续费](../../../../cn.zh-CN/用户指南/管理包年包月实例/续费.md#)。

## 释放EIP {#section_1tv_4dp_ezm .section}

如果您不再需要一个EIP地址，先将其与ECS实例解绑，再登录EIP管理控制台释放EIP。具体步骤，请参见[解绑EIP](../../../../cn.zh-CN/用户指南/解绑EIP.md#)。

