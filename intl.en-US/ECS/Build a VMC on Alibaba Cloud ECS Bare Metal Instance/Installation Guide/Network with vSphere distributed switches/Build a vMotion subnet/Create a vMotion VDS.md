# Create a vMotion VDS {#task_vzy_yqz_ggb .task}

This topic describes how to create a vMotion Virtual Distributed Switch \(VDS\).

1.  Log on to vCenter Server. 
2.  Select **Actions** \> **Distributed Switch** \> **New Distributed Switch**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84632/154857725135546_en-US.png)

3.  In the **Name** text box, enter a name for the new vSphere distributed switch. In this example, vmotion-vds is used. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84632/154857725135548_en-US.png)

4.  Select **Distributed switch 6.5.0**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84632/154857725135549_en-US.png)

5.  Select the **Number of uplinks** and select the **Default port group**. 

    **Note:** Uplink ports connect the distributed switch to physical NICs on the associated hosts. The number of uplink ports is the maximum number of allowed physical connections to the distributed switch of each host.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84632/154857725135550_en-US.png)

6.  Enter a name for the port group and click **Next**. 
7.  Confirm the settings, and then click **Finish**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84632/154857725135551_en-US.png)


