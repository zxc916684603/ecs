# Add a host to the vtep VDS {#task_ct4_hj1_hgb .task}

This topic describes how to add a host to the vtep vSphere Distributed Switch \(VDS\).

1.  You have created a vtep-VDS.
2.  You have logged on to the Windows instance on which vCenter Server is installed.
3.  You have logged on to vCenter Server.
4.  You have recorded the vmnics corresponding to the two vtep ENIs of the host with network management utilities. For more information, see [Obtain information about the ENIs and their vmnics](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS bare metal instances/Preparations/Obtain information about the ENIs and their vmnics.md#).

1.  Log on to **vSphere Web Client**. 
2.   In the left-side navigation pane, click **vtep-vds**, and then choose **Actions** \> **Add and Manage Hosts**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154886344735572_en-US.png)

 
3.   On the Select task page, select **Add hosts**, and then click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154886344735573_en-US.png)

 
4.   On the **Select hosts** page, click **New hosts**, select the IP address of the host with network management utilities, and then click **OK**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154886344735574_en-US.png)

 
5.   On the Select hosts page, you can see the host selected in the previous step. Click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154886344735575_en-US.png)

 
6.   On the Select network adapter tasks page, select **Manage physical adapters** and **Manage VMkernel adapters**, and then click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154886344835576_en-US.png)

 
7.   On the Manage physical network adapters page, select either of the vmnics corresponding to two vtep ENIs of the host with network management utilities. Then, assign this vmnic to the uplink on the vtep VDS.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84992/154886344838005_en-US.png)

 
8.   \(Optional\) On the Manage VMkernel network adapters page, add a VMkernel adapter, and then click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154886344835578_en-US.png)

 
9.   Confirm the impact of this change on some network dependent services, and then click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154886344835579_en-US.png)

 
10.  On the Ready to complete page, confirm your settings, and then click Finish.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154886344835580_en-US.png)

 

