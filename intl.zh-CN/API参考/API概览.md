# API概览 {#doc_9844 .concept}

云服务器ECS提供以下相关API接口。

## 实例 {#section_qgi_2ia_agq .section}

|API|描述|
|---|--|
|[RunInstances](intl.zh-CN/API参考/实例/RunInstances.md)|创建一台或多台按量付费或者预付费（包年包月）ECS实例。|
|[CreateInstance](intl.zh-CN/API参考/实例/CreateInstance.md)|创建一台ECS实例。|
|[DescribeInstances](intl.zh-CN/API参考/实例/DescribeInstances.md)|查询一台或多台实例的详细信息。|
|[StartInstance](intl.zh-CN/API参考/实例/StartInstance.md)|启动一台实例。|
|[RebootInstance](intl.zh-CN/API参考/实例/RebootInstance.md)|重启一台实例。|
|[StopInstance](intl.zh-CN/API参考/实例/StopInstance.md)|停止运行一台实例。|
|[DeleteInstance](intl.zh-CN/API参考/实例/DeleteInstance.md)|释放一台按量付费实例或者到期的预付费（包年包月）实例。|
|[AttachInstanceRamRole](intl.zh-CN/API参考/实例/AttachInstanceRamRole.md)|为一台或多台 ECS 实例授予 实例 RAM 角色。如果实例已有 RAM 角色，则报错提示您不能附加新的角色。|
|[DetachInstanceRamRole](intl.zh-CN/API参考/实例/DetachInstanceRamRole.md)|收回一台或多台ECS实例的实例RAM角色。|
|[DescribeInstanceStatus](intl.zh-CN/API参考/实例/DescribeInstanceStatus.md)|批量获取实例状态信息。|
|[RenewInstance](intl.zh-CN/API参考/实例/RenewInstance.md)|续费一台预付费 ECS 实例。|
|[ReactivateInstances](intl.zh-CN/API参考/实例/ReactivateInstances.md)|重新启动一台已过期或欠费回收中的按量付费 ECS 实例。|
|[RedeployInstance](intl.zh-CN/API参考/实例/RedeployInstance.md)|当ECS实例收到系统事件通知时，RedeployInstance可以重新部署这台实例。|
|[DescribeInstanceVncUrl](intl.zh-CN/API参考/实例/DescribeInstanceVncUrl.md)|查询一台ECS实例的Web管理终端地址。|
|[DescribeUserData](intl.zh-CN/API参考/实例/DescribeUserData.md)|查询一台 ECS 实例的 自定义数据。|
|[DescribeInstanceAutoRenewAttribute](intl.zh-CN/API参考/实例/DescribeInstanceAutoRenewAttribute.md)|查询一台或多台预付费实例自动续费状态。|
|[DescribeInstanceRamRole](intl.zh-CN/API参考/实例/DescribeInstanceRamRole.md)|查询一台或者多台 ECS 实例上的已赋予的实例 RAM 角色。|
|[DescribeSpotPriceHistory](intl.zh-CN/API参考/实例/DescribeSpotPriceHistory.md)|查询抢占式实例近 30 天内的历史价格。|
|[DescribeInstanceTypeFamilies](intl.zh-CN/API参考/实例/DescribeInstanceTypeFamilies.md)|查询云服务器 ECS 提供的实例规格族资源。|
|[DescribeInstanceTypes](intl.zh-CN/API参考/实例/DescribeInstanceTypes.md)|查询云服务器 ECS 提供的实例规格资源。|
|[ModifyInstanceVpcAttribute](intl.zh-CN/API参考/实例/ModifyInstanceVpcAttribute.md)|修改一台 ECS 实例的专有网络 VPC 属性。|
|[ModifyInstanceAttribute](intl.zh-CN/API参考/实例/ModifyInstanceAttribute.md)|修改一台实例的部分信息，包括实例密码、名称、描述、主机名和自定义数据等。如果是t5突发性能实例，可以切换这台实例的性能突发模式。|
|[ModifyInstanceVncPasswd](intl.zh-CN/API参考/实例/ModifyInstanceVncPasswd.md)|修改一台 ECS 实例的 Web 管理终端 密码。|
|[ModifyInstanceAutoReleaseTime](intl.zh-CN/API参考/实例/ModifyInstanceAutoReleaseTime.md)|为一台按量付费 实例设定或者取消自动释放时间。设置自动释放时请谨慎操作，配置的时间到期后将自动释放 ECS 实例。|
|[ModifyInstanceAutoRenewAttribute](intl.zh-CN/API参考/实例/ModifyInstanceAutoRenewAttribute.md)|设置一台或多台预付费实例的自动续费状态。为了减少您的资源到期维护成本，包年包月 ECS 实例可以设置自动续费。|
|[ModifyInstanceChargeType](intl.zh-CN/API参考/实例/ModifyInstanceChargeType.md)|更换一台或者多台实例的计费方式。支持在按量付费实例和预付费（包年包月）实例间相互转换，同时可以将实例挂载的所有按量付费云盘转换为预付费（包年包月）云盘。|
|[ModifyInstanceSpec](intl.zh-CN/API参考/实例/ModifyInstanceSpec.md)|调整一台按量付费实例的实例规格和公网带宽大小。|
|[ModifyPrepayInstanceSpec](intl.zh-CN/API参考/实例/ModifyPrepayInstanceSpec.md)|升级或者降低预付费（包年包月）实例规格，新实例规格将会覆盖实例的整个生命周期。|

