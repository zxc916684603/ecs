# Before you begin {#concept_twr_plj_pgb .concept}

This topic describes how to build a VMware Cloud \(VMC\) on an ECS bare metal instance.

## Networking mode {#section_uwr_plj_pgb .section}

In this example, network virtualization is implemented for the ECS bare metal instance through overlay networking. Specifically, an Alibaba Cloud VPC acts as a layer-three IP network, and NSX is used to control the VMC network.

**Advantages of overlay networks:**

-   Supports features such as VMware vMotion and VMware DRS.
-   On-premises VMCs can be migrated to a cloud, or combined with existing on-premises VMCs to form a hybrid cloud.

## Network planning {#section_wwr_plj_pgb .section}

In this example, one ECS instance and two ECS bare metal instances are used. Specifically:

-   One ECS instance used for vCenter implementation.
-   One ECS bare metal instance used for ESXi host implementation. It acts as both the network node \(for deploying the NSX component\), and as the compute node \(for deploying the VMC VM component\).
-   The other ECS bare metal instance is used for ESXi host implementation. It acts as the compute node.

The network architecture is shown in the following figure.

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83708/155921978238165_en-US.png)

In the network architecture, five Virtual Switches \(vSwitches\) are deployed to provide network connectivity to ESXi hosts and VMC VM network. The following table describes the major nodes.

|Node|Description|
|:---|:----------|
|VMC host networking|VSW \(management subnet\)|Handles management layer packets. Each ESXi host and the NSX components \(NSX Manager/NSX Controller/NSX Edge\) must connect to this VSW. Specifically, NSX Manager, NSX Controller, and NSX Edge are connected to this VSW in the form of ENI passthrough.|
|VSW \(vMotion subnet\)|Used for VMC VM vMotion.|
|VMC VM networking|VSW \(vtep\_overlay subnet\)|Handles VMC VM east-to-west \(E-W\) packets. Any ESXi host that acts as a compute node must connect to this VSW through an ENI. NSX Edge also needs to connect to this VSW through an ENI.|
|VSW \(ext subnet\)|Handles VMC VM north-to-south \(N-S\) packets. NSX Edge needs to connect to this VSW through an ENI.|
|VSW \( ecsvm subnet\)|Handles the connection to ECS VMs.|
|vRouter|Handles VMC VM north-to-south \(N-S\) packets, and accessing Alibaba Cloud services such as RDS, NFS, and ECS.|
|XGW|Handles VMC VM north-to-south \(N-S\) packets.|
|IPSec VPN|Connects the control layer and data layer between a public cloud and a Customer VMC.|
|ENI|Assigned as an uplink port for an ESXi host or NSX Manager, NSX Controller, and NSX Edge.|

