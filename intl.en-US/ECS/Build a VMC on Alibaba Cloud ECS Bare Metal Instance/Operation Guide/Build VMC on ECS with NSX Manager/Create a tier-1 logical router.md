# Create a tier-1 logical router {#task_k2x_b5t_lgb .task}

This topic describes how to create a tier-1 logical router.

1.  Enter `https://nsx-manager-ip-address` in your browser and log on to NSX Manager with you admin privileges. 
2.   Select **Routing** \> **Routers**, and then click **Add** \> **Tier-1 Router**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85005/154857834536106_en-US.png)

 
3.  Enter a name and description for the logical router. 
4.  \(Optional\) Select a tier-0 logical router and connect it to this tier-1 logical router. 

    **Note:** You can either configure a tier-0 logical router now or leave this field blank and configure a router at a later time.

5.  \(Optional\) Select an NSX Edge cluster and connect it to this tier-1 logical router. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85005/154857834536107_en-US.png)

    **Note:** If you want to use the tier-1 logical router for Network Address Translation \(NAT\) configuration, you need to connect the tier-1 logical router to an NSX Edge cluster. Otherwise, if you have yet to configure a NSX Edge cluster, you can either configure one now or leave this field blank and edit the router configuration at a later time.

6.  \(Optional\) When configuring an NSX Edge cluster, you need to select a failover mode. The following table describes the failover mode options. 

    |Option|Description|
    |------|-----------|
    |Preemptive|This is the default setting. If the preferred node fails and recovers, it will preempt its peer to become the active node. At the same time, its peer will enter standby.|
    |Non-preemptive|If the preferred node fails and recovers, it will check whether its peer is the active node, and in the case that its peer is in active mode, the preferred node will not preempt its peer, staying in standby.|

7.  \(Optional\) Click the **Advanced** tab and enter a value for **Intra Tier-1 Transit Subnet**. 
8.  Click **Add**. 