## 启动模板 {#section_jxn_j1p_nw6 .section}

|API|描述|
|---|--|
|[CreateLaunchTemplate](intl.zh-CN/API参考/启动模板/CreateLaunchTemplate.md)|创建一个实例启动模板，简称模板。实例启动模板能免除您每次创建实例时都需要填入大量配置参数。|
|[CreateLaunchTemplateVersion](intl.zh-CN/API参考/启动模板/CreateLaunchTemplateVersion.md)|根据指定的实例启动模板创建一个版本。|
|[DeleteLaunchTemplate](intl.zh-CN/API参考/启动模板/DeleteLaunchTemplate.md)|删除一个实例启动模板。|
|[DeleteLaunchTemplateVersion](intl.zh-CN/API参考/启动模板/DeleteLaunchTemplateVersion.md)|删除指定实例启动模板的一个版本。不支持删除默认版本，您需要通过 DeleteLaunchTemplate 删除整个实例启动模板才能删除默认版本。|
|[DescribeLaunchTemplates](intl.zh-CN/API参考/启动模板/DescribeLaunchTemplates.md)|查询一个或多个可用的实例启动模板。|
|[DescribeLaunchTemplateVersions](intl.zh-CN/API参考/启动模板/DescribeLaunchTemplateVersions.md)|查询实例启动模板版本。|
|[ModifyLaunchTemplateDefaultVersion](intl.zh-CN/API参考/启动模板/ModifyLaunchTemplateDefaultVersion.md)|切换启动模板的某个版本为该模板的默认版本。如果您在创建实例（RunInstances）时不指定模板版本号，会采用默认版本。|

## 弹性供应组 {#section_xzj_fvi_g6o .section}

|API|描述|
|---|--|
|[CreateAutoProvisioningGroup](intl.zh-CN/API参考/弹性供应组/CreateAutoProvisioningGroup.md)|调用CreateAutoProvisioningGroup接口创建一个弹性供应组。|
|[ModifyAutoProvisioningGroup](intl.zh-CN/API参考/弹性供应组/ModifyAutoProvisioningGroup.md)|调用ModifyAutoProvisioningGroup接口修改一个弹性供应组的设置。|
|[DeleteAutoProvisioningGroup](intl.zh-CN/API参考/弹性供应组/DeleteAutoProvisioningGroup.md)|调用DeleteAutoProvisioningGroup接口删除一个弹性供应组。|
|[DescribeAutoProvisioningGroups](intl.zh-CN/API参考/弹性供应组/DescribeAutoProvisioningGroups.md)|调用DescribeAutoProvisioningGroups接口查询弹性供应组。|
|[DescribeAutoProvisioningGroupInstances](intl.zh-CN/API参考/弹性供应组/DescribeAutoProvisioningGroupInstances.md)|调用DescribeAutoProvisioningGroupInstances查询指定弹性供应组下的实例。|
|[DescribeAutoProvisioningGroupHistory](intl.zh-CN/API参考/弹性供应组/DescribeAutoProvisioningGroupHistory.md)|调用DescribeAutoProvisioningGroupHistory接口查询弹性供应组的调度任务信息。|

## 磁盘 {#section_agf_aec_xie .section}

