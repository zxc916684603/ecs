# Configure the VMKernel network interface {#task_f1r_2vs_ggb .task}

This topic describes how to configure the VMKernel network interface for NSX Manager.

-   You have logged on to the Windows instance where VMware vCenter Server is installed.
-   You have logged on to VMware vSphere Web Client.

1.  In the left-side navigation pane, right-click the target NSX Manager, and then click **Edit Settings**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83725/154886384036908_en-US.png)

2.  Clear the redundant default network adapter.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84983/154886384135891_en-US.png)

 
3.  From the **New device** drop-down list, select **PCI device** to add a PCI device to the NSX Manager appliance. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85018/154886384135943_en-US.png)

    Select the secondary management ENI assigned to NSX Manager during the NSX Manager installation. For more information, see [Obtain information about the ENIs and their vmnics](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS bare metal instances/Preparations/Obtain information about the ENIs and their vmnics.md#).

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83725/154886384137964_en-US.png)


