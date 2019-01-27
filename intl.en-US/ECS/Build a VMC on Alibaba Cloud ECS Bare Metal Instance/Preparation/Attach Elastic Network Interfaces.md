# Attach Elastic Network Interfaces {#task_wng_dlc_ggb .task}

The topic describes attaching secondary network interfaces to bare-metal servers.

You must create a specified quantity of ENIs in the ECS console. In this topic, 9 ENIs must be created and secured by the VSwitches that you launched in the [Prepare network](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS Bare Metal Instance/Preparation/Prepare network.md#) topic.

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home).
2.  In the left-side navigation pane, select **Networks and Security** \> **ENI**.
3.  Select a region.

    **Note:** The region must be identical to where the bare-metal servers belong.

4.  Click **Create ENI**.
5.  Refer to the document [Create an ENI](../../../../../intl.en-US/User Guide/Elastic Network Interfaces/Create an ENI.md#) for configuration details. To keep the configuration consistent in this tutorial, configuration settings are specified as follows:

    |Attribute|Setting|
    |:--------|:------|
    |VPC|The VPC "vmware-on-xdragon" created in the [Prepare network](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS Bare Metal Instance/Preparation/Prepare network.md#) topic.|
    |VSwitch|The VSwitch created in the [Prepare network](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS Bare Metal Instance/Preparation/Prepare network.md#) topic.**Note:** For more information about the number of ENIs and the VSwitches name , see [Background information](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS Bare Metal Instance/Preparation/Attach Elastic Network Interfaces.md#context_mbn_szx_ggb).

|
    |Security Group|The security group selected in the [Prepare network](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS Bare Metal Instance/Preparation/Prepare network.md#) topic.|

    After you complete the operation, 9 ENIs are created with the following **ID/Name**, and the ENIs are all controlled by the same VPC \(**vmware-on-xdragon**\).

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83055/154857519735504_en-US.png)


The following table describes how ENIs are used:

|VSwitch name|Functions|Number of required ENIs|Assigned network segments|
|:-----------|:--------|:----------------------|:------------------------|
|Management|Three secondary management ENIs are assigned to the host that provides network management utilities, to work as the uplink port for each NSX component.|3|192.168.10.0/24|
|Vtep|Two vtep ENIs are assigned to the host that provides network utilities, and one vtep ENI is assigned to the other host. For internal NSX-T tunneling between transport nodes, the vtep ENIs provide the east-west network connectivity.|3|192.168.40.0/24|
|Vmotion|Each ESXi host has a vmotion ENI to work as an uplink port for vmotion subnet that enables the live migration for the VMC VM.|2|192.168.20.0/24|
|EXT|The NSX Edge installed on the host that provides network management utilities requires an ext ENI to work as a VLAN uplink.|1|192.168.50.0/24|

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home). 
2.  In the left-side navigation pane, select **Networks and Security** \> **ENI**. 
3.  Locates the previously created ENI, in the **Action** column, click **Bind to Instance**. 
4.  At the **Select Instance** entry, choose the ESXi host, and click **OK**. 

    The following table lists how the 9 ENIs are allocated:

    |ESXi host|ENI name|ENI quantity|
    |:--------|:-------|:-----------|
    |Network node and compute node|management|3|
    |vtep|2|
    |vmotion|1|
    |ext|1|
    |Compute node|vtep|1|
    |vmotion|1|