|API|描述|
|---|--|
|[CreateDisk](intl.zh-CN/API参考/磁盘/CreateDisk.md)|创建一块按量付费或预付费数据盘。磁盘类型包括普通云盘、高效云盘、SSD云盘和ESSD云盘。|
|[DeleteDisk](intl.zh-CN/API参考/磁盘/DeleteDisk.md)|释放一块按量付费数据盘。磁盘类型包括普通云盘、高效云盘和SSD云盘。|
|[DescribeDisks](intl.zh-CN/API参考/磁盘/DescribeDisks.md)|查询您已经创建的磁盘。|
|[AttachDisk](intl.zh-CN/API参考/磁盘/AttachDisk.md)|为一台ECS实例挂载一块数据盘。|
|[DetachDisk](intl.zh-CN/API参考/磁盘/DetachDisk.md)|从一台实例上卸载一块按量付费磁盘。磁盘类型包括普通云盘、高效云盘和SSD云盘。|
|[ModifyDiskChargeType](intl.zh-CN/API参考/磁盘/ModifyDiskChargeType.md)|修改一台实例上挂载的一块或最多 16 块磁盘的计费方式。|
|[ModifyDiskAttribute](intl.zh-CN/API参考/磁盘/ModifyDiskAttribute.md)|修改您的磁盘的属性或者明细。|
|[ReplaceSystemDisk](intl.zh-CN/API参考/磁盘/ReplaceSystemDisk.md)|更换一台 ECS 实例的系统盘或者操作系统。|
|[ReInitDisk](intl.zh-CN/API参考/磁盘/ReInitDisk.md)|重新初始化云盘到创建时的初始状态。|
|[ResetDisk](intl.zh-CN/API参考/磁盘/ResetDisk.md)|使用磁盘的历史快照回滚至某一阶段的磁盘状态。|
|[ResizeDisk](intl.zh-CN/API参考/磁盘/ResizeDisk.md)|扩容一块云盘，支持扩容系统盘和数据盘。|
|[ModifyDiskSpec](intl.zh-CN/API参考/磁盘/ModifyDiskSpec.md)|调用ModifyDiskSpec升级一块ESSD云盘的性能等级。|

## 预留实例券 {#section_cat_cse_92c .section}

|API|描述|
|---|--|
|[PurchaseReservedInstancesOffering](intl.zh-CN/API参考/预留实例券/PurchaseReservedInstancesOffering.md)|您可以调用PurchaseReservedInstancesOffering购买预留实例券，以自动匹配对应的物理实例，抵扣按量付费实例账单。|
|[DescribeReservedInstances](intl.zh-CN/API参考/预留实例券/DescribeReservedInstances.md)|您可以调用DescribeReservedInstances查询已经购买的预留实例券。|
|[ModifyReservedInstances](intl.zh-CN/API参考/预留实例券/ModifyReservedInstances.md)|您可以通过ModifyReservedInstances更改预留实例券。|

## 镜像 {#section_3q0_tyv_7ka .section}

|API|描述|
|---|--|
|[ExportImage](intl.zh-CN/API参考/镜像/ExportImage.md)|导出您的自定义镜像到与该自定义镜像同一地域的 OSS Bucket 里。|
|[CreateImage](intl.zh-CN/API参考/镜像/CreateImage.md)|创建一份自定义镜像。您可以使用创建的自定义镜像创建ECS实例（RunInstances）或者更换实例的系统盘（ReplaceSystemDisk）。|
|[ImportImage](intl.zh-CN/API参考/镜像/ImportImage.md)|导入您已有的镜像文件到云服务器ECS，并作为自定义镜像出现在相应地域中。|
|[CopyImage](intl.zh-CN/API参考/镜像/CopyImage.md)|复制一个地域下的自定义镜像到其他地域。您可以在其他地域可以使用复制后的镜像 创建 ECS 实例（RunInstances）或者更换实例的系统盘（ReplaceSystemDisk）。|
|[CancelCopyImage](intl.zh-CN/API参考/镜像/CancelCopyImage.md)|取消正在进行中的复制镜像（CopyImage）任务。|
|[DescribeImages](intl.zh-CN/API参考/镜像/DescribeImages.md)|查询您可以使用的镜像资源。|
|[DeleteImage](intl.zh-CN/API参考/镜像/DeleteImage.md)|删除一份自定义镜像。|
|[DescribeImageSharePermission](intl.zh-CN/API参考/镜像/DescribeImageSharePermission.md)|查询一份自定义镜像已经共享的所有用户。返回结果支持分页显示，每页的信息条目默认为 10 条。|
|[ModifyImageAttribute](intl.zh-CN/API参考/镜像/ModifyImageAttribute.md)|修改一份自定义镜像的名称和描述。|
|[ModifyImageSharePermission](intl.zh-CN/API参考/镜像/ModifyImageSharePermission.md)|管理镜像共享权限。您可以将自己的自定义镜像共享给其他阿里云用户，该用户可以使用共享的自定义镜像创建 ECS 实例（RunInstances）或者更换实例的系统盘（ReplaceSystemDisk）。|
|[DescribeImageSupportInstanceTypes](intl.zh-CN/API参考/镜像/DescribeImageSupportInstanceTypes.md)|查询指定镜像支持的实例规格。|

