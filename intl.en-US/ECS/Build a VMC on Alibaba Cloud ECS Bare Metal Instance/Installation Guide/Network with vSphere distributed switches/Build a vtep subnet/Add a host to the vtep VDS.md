# Add a host to the vtep VDS {#task_ct4_hj1_hgb .task}

This topic describes how to add a host to the vtep vSphere Distributed Switch \(VDS\).

1.  Create a vtep-VDS.
2.  Log on to the Windows instance on which the vCenter is installed.
3.  Log on to vCenter Server.
4.  Check the [ENI Mapping to Vmnic](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS Bare Metal Instance/Preparation/ENI Mapping to Vmnic.md#) and record the vmnics that correspond to the two vtep ENIs of the host that provides network management utilities.

1.  Log on to the **vSphere Web Client**. 
2.   In the left-side navigation pane, click **vtep-vds**, and then click **Actions** \> **Add and Manage Hosts**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154857734935572_en-US.png)

 
3.   On the Select task page, select **Add hosts**, and then click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154857734935573_en-US.png)

 
4.   On the **Select hosts** page, click **New hosts**, check the IP of the host that provides network management utilities, and then click **OK**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154857734935574_en-US.png)

 
5.   On the Select hosts page, you can see the host checked in the previous step. Click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154857735035575_en-US.png)

 
6.   On the Select network adapter tasks page, select **Manage physical adapters** and **Manage VMkernel adapters**, and then click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154857735035576_en-US.png)

 
7.   On the Manage physical network adapters page, select either of the vmnics corresponding to two vtep ENIs of the host that provides network management utilities, and assign this vmnic to the uplink on the vtep VDS.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84992/154857735038005_en-US.png)

 
8.   \(Optional\) On the Manage VMkernel network adapters page, add a VMkernel adapter, and then click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154857735035578_en-US.png)

 
9.   Confirm the impact of this change on some network dependent services, and then click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154857735035579_en-US.png)

 
10.  On the Ready to complete page, confirm your settings, and then click Finish.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154857735035580_en-US.png)

 

