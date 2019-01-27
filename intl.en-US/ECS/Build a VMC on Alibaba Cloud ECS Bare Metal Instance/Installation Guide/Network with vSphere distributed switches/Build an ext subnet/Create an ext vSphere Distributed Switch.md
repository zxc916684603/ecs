# Create an ext vSphere Distributed Switch {#task_pvh_py1_hgb .task}

This topic describes the steps to create an ext vSphere Distributed Switch.

1.  Log on to the Windows instance on which the vCenter Server has been installed.
2.  Log on to the **vSphere Web Client**.

1.  In the left-side navigation pane, click **vmc-xdragon**, and then click **Actions** \> **Distributed Switch** \> **New Distributed Switch**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84998/154858254436545_en-US.png)

 
2.  In the **Name** text box, type a name for the new vSphere distributed switch. In this example, ext-vds is used.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84998/154858254436546_en-US.png)

 
3.  On the Select version page, select **Distributed switch: 6.5.0**, and then click **Next**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84998/154858254436547_en-US.png)

 
4.   Use the arrow buttons to select the Number of uplinks and check the Default port group. Uplink ports connect the distributed switch to physical NICs on associated hosts. The number of uplink ports is the maximum number of allowed physical connections to the distributed switch per host.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84998/154858254436548_en-US.png)

 
5.  Enter a name for the port group and click **Next**. 
6.  On the Ready to complete page, check your settings. Click **Finish** to confirm the settings.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84998/154858254436549_en-US.png)

 

