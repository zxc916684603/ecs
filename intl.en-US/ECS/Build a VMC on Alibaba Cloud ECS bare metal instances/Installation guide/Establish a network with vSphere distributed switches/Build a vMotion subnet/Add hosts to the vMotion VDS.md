# Add hosts to the vMotion VDS {#task_wyj_r5s_ggb .task}

This topic describes how to add two ESXi hosts to the newly created vMotion vSphere Distributed Switch \(VDS\).

1.  Log on to vCenter Server. 
2.  Record the vmnics that correspond to the vMotion ENIs of all hosts. For more information, see [Obtain information about the ENIs and their vmnics](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS bare metal instances/Preparations/Obtain information about the ENIs and their vmnics.md#) 
3.  In the left-side navigation pane, select the newly created vMotion VDS, and then choose **Actions** \> **Add and Manage Hosts...**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83715/154886333135592_en-US.png)

4.  Select **Add hosts**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83715/154886333135593_en-US.png)

5.  Select both ESXi hosts, and then click **OK**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83715/154886333135594_en-US.png)

6.  Select **Manage physical adapters** and **Manage VMkernel adapters**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83715/154886333135595_en-US.png)

7.  On the Manage physical network adapters page, select the vmnic corresponding to the vMotion ENI of the host with network management utilities. Then, assign this vmnic to the uplink on the vMotion VDS.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83715/154886333138002_en-US.png)

 
8.  For the other host, select the vmnic that corresponds to the vMotion ENI of this host, and then assign this vmnic to the uplink on the vMotion VDS. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83715/154886333138003_en-US.png)

9.  Add a vMotion VMkernel adapter to the host that provides network management utilities. 
    1.  Click **New adapter**. 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83715/154886333235601_en-US.png)

    2.  Select the network. 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83715/154886333235602_en-US.png)

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83715/154886333235603_en-US.png)

    3.  Set the port properties and select **vMotion**. 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83715/154886333235605_en-US.png)

    4.  Select **Obtain IPv4 settings automatically**. 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83715/154886333235606_en-US.png)

    5.  Confirm your settings. 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83715/154886333235607_en-US.png)

10. Repeat the previous step to add a vMotion VMkernel adapter to the other ESXi host. ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83715/154886333235608_en-US.png)

 
11. Confirm the possible impacts. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83715/154886333235609_en-US.png)

12. Confirm your settings, and then click **Finish**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83715/154886333235610_en-US.png)