## 快照 {#section_vay_o96_urw .section}

|API|描述|
|---|--|
|[CreateSnapshot](intl.zh-CN/API参考/快照/CreateSnapshot.md)|为一块云盘创建一份快照。|
|[CreateAutoSnapshotPolicy](intl.zh-CN/API参考/快照/CreateAutoSnapshotPolicy.md)|创建一条自动快照策略。创建的自动快照策略可以应用到任一磁盘（ApplyAutoSnapshotPolicy），成功创建的自动快照策略可以后续修改策略内容（ModifyAutoSnapshotPolicyEx）。|
|[ApplyAutoSnapshotPolicy](intl.zh-CN/API参考/快照/ApplyAutoSnapshotPolicy.md)|为一块或者多块磁盘应用自动快照策略。目标磁盘已经应用了自动快照策略时，调用 ApplyAutoSnapshotPolicy 可以更换磁盘当前应用的自动快照策略。|
|[DeleteSnapshot](intl.zh-CN/API参考/快照/DeleteSnapshot.md)|删除指定的快照。如果需要取消正在创建的快照，也可以调用该接口删除快照，即取消创建快照任务。|
|[CancelAutoSnapshotPolicy](intl.zh-CN/API参考/快照/CancelAutoSnapshotPolicy.md)|取消一块或者多块磁盘的自动快照策略。|
|[DeleteAutoSnapshotPolicy](intl.zh-CN/API参考/快照/DeleteAutoSnapshotPolicy.md)|删除一条自动快照策略。如果目标自动快照策略已经被应用到磁盘上，删除自动快照策略后，这些磁盘不再执行该策略。|
|[DescribeAutoSnapshotPolicyEX](intl.zh-CN/API参考/快照/DescribeAutoSnapshotPolicyEX.md)|查询您已创建的自动快照策略。|
|[DescribeSnapshots](intl.zh-CN/API参考/快照/DescribeSnapshots.md)|查询一台ECS实例或一块磁盘设备所有的快照列表。InstanceId、DiskId和SnapshotIds不是必需参数，但是可以构建过滤器逻辑，参数之间为逻辑与（And）关系。|
|[DescribeSnapshotLinks](intl.zh-CN/API参考/快照/DescribeSnapshotLinks.md)|查询磁盘快照链。快照链是一个磁盘所有快照组成的关系链，一个磁盘对应一条快照链。|
|[ModifyAutoSnapshotPolicyEx](intl.zh-CN/API参考/快照/ModifyAutoSnapshotPolicyEx.md)|修改一条自动快照策略。修改自动快照策略后，之前已应用该策略的磁盘随即执行修改后的自动快照策略。|
|[DescribeSnapshotsUsage](intl.zh-CN/API参考/快照/DescribeSnapshotsUsage.md)|查询您在一个地域下的快照数量以及快照容量。如果您想知道当前地域下每块磁盘的快照使用情况，推荐使用 DescribeSnapshotLinks 查询磁盘快照链。|
|[DescribeSnapshotPackage](intl.zh-CN/API参考/快照/DescribeSnapshotPackage.md)|查询您在一个阿里云地域下已经购买了用于可以抵扣快照存储容量的对象存储OSS（存储包）。|

## 安全组 {#section_jf8_l64_log .section}

