# Add Hosts to the ext vSphere Distributed Switch {#task_ct4_hj1_hgb .task}

This topic introduces the steps to add a host to the ext vSphere Distributed Switch.

1.  You have created a ext-VDS.
2.  Log on to the Windows instance on which the vCenter has been installed.
3.  Log on to the vCenter Server.
4.  Check the [ENI Mapping to Vmnic](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS Bare Metal Instance/Preparation/ENI Mapping to Vmnic.md#) and record the vmnic that corresponds to the ext ENI of the host that provides network management utilities.

1.   Log on to the **vSphere Web Client**. In the left-side navigation pane, click **ext-vds**, and then click **Actions** \> **Add and Manage Hosts**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85000/154858190736553_en-US.png) 
2.   On the Select task page, select **Add hosts**, and then click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154858190735573_en-US.png)

 
3.   On the **Select hosts** page, click **New hosts**, check the IP of the host that provides network management utilities, and then click **OK**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154858190835574_en-US.png)

 
4.   On the Select hosts page, you can see the host checked in the previous step. Click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154858190835575_en-US.png)

 
5.   On the Select network adapter tasks page, check**Manage physical adapters** and **Manage VMkernel adapters**, as shown in the following figure. Click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154858190835576_en-US.png)

 
6.   On the Manage physical network adapters page, select the vmnic that corresponds to the ext ENI of the host that provides network management utilities, and assign this vmnic to the uplink on the ext VDS.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85000/154858190838007_en-US.png)

 
7.   On the Manage VMkernel network adapters page, you can choose to add a VMKernel adapter now or later. Click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154858190835578_en-US.png)

 
8.   Review whether this configuration change might impact some network dependent services. Click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154858190835579_en-US.png)

 
9.   On the Ready to complete page, you can view the details of your configurations. Click Finish to confirm the configurations.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154858190835580_en-US.png)

 

