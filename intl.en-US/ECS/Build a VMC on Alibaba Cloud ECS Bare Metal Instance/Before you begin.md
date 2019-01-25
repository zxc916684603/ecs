# Before you begin {#concept_k34_sts_ggb .concept}

This topic describes how to build a VMware Cloud \(VMC\) on an ECS Bare Metal Instance.

## Networking mode {#section_szx_h1t_ggb .section}

In this example, network virtualization is implemented for the ECS Bare Metal Instance through overlay networking. Specifically, an Alibaba Cloud VPC acts as a layer-three IP network, and NSX is used to control the VMC network.

**Advantages of overlay networks:**

-   Supports features such as VMware vMotion and VMware DRS.
-   On-premises VMCs can be migrated to a cloud, or combined with existing on-premises VMCs to form a hybrid cloud.
-   It allows you to connect to the Internet, build public clouds, and provide external services.

## Network planning {#section_sx1_kdt_ggb .section}

In this example, one ECS instance and two ECS Bare Metal Instances are used. Specifically:

-   One ECS instance used for vCenter implementation.
-   One ECS Bare Metal Instance used for ESXi host implementation. It acts as both the network node \(for deploying the NSX component\), and as the compute node \(for deploying the VMC VM component\).
-   The other ECS Bare Metal Instance is used for ESXi host implementation. It acts as the compute node.

The detailed network architecture is shown in the following diagram:

![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83708/154841183038165_en-US.png)

In the architecture shown above, five Virtual Switches \(vSwitches\) are deployed to provide network connectivity to ESXi hosts and VMC VM network. The following table describes the major nodes.

|Node|Description|
|:---|:----------|
|VMC host networking|VSW \(management subnet\)|Handles management layer packets. Each ESXi host and the NSX components \(NSX-manager/NSX-controller/NSX-edge\) must connect to this VSW. Specifically, NSX-manager, NSX-controller, and NSX-edge are connected to this VSW in the form of ENI passthrough.|
|VSW \(vmotion subnet\)|Used for VMC VM vMotion.|
|VMC VM networking|VSW \(vtep\_overlay subnet\)|Handles VMC VM east-to-west \(E-W\) packets. Any ESXi host that acts as a compute node must connect to this VSW through an ENI. NSX-edge also needs to connect to this VSW through an ENI.|
|VSW \(ext subnet\)|Handles VMC VM north-to-south \(N-S\) packets. NSX-edge needs to connect to this VSW through an ENI.|
|VSW \( ecsvm subnet\)|Handles the connection to ECS VMs.|
|vRouter|Handles VMC VM north-to-south \(N-S\) packets, and accessing Alibaba Cloud services such as RDS, NFS, and ECS.|
|XGW|Handles VMC VM north-to-south \(N-S\) packets.|
|IPSec VPN|Connects the control layer and data layer between a public cloud and a Customer VMC.|
|ENI|Assigned as an uplink port for an ESXi host or NSX-manager,NSX-controller, NSX-edge.|