|API|描述|
|---|--|
|[ModifySecurityGroupEgressRule](intl.zh-CN/API参考/安全组/ModifySecurityGroupEgressRule.md)|修改安全组出方向规则的描述信息。如果您还没有增加过安全组规则，可以调用 AuthorizeSecurityGroupEgress 增加。|
|[CreateSecurityGroup](intl.zh-CN/API参考/安全组/CreateSecurityGroup.md)|新建一个安全组。新建的安全组，默认只允许安全组内实例互相访问，安全组外的一切通信请求会被拒绝。若您想允许其他安全组实例的通信请求，或者来自互联网的访问请求，需要授权安全组权限（AuthorizeSecurityGroup）。|
|[AuthorizeSecurityGroup](intl.zh-CN/API参考/安全组/AuthorizeSecurityGroup.md)|增加一条安全组入方向规则。指定安全组入方向的访问权限，允许或者拒绝其他设备发送入方向流量到安全组里的实例。|
|[AuthorizeSecurityGroupEgress](intl.zh-CN/API参考/安全组/AuthorizeSecurityGroupEgress.md)|增加一条安全组出方向规则。指定安全组出方向的访问权限，允许或者拒绝安全组里的实例发送出方向流量到其他设备。|
|[RevokeSecurityGroup](intl.zh-CN/API参考/安全组/RevokeSecurityGroup.md)|删除一条安全组入方向规则，撤销安全组入方向的权限设置。|
|[RevokeSecurityGroupEgress](intl.zh-CN/API参考/安全组/RevokeSecurityGroupEgress.md)|删除一条安全组出方向规则，撤销安全组出方向的访问权限。|
|[JoinSecurityGroup](intl.zh-CN/API参考/安全组/JoinSecurityGroup.md)|将一台实例加入到指定的安全组。|
|[LeaveSecurityGroup](intl.zh-CN/API参考/安全组/LeaveSecurityGroup.md)|将一台实例移出指定的安全组。|
|[DeleteSecurityGroup](intl.zh-CN/API参考/安全组/DeleteSecurityGroup.md)|删除一个安全组。删除安全组之前，请确保安全组内不存在实例，并且没有其他安全组与该安全组有授权行为（DescribeSecurityGroupReferences），否则 DeleteSecurityGroup 请求失败。|
|[DescribeSecurityGroupAttribute](intl.zh-CN/API参考/安全组/DescribeSecurityGroupAttribute.md)|查询安全组详情。|
|[DescribeSecurityGroups](intl.zh-CN/API参考/安全组/DescribeSecurityGroups.md)|查询您创建的安全组的基本信息，例如安全组ID和安全组描述等。返回列表按照安全组ID降序排列。|
|[DescribeSecurityGroupReferences](intl.zh-CN/API参考/安全组/DescribeSecurityGroupReferences.md)|查询一个安全组和其他哪些安全组有安全组级别的授权行为。|
|[ModifySecurityGroupAttribute](intl.zh-CN/API参考/安全组/ModifySecurityGroupAttribute.md)|修改指定安全组的属性，包括修改安全组名称和描述。|
|[ModifySecurityGroupPolicy](intl.zh-CN/API参考/安全组/ModifySecurityGroupPolicy.md)|修改安全组内网连通策略。|
|[ModifySecurityGroupRule](intl.zh-CN/API参考/安全组/ModifySecurityGroupRule.md)|修改安全组入方向规则的描述信息。如果您还没有增加过安全组规则，可以调用 AuthorizeSecurityGroup 增加。|

## 部署集 {#section_cpi_uva_ga4 .section}

|API|描述|
|---|--|
|[CreateDeploymentSet](intl.zh-CN/API参考/部署集/CreateDeploymentSet.md)|在指定的地域内创建一个部署集。|
|[ModifyInstanceDeployment](intl.zh-CN/API参考/部署集/ModifyInstanceDeployment.md)|在同一地域下，修改一台 ECS 实例的宿主机。|
|[ModifyDeploymentSetAttribute](intl.zh-CN/API参考/部署集/ModifyDeploymentSetAttribute.md)|修改一个部署集的名称和描述信息。|
|[DeleteDeploymentSet](intl.zh-CN/API参考/部署集/DeleteDeploymentSet.md)|删除一个部署集。|
|[DescribeDeploymentSets](intl.zh-CN/API参考/部署集/DescribeDeploymentSets.md)|查询一个或多个部署集的属性列表。|

## SSH 密钥对 {#section_2x5_hp3_lk2 .section}

