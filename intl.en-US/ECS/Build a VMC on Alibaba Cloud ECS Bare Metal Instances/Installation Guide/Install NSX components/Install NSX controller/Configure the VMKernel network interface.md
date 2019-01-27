# Configure the VMKernel network interface {#task_cdg_lz1_hgb .task}

This topic describes how to configure the VMKernel network interface for NSX Controller.

1.  Log on to VMware vSphere Web Client. 
2.   In the **Hosts and Clusters** navigation pane, right-click the NSX Controller appliance, and then click **Edit Settings...**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85021/154859482936646_en-US.png)

 
3.   Clear the invalid network adapter.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85021/154859482935857_en-US.png)

 
4.  Add a PCI device to NSX Controller. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85021/154859483035858_en-US.png)

5.   Check the [ENI Mapping to Vmnic](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS Bare Metal Instances/Preparation/ENI Mapping to Vmnic.md#) to select the secondary management ENI assigned to NSX Controller duing the NSX Controller installation.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85021/154859483035860_en-US.png)

 

