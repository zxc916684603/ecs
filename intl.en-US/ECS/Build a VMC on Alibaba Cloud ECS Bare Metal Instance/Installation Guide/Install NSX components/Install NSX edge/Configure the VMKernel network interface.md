# Configure the VMKernel network interface {#task_ilh_jz1_hgb .task}

This topic describes how to configure the VMKernel network interface for NSX Edge.

Log on to the Windows instance where VMware vCenter Server is installed.

1.  Log on to VMware vSphere Web Client. 
2.  Right-click the NSX Edge appliance, and then click **Edit settings...**. 
3.  Clear the two redundant default network adapters. 
4.  Change the settings of the other two network adapters. 

    1.  From the **New adapter 1** drop-down list, select **Show more networks...**. 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85018/154859248935938_en-US.png)

    2.  Select **ext-DPortGroup**, and then click **OK**. 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85018/154859248935939_en-US.png)

    3.  Add vtep-DPortGroup by following the preceding steps. 
    The two network adapters are configured as follows.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85018/154859248935942_en-US.png)

5.  From the **New device** drop-down list, select **PCI device** to add a PCI device to the NSX Edge appliance. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85018/154859248935943_en-US.png)

    Check the [ENI Mapping to Vmnic](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS Bare Metal Instance/Preparation/ENI Mapping to Vmnic.md#) to select the secondary management ENI assigned to NSX Edge duing the NSX Edge installation.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85018/154859248935945_en-US.png)

6.  Follow [ENI Mapping to Vmnic](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS Bare Metal Instance/Preparation/ENI Mapping to Vmnic.md#) to obtain the correct MAC addresses of the vtep uplink port and the ext uplink port, and then change the MAC address of the two VMKernel network adapters. 
    1.  Expand **Network adapter 1**, and then select **Manual** to change the **MAC Address**. 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85018/154859248935949_en-US.png)

    2.  Change the MAC address of the other network adapter by following the previous step. 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85018/154859248935954_en-US.png)

7.   Reboot the host that provides network management utilities to make the change of MAC address take effect.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85018/154859248936870_en-US.png)

 

