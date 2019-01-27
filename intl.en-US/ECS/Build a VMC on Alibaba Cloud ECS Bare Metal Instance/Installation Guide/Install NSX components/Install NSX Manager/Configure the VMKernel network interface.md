# Configure the VMKernel network interface {#task_f1r_2vs_ggb .task}

This topic describes how to configure the VMKernel network interface for NSX Manager.

-   Log on to the Windows instance where VMware vCenter Server is installed.
-   Log on to VMware vSphere Web Client.

1.  In the left-side navigation pane, right- click the target NSX Manager, and choose **Edit Settings**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83725/154857748836908_en-US.png)

2.  Clear the redundant default network adapter.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84983/154857748835891_en-US.png)

 
3.  From the **New device** drop-down menu, select **PCI device** to add a PCI device to the NSX Manager appliance. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85018/154857748835943_en-US.png)

    Check the [ENI Mapping to Vmnic](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS Bare Metal Instance/Preparation/ENI Mapping to Vmnic.md#) to select the secondary management ENI assigned to NSX Manager during the NSX Manager installation.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83725/154857748837964_en-US.png)


