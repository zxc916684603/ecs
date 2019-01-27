# Create a vtep VDS {#task_iyb_qc1_hgb .task}

This topic describes how to create a vtep vSphere Distributed Switch \(VDS\).

1.  Log on to the Windows instance on which vCenter Server is installed.
2.  Log on to **vSphere Web Client**.

1.   In the left-side navigation pane, click **vmc-xdragon**, and then click **Actions** \> **Distributed Switch** \> **New Distributed Switch**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154857731435566_en-US.png)

 
2.   In the **Name** text box, enter a name for the new VDS. In this example, vtep-vds is used.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154857731535567_en-US.png)

 
3.   On the Select version page, select **Distributed switch: 6.5.0**, and then click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154857731535569_en-US.png)

 
4.   Select the **Number of uplinks** and select the **Default port group**. Uplink ports connect the distributed switch to physical NICs on associated hosts. The number of uplink ports is the maximum number of allowed physical connections to the distributed switch of each host.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154857731535570_en-US.png)

 
5.  Enter a name for the port group, and then click **Next**. 
6.   On the Ready to complete page, confirm your settings, and then click **Finish**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84968/154857731535571_en-US.png)

 