|API|描述|
|---|--|
|[CreateKeyPair](intl.zh-CN/API参考/SSH 密钥对/CreateKeyPair.md)|创建一对SSH密钥对。我们会为您保管密钥的公钥部分，并返回未加密的 PEM 编码的 PKCS\#8 格式私钥。您需要自行妥善保管私钥部分。|
|[ImportKeyPair](intl.zh-CN/API参考/SSH 密钥对/ImportKeyPair.md)|导入由其他工具产生的 RSA 密钥对的公钥部分。导入密钥对后，我们会为您保管公钥部分，您需要自行妥善保存密钥对的私钥部分。|
|[AttachKeyPair](intl.zh-CN/API参考/SSH 密钥对/AttachKeyPair.md)|绑定一个 SSH 密钥对到一台或多台 Linux 实例。|
|[DetachKeyPair](intl.zh-CN/API参考/SSH 密钥对/DetachKeyPair.md)|为一台或者多台 Linux 实例解绑 SSH 密钥对。|
|[DeleteKeyPairs](intl.zh-CN/API参考/SSH 密钥对/DeleteKeyPairs.md)|删除一对或者多对 SSH 密钥对。删除 SSH 密钥对后，我们不再为您保存该 SSH 密钥对，但是已经绑定的实例可以正常使用该 SSH 密钥对，其 SSH 密钥对名称仍然显示在实例详情中。|
|[DescribeKeyPairs](intl.zh-CN/API参考/SSH 密钥对/DescribeKeyPairs.md)|查询一个或多个密钥对。|

## 网络 {#section_uxh_hxh_lyb .section}

|API|描述|
|---|--|
|[AllocatePublicIpAddress](intl.zh-CN/API参考/网络/AllocatePublicIpAddress.md)|为一台ECS实例分配一个公网IP地址。|
|[ConvertNatPublicIpToEip](intl.zh-CN/API参考/网络/ConvertNatPublicIpToEip.md)|将一台网络类型为专有网络VPC的ECS实例的公网 IP（NatPublicIp）转化为弹性公网IP（EIP）。|
|[AttachClassicLinkVpc](intl.zh-CN/API参考/网络/AttachClassicLinkVpc.md)|将一台经典网络类型实例连接到专有网络 VPC 中，使经典网络类型实例可以和 VPC 中的云资源私网互通。更多详情，请参阅 VPC 文档 ClassicLink 迁移概述。|
|[DetachClassicLinkVpc](intl.zh-CN/API参考/网络/DetachClassicLinkVpc.md)|取消经典网络类型实例与专有网络 VPC 的连接（ClassicLink）。更多详情，请参阅 VPC 文档 ClassicLink 迁移概述。取消 ClassicLink 后，经典网络类型实例无法与 VPC 互通。|
|[DescribeBandwidthLimitation](intl.zh-CN/API参考/网络/DescribeBandwidthLimitation.md)|查询带宽资源列表。|
|[DescribeClassicLinkInstances](intl.zh-CN/API参考/网络/DescribeClassicLinkInstances.md)|查询一台或多台与专有网络 VPC 建立了连接的经典网络类型实例。|
|[ModifyInstanceNetworkSpec](intl.zh-CN/API参考/网络/ModifyInstanceNetworkSpec.md)|修改实例的带宽配置。当实例现有网络规格不满足要求时，可以通过修改实例的带宽配置提高网络性能。|

## 弹性网卡 {#section_vx8_gtz_yjf .section}

