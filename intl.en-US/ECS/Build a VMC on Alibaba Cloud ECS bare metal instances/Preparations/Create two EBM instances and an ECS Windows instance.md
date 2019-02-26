# Create two EBM instances and an ECS Windows instance {#task_qv3_n5s_ggb .task}

This topic describes how to create an ECS Windows instance and two ECS Bare Metal \(EBM\) instances in the Alibaba Cloud ECS console.

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#home). 
2.  In the left-side navigation pane, click **Instances**. 
3.  On the **Instances** page, click **Create Instance**. 
4.  Set the parameters. For more information, see [Create an instance by using the wizard](../../../../../reseller.en-US/Instances/ECS instance life cycle/Create an instance/Create an instance by using the wizard.md#). 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83714/155116294335460_en-US.png)

    To be consistent with in this tutorial, use the settings specified in the following three tables.

    |Attribute|Setting|
    |:--------|:------|
    |Region|China East 2 \(Shanghai\)|
    |Zone|China East 2 Zone E|
    |Instance Type|ecs.g5.2xlarge|
    |Images|WINDOWS SERVER data center 2016|
    |System Disk|Cloud SSD \(100 GiB\)|
    |VPC|The VPC "vmware-on-xdragon" created in the [Prepare network](reseller.en-US/ECS/Build a VMC on Alibaba Cloud ECS bare metal instances/Preparations/Prepare the network.md#) topic|
    |VSwitch|The VSwitch "management" created in the [Prepare network](reseller.en-US/ECS/Build a VMC on Alibaba Cloud ECS bare metal instances/Preparations/Prepare the network.md#) topic|
    |Assign public IP?|Yes|

    |Attribute|Setting|
    |:--------|:------|
    |Region|China East 2 \(Shanghai\)|
    |Zone|China East 2 Zone E|
    |Instance type|ecs.ebmg5.24xlarge|
    |Images|The ESXi 6.5 custom image that created in the Create ESXi custom image topic|
    |System disk|Cloud SSD \(40 GiB\)|
    |Data disk|Cloud SSD \(100 GiB\)|
    |VPC|The VPC "vmware-on-xdragon" created in the [Prepare network](reseller.en-US/ECS/Build a VMC on Alibaba Cloud ECS bare metal instances/Preparations/Prepare the network.md#) topic|
    |VSwitch|The VSwitch "management" created in the [Prepare network](reseller.en-US/ECS/Build a VMC on Alibaba Cloud ECS bare metal instances/Preparations/Prepare the network.md#) topic|

    |Attribute|Setting|
    |:--------|:------|
    |Region|China East 2 \(Shanghai\)|
    |Zone|China East 2 Zone E|
    |Instance type|ecs.ebmg5.24xlarge|
    |Images|The ESXi 6.5 custom image created in the Create ESXi custom image topic|
    |System disk|Cloud SSD \(40 GiB\)|
    |Data disk|Cloud SSD \(100 GiB\)|
    |VPC|The VPC "vmware-on-xdragon"created in the [Prepare network](reseller.en-US/ECS/Build a VMC on Alibaba Cloud ECS bare metal instances/Preparations/Prepare the network.md#) topic|
    |VSwitch|The VSwitch "management" created in the [Prepare network](reseller.en-US/ECS/Build a VMC on Alibaba Cloud ECS bare metal instances/Preparations/Prepare the network.md#) topic|


