# Attach elastic network interfaces {#task_wng_dlc_ggb .task}

The topic describes how to attach secondary Elastic Network Interfaces \(ENIs\) to the bare metal servers.

You have created a specified quantity of ENIs in the ECS console. In this example, nine ENIs are created and secured by the VSwitches launched in [Prepare the network](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS bare metal instances/Preparations/Prepare network.md#).

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home). 
2.  In the left-side navigation pane, choose **Networks and Security** \> **ENI**. 
3.  Select a region. 

    **Note:** The region must be the same as the region to which the bare metal servers belong.

4.  Click **Create ENI**. 
5.  Set the parameters. For more information, see [Create an ENI](../../../../../intl.en-US/User Guide/Elastic Network Interfaces/Create an ENI.md#). To be consistent with this tutorial, use the settings specified in the following table. 

    |Attribute|Setting|
    |:--------|:------|
    |VPC|The VPC "vmware-on-xdragon" created in [Prepare the network](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS bare metal instances/Preparations/Prepare network.md#).|
    |VSwitch|The VSwitch created in the [Prepare the network](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS bare metal instances/Preparations/Prepare network.md#) topic.**Note:** For more information about the number of ENIs and the VSwitch names, see [Background information](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS bare metal instances/Preparations/Attach elastic network interfaces.md#context_mbn_szx_ggb).

|
    |Security Group|The security group selected in the [Prepare the network](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS bare metal instances/Preparations/Prepare network.md#) topic.|

    Nine ENIs are created. The ENIs are all controlled by the same VPC \(**vmware-on-xdragon**\).

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83055/154886275535504_en-US.png)

    The following table describes the functions of these ENIs.

    |VSwitch|Function|Number of required ENIs|Assigned network segments|
    |:------|:-------|:----------------------|:------------------------|
    |Management|Three secondary management ENIs are assigned to the host that provides network management utilities. These ENIs work as uplink ports for each NSX component.|3|192.168.10.0/24|
    |Vtep|Two vtep ENIs are assigned to the host that provides network utilities, and one vtep ENI is assigned to the other host. For internal NSX-T tunneling between transport nodes, the vtep ENIs provide the east-west network connectivity.|3|192.168.40.0/24|
    |Vmotion|Each ESXi host has a vmotion ENI to work as an uplink port for vmotion subnet that enables the live migration for the VMC VM.|2|192.168.20.0/24|
    |EXT|NSX Edge installed on the host that provides network management utilities requires an ext ENI to work as a VLAN uplink.|1|192.168.50.0/24|

6.  Locate the previously created ENI, and then click **Bind to Instance** in the **Action** column. 
7.  At the **Select Instance** entry, choose the ESXi host, and click **OK**. 

    The following table describes how these nine ENIs are allocated.

    |ESXi host|ENI name|ENI quantity|
    |:--------|:-------|:-----------|
    |Network node and compute node|management|3|
    |vtep|2|
    |vmotion|1|
    |ext|1|
    |Compute node|vtep|1|
    |vmotion|1|