|API|描述|
|---|--|
|[CreateNetworkInterface](intl.zh-CN/API参考/弹性网卡/CreateNetworkInterface.md)|创建一个弹性网卡（ENI）。|
|[AttachNetworkInterface](intl.zh-CN/API参考/弹性网卡/AttachNetworkInterface.md)|附加弹性网卡（ENI）到专有网络（VPC）类型实例上。|
|[AssignPrivateIpAddresses](intl.zh-CN/API参考/弹性网卡/AssignPrivateIpAddresses.md)|为一块弹性网卡分配一个或多个辅助私有IP地址。可以为网卡指定在所属虚拟交换机（VSwitch）的CIDR私有IP地址，或者通过指定私有网络地址数量自动创建私有IP地址。|
|[UnassignPrivateIpAddresses](intl.zh-CN/API参考/弹性网卡/UnassignPrivateIpAddresses.md)|从一块弹性网卡删除一个或多个辅助私有IP地址。|
|[DetachNetworkInterface](intl.zh-CN/API参考/弹性网卡/DetachNetworkInterface.md)|从一台实例上分离一个弹性网卡（ENI）。|
|[DeleteNetworkInterface](intl.zh-CN/API参考/弹性网卡/DeleteNetworkInterface.md)|删除弹性网卡（ENI）。|
|[DescribeNetworkInterfaces](intl.zh-CN/API参考/弹性网卡/DescribeNetworkInterfaces.md)|查看弹性网卡（ENI）列表。|
|[ModifyNetworkInterfaceAttribute](intl.zh-CN/API参考/弹性网卡/ModifyNetworkInterfaceAttribute.md)|修改一个弹性网卡（ENI）的属性。例如，弹性网卡名称、描述以及所属安全组等。|
|[AssignIpv6Addresses](intl.zh-CN/API参考/弹性网卡/AssignIpv6Addresses.md)|使用 AssignIpv6Addresses 为弹性网卡分配一个或多个 IPv6 地址。|
|[UnassignIpv6Addresses](intl.zh-CN/API参考/弹性网卡/UnassignIpv6Addresses.md)|若弹性网卡已被分配了 IPv6 地址，UnassignIpv6Addresses 可以回收一个或多个 IPv6 地址。|

## 系统事件 {#section_era_0mo_yvs .section}

|API|描述|
|---|--|
|[DescribeInstancesFullStatus](intl.zh-CN/API参考/系统事件/DescribeInstancesFullStatus.md)|查询一台或多台实例的全状态信息。全状态信息包括实例状态和实例事件状态，其中，实例状态为实例的生命周期状态，实例事件为维护事件的健康状态，更多详情，请参阅实例生命周期和实例系统事件。|
|[DescribeInstanceHistoryEvents](intl.zh-CN/API参考/系统事件/DescribeInstanceHistoryEvents.md)|查询指定实例的系统事件信息，默认查询处于非活跃状态的历史系统事件。目前，您最多可以查询最近一周的历史系统事件。通过指定InstanceEventCycleStatus参数，可以查询处于Scheduled（计划中）和Executing（执行中）状态的系统事件。|
|[DescribeDisksFullStatus](intl.zh-CN/API参考/系统事件/DescribeDisksFullStatus.md)|查询一块或多块磁盘的全部状态信息。|
|[CancelSimulatedSystemEvents](intl.zh-CN/API参考/系统事件/CancelSimulatedSystemEvents.md)|取消一件或多件处于Scheduled（计划中）或Executing（执行中）状态的模拟系统事件。取消系统事件后，模拟事件变为Canceled（已取消）状态。|
|[CreateSimulatedSystemEvents](intl.zh-CN/API参考/系统事件/CreateSimulatedSystemEvents.md)|为一台或多台ECS实例预约模拟系统事件。模拟系统事件相当于事件演习，不会真正执行事件，也不会对ECS实例产生影响。|

## 运维与监控 {#section_qha_80y_png .section}

|API|描述|
|---|--|
|[DescribeEniMonitorData](intl.zh-CN/API参考/运维与监控/DescribeEniMonitorData.md)|查询一块辅助网卡在指定时间段内使用的流量信息。|
|[DescribeDiskMonitorData](intl.zh-CN/API参考/运维与监控/DescribeDiskMonitorData.md)|查询一块磁盘指定时间内的使用信息。可查询磁盘实用信息包括读 IOPS、写 IOPS、读带宽（Bps）、写带宽（Bps）、读延时（ms）以及写延时（ms）。若查询的信息中出现内容缺失，是因为我们无法获取该段时间的使用信息，即磁盘状态不是使用中（In\_Use）。|
|[DescribeInstanceMonitorData](intl.zh-CN/API参考/运维与监控/DescribeInstanceMonitorData.md)|查询一台 ECS 实例所有相关的监控信息。返回的监控内容包括 ECS 实例的 CPU 使用率、接收的数据流量、发送的数据流量、网络流量、平均带宽。当返回信息中缺少部分内容时，可能是由于系统没有获取到相应的信息，比如当时实例处于已停止（Stopped）状态。|
|[GetInstanceScreenshot](intl.zh-CN/API参考/运维与监控/GetInstanceScreenshot.md)|获取实例的截屏信息。|
|[GetInstanceConsoleOutput](intl.zh-CN/API参考/运维与监控/GetInstanceConsoleOutput.md)|获取一台实例的系统命令行输出，数据以Base64编码后返回。|

