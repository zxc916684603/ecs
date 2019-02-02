# Create a tier-0 logical router {#task_f2g_d5t_lgb .task}

This topic describes how to create a tier-0 logical router. Tier-0 logical routers provide downlink ports to connect to tier-1 logical routers and provide uplink ports to connect to external networks.

-   You have installed at least one NSX Edge.
-   Your NSX Controller cluster is stable.
-   You have configured an NSX Edge cluster.

1.  Enter `https://nsx-manager-ip-address` in your browser and log on to NSX Manager with your admin privileges. 
2.   Choose **Routing** \> **Routers**, and then click **Add** \> **Tier-0 Router**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85005/154886437136108_en-US.png)

 
3.  Enter a name and description for the logical router. 
4.  Select an Edge cluster from the drop-down list. 
5.  \(Optional\) Select a high availability mode, for example, **Active-Standby**, as shown in the following figure. 

    **Note:** In **Active-Active** mode, traffic is load balanced across all members. In **Active-Standby** mode, all traffic is processed by the selected active member and in the case that the active member fails, another member is selected to be active.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85005/154886437136109_en-US.png)

6.  \(Optional\) When configuring **Active-Standby**, you need to select a failover mode. The following table describes the failover mode options. 

    |Option|Description|
    |------|-----------|
    |Preemptive|This is the default setting. If the preferred node fails and recovers, it will preempt its peer to become the active node. At the same time, its peer will enter standby.|
    |Non-preemptive|If the preferred node fails and recovers, it will check whether its peer is the active node, and in the case that its peer is in an active mode, the preferred node will not preempt, staying in standby.|

7.  \(Optional\) Select a preferred member from the drop-down list, for example, nsx-edge. 

    **Note:** If you do not select a preferred member, the first selected Edge cluster member will be automatically set as the preferred member.

8.  \(Optional\) Click the **Advanced** tab, and then enter a subnet for the intra-tier-0 transit subnet. 

    **Note:** The transit subnet connects the tier-0 service router to the distributed router of the transit subnet. If you leave this field blank, the default 169.0.0.0/28 subnet will be used.

9.  \(Optional\) On the **Advanced** tab, enter a subnet for the tier 0-to-tier 1 transit subnet. 

    **Note:** The transit subnet connects the tier-0 router to any tier-1 router that connects to this tier-0 router. If you leave this field blank, the default address space assigned for these tier 0-to-tier 1 connections will be 100.64.0.0/10. Each tier 0-to-tier 1 peer connection is provided with a /31 subnet within the 100.64.0.0/10 address space.

10. Click **Save**. 

