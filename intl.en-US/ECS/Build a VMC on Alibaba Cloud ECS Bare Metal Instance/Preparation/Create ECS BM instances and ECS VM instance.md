# Create ECS BM instances and ECS VM instance {#task_qv3_n5s_ggb .task}

The topic describes how to create an ECS Windows instance and 2 bare-metal instances in the Alibaba Cloud ECS console.

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#home). 
2.  In the left-side navigation pane, click **Instances**. 
3.  On the **Instances** list page, click **Create Instance**. 
4.  Refer to the [Create an instance by using the wizard](../../../../../intl.en-US/User Guide/Instances/Create an instance/Create an instance by using the wizard.md#) for configuration details. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83714/154858223835460_en-US.png)

    To keep the configuration consistent in this tutorial, the specified configuration settings as follows:

    |Attribute|Setting|
    |:--------|:------|
    |Region|China East 2 \(Shanghai\)|
    |Zone|China East 2 Zone E|
    |Instance Type|ecs.g5.2xlarge|
    |Images|WINDOWS SERVER data center 2016|
    |System Disk|Cloud SSD \(100 GiB\)|
    |VPC|The VPC "vmware-on-xdragon" created in the [Prepare network](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS Bare Metal Instance/Preparation/Prepare network.md#) topic.|
    |VSwitch|The VSwitch "management" created in the [Prepare network](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS Bare Metal Instance/Preparation/Prepare network.md#) topic.|
    |Assign public IP?|Yes|

    |Attribute|Setting|
    |:--------|:------|
    |Region|China East 2 \(Shanghai\)|
    |Zone|China East 2 Zone E|
    |Instance type|ecs.ebmg5.24xlarge|
    |Images|The ESXi 6.5 custom image that created in the [Create ESXi custom image](intl.en-US/ECS/Folder1/Create an ESXi image.md#) topic.|
    |System disk|Cloud SSD \(40 GiB\)|
    |Data disk|Cloud SSD \(100 GiB\)|
    |VPC|The VPC "vmware-on-xdragon" created in the [Prepare network](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS Bare Metal Instance/Preparation/Prepare network.md#) topic.|
    |VSwitch|The VSwitch "management" created in the [Prepare network](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS Bare Metal Instance/Preparation/Prepare network.md#) topic.|

    |Attribute|Setting|
    |:--------|:------|
    |Region|China East 2 \(Shanghai\)|
    |Zone|China East 2 Zone E|
    |Instance type|ecs.ebmg5.24xlarge|
    |Images|The ESXi 6.5 custom image created in the [Create ESXi custom image](intl.en-US/ECS/Folder1/Create an ESXi image.md#) topic.|
    |System disk|Cloud SSD \(40 GiB\)|
    |Data disk|Cloud SSD \(100 GiB\)|
    |VPC|The VPC "vmware-on-xdragon"created in the [Prepare network](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS Bare Metal Instance/Preparation/Prepare network.md#) topic.|
    |VSwitch|The VSwitch "management" created in the [Prepare network](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS Bare Metal Instance/Preparation/Prepare network.md#) topic.|