## 云助手 {#section_nds_h39_z6y .section}

|API|描述|
|---|--|
|[CreateCommand](intl.zh-CN/API参考/云助手/CreateCommand.md)|新建一条云助手命令。|
|[InstallCloudAssistant](intl.zh-CN/API参考/云助手/InstallCloudAssistant.md)|为一台或多台实例安装云助手客户端。|
|[InvokeCommand](intl.zh-CN/API参考/云助手/InvokeCommand.md)|为一台或多台ECS实例触发一条云助手命令。|
|[StopInvocation](intl.zh-CN/API参考/云助手/StopInvocation.md)|停止一台或多台ECS实例中一条正在进行中（Running）的云助手命令进程。|
|[DeleteCommand](intl.zh-CN/API参考/云助手/DeleteCommand.md)|删除一条云助手命令。|
|[DescribeCloudAssistantStatus](intl.zh-CN/API参考/云助手/DescribeCloudAssistantStatus.md)|查询一台或者多台实例是否安装了云助手客户端。|
|[DescribeCommands](intl.zh-CN/API参考/云助手/DescribeCommands.md)|查询您已经创建的云助手命令。只输入参数 Action 和 RegionId，不输入其他任何请求参数，则默认查询您所有可用的命令（CommandId）。|
|[DescribeInvocations](intl.zh-CN/API参考/云助手/DescribeInvocations.md)|查询云助手命令的执行列表和状态。|
|[DescribeInvocationResults](intl.zh-CN/API参考/云助手/DescribeInvocationResults.md)|查看云助手命令的执行结果，在指定ECS实例中的实际执行结果。|

## 标签 {#section_79i_o7d_zum .section}

|API|描述|
|---|--|
|[TagResources](intl.zh-CN/API参考/标签/TagResources.md)|为指定的ECS资源列表统一创建并绑定标签。|
|[ListTagResources](intl.zh-CN/API参考/标签/ListTagResources.md)|查询一个或多个ECS资源已经绑定的标签列表。|
|[UntagResources](intl.zh-CN/API参考/标签/UntagResources.md)|为指定的ECS资源列表统一解绑并删除标签。|

## 地域 {#section_ykr_fmw_kcg .section}

|API|描述|
|---|--|
|[DescribeRegions](intl.zh-CN/API参考/地域/DescribeRegions.md)|查询您可以使用的阿里云地域。|
|[DescribeZones](intl.zh-CN/API参考/地域/DescribeZones.md)|查询一个阿里云地域下的可用区。|
|[DescribeResourcesModification](intl.zh-CN/API参考/地域/DescribeResourcesModification.md)|查询升级和降配实例规格或者系统盘时，某一可用区的可用资源信息。|
|[DescribeAvailableResource](intl.zh-CN/API参考/地域/DescribeAvailableResource.md)|查询某一可用区的资源列表。例如，您可以在某一可用区创建实例（RunInstances）或者修改实例规格（ModifyInstanceSpec）时查询该可用区的资源列表。|

## 其他接口 {#section_lip_cie_w96 .section}

|API|描述|
|---|--|
|[CancelTask](intl.zh-CN/API参考/其他接口/CancelTask.md)|取消一件正在运行的任务。目前，您能取消正在运行的导入镜像任务（ImportImage）和导出镜像任务（ExportImage）。|
|[DescribeTasks](intl.zh-CN/API参考/其他接口/DescribeTasks.md)|查询一个或多个异步请求的进度。|
|[DescribeTaskAttribute](intl.zh-CN/API参考/其他接口/DescribeTaskAttribute.md)|查询异步任务的详细信息。目前，可以查询的异步任务有导入镜像（ImportImage）和导出镜像（ExportImage）两种。|
|[DescribeAccountAttributes](intl.zh-CN/API参考/DescribeAccountAttributes.md)|查询您在一个阿里云地域下能创建的ECS资源上限。包括您能创建的安全组数量、弹性网卡数量、按量付费vCPU核数、抢占式实例vCPU核数、专用宿主机数量、地域网络类型以及账号是否已完成实名认证。|
|[DescribePrice](intl.zh-CN/API参考/其他接口/DescribePrice.md)|查询云服务器 ECS 资源的最新价格。|

