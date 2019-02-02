# Configure the VMKernel network interface {#task_ilh_jz1_hgb .task}

This topic describes how to configure the VMKernel network interface for NSX Edge.

You have logged on to the Windows instance where VMware vCenter Server is installed.

1.  Log on to VMware vSphere Web Client. 
2.  Right-click the NSX Edge appliance, and then click **Edit settings...**. 
3.  Clear the two redundant default network adapters. 
4.  Change the settings of the other two network adapters. 

    1.  From the **New adapter 1** drop-down list, select **Show more networks...**. 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85018/154886402735938_en-US.png)

    2.  Select **ext-DPortGroup**, and then click **OK**. 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85018/154886402735939_en-US.png)

    3.  Add vtep-DPortGroup by following the preceding steps. 
    The two network adapters are configured as follows.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85018/154886402735942_en-US.png)

5.  From the **New device** drop-down list, select **PCI device** to add a PCI device to the NSX Edge appliance. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85018/154886402735943_en-US.png)

    Select the secondary management ENI assigned to NSX Edge during the NSX Edge installation. For more information, see [Obtain information about the ENIs and their vmnics](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS bare metal instances/Preparations/Obtain information about the ENIs and their vmnics.md#).

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85018/154886402735945_en-US.png)

6.  Follow [Obtain information about the ENIs and their vmnics](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS bare metal instances/Preparations/Obtain information about the ENIs and their vmnics.md#) to obtain the correct MAC addresses of the vtep uplink port and the ext uplink port. Then, change the MAC address of the two VMKernel network adapters. 
    1.  Expand **Network adapter 1**, and then select **Manual** to change the **MAC Address**. 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85018/154886402735949_en-US.png)

    2.  Change the MAC address of the other network adapter by following the previous step. 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85018/154886402835954_en-US.png)

7.   Restart the host that provides network management utilities to validate the MAC address change.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85018/154886402836870_en-US.png)

 

