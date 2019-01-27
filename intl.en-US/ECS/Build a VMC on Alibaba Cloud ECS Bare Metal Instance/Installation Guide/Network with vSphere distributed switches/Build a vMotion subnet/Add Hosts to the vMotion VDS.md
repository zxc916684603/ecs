# Add Hosts to the vMotion VDS {#task_wyj_r5s_ggb .task}

This topic describes how to add two ESXi hosts to the newly created vMotion vSphere Distributed Switch \(VDS\).

1.  Log on to vCenter Server. 
2.  Check the [ENI Mapping to Vmnic](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS Bare Metal Instance/Preparation/ENI Mapping to Vmnic.md#) and record the vmnics that correspond to the vMotion ENIs of all hosts. 
3.  In the left-side navigation pane, select the newly created vMotion VDS, and then click **Actions** \> **Add and Manage Hosts...**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83715/154857726735592_en-US.png)

4.  Select **Add hosts**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83715/154857726735593_en-US.png)

5.  Select both ESXi hosts, and then click **OK**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83715/154857726735594_en-US.png)

6.  Select **Manage physical adapters** and **Manage VMkernel adapters**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83715/154857726735595_en-US.png)

7.   On the Manage physical network adapters page, select the vmnic corresponding to the vMotion ENI of the host that provides network management utilities, and then assign this vmnic to the uplink on the vMotion VDS.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83715/154857726738002_en-US.png)

 
8.  For the other host, select the vmnic that corresponds to the vMotion ENI of this host, and then assign this vmnic to the uplink on the vMotion VDS. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83715/154857726738003_en-US.png)

9.  Add a vMotion VMkernel adapter to the host that provides network management utilities. 
    1.  Click **New adapter**. 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83715/154857726735601_en-US.png)

    2.  Select the network. 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83715/154857726735602_en-US.png)

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83715/154857726735603_en-US.png)

    3.  Set the port properties and select **vMotion**. 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83715/154857726735605_en-US.png)

    4.  Select **Obtain IPv4 settings automatically**. 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83715/154857726735606_en-US.png)

    5.  Confirm the settings. 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83715/154857726735607_en-US.png)

10. Repeat the previous step to add a vMotion VMkernel adapter to the other ESXi host. ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83715/154857726835608_en-US.png)

 
11. Confirm the possible impacts. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83715/154857726835609_en-US.png)

12. Confirm the settings, and then click **Finish**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83715/154857726835610_en-US.png)


