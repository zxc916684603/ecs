# Add a host to the ext VDS {#task_ct4_hj1_hgb .task}

This topic describes how to add a host to the ext vSphere Distributed Switch \(VDS\).

1.  You have created an ext-VDS.
2.  You have logged on to the Windows instance on which vCenter is installed.
3.  You have logged on to vCenter Server.
4.  You have recorded the vmnic corresponding to the ext ENI of the host that provides network management utilities. For more information, see [Obtain information about the ENIs and their vmnics](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS bare metal instances/Preparations/Obtain information about the ENIs and their vmnics.md#).

1.  Log on to **vSphere Web Client**. In the left-side navigation pane, click **ext-vds**, and then choose **Actions** \> **Add and Manage Hosts**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85000/154886377036553_en-US.png) 
2.   On the Select task page, select **Add hosts**, and then click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154886377035573_en-US.png)

 
3.   On the **Select hosts** page, click **New hosts**, select the IP address of the host that provides network management utilities, and then click **OK**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154886377035574_en-US.png)

 
4.   On the Select hosts page, you can see the host selected in the previous step. Click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154886377035575_en-US.png)

 
5.   On the Select network adapter tasks page, select **Manage physical adapters** and **Manage VMkernel adapters**, and then click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154886377035576_en-US.png)

 
6.   On the Manage physical network adapters page, select the vmnic corresponding to the ext ENI of the host with network management utilities. Then assign this vmnic to the uplink on the ext VDS.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85000/154886377038007_en-US.png)

 
7.   \(Optional\) On the Manage VMkernel network adapters page, add a VMKernel adapter, and then click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154886377035578_en-US.png)

 
8.   Confirm the possible impact of the change on some network dependent services, and then click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154886377035579_en-US.png)

 
9.   On the Ready to complete page, confirm your settings, and then click Finish.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154886377035580_en-US.png)

 

