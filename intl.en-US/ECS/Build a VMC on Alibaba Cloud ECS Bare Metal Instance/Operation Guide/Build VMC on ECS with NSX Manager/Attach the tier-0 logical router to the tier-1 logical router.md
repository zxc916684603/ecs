# Attach the tier-0 logical router to the tier-1 logical router {#task_ox5_j5t_lgb .task}

This topic describes how to attach the tier-0 logical router to the tier-1 logical router. This ensures that the tier-1 logical router receives northbound and east-west network connectivity.

1.  Enter `https://nsx-manager-ip-address` in your browser and log on to NSX Manager with your admin privileges. 
2.  Select **Routing** \> **Routers**, and then select the tier-1 logical router. 
3.  On the **Overview** tab page, click **CONNECT** in the **Tier-0 Connection** field.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85005/154857840536110_en-US.png)

 
4.  Click the **Configuration** tab. In the **Logical Router Ports** list, verify that a router-link switch between the two routers has been created.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/104642/154857840537596_en-US.png)

 

    This switch is labeled as system-generated in the topology. The default address space assigned for this tier 0-to-tier 1 connection is 100.64.0.0/10. Each tier 0-to-tier 1 peer connection is provided with a /31 subnet within the 100.64.0.0/10 address space.


