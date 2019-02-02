# Configure the VMKernel network interface {#task_cdg_lz1_hgb .task}

This topic describes how to configure the VMKernel network interface for NSX Controller.

1.  Log on to VMware vSphere Web Client. 
2.   In the **Hosts and Clusters** navigation pane, right-click the NSX Controller appliance, and then click **Edit Settings...**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85021/154886393836646_en-US.png)

 
3.   Clear the invalid network adapter.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85021/154886393835857_en-US.png)

 
4.  Add a PCI device to NSX Controller. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85021/154886393835858_en-US.png)

5.   Select the secondary management ENI assigned to NSX Controller during the NSX Controller installation. For more information, see [Obtain information about the ENIs and their vmnics](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS bare metal instances/Preparations/Obtain information about the ENIs and their vmnics.md#).![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85021/154886393835860_en-US.png)

 

