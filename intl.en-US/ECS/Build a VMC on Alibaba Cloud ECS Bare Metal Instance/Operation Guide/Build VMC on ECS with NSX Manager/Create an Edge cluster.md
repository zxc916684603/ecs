# Create an Edge cluster {#task_dfy_ghz_lgb .task}

This topic describes how to create an Edge cluster. To create a tier-0 logical router or a tier-1 logical router with stateful services, such as NAT and load balancer, you need to associate the router with an NSX Edge cluster.

-   Install at least one NSX Edge node.
-   Join the NSX Edges with the management plane.
-   Add the NSX Edges as transport nodes.

1.  Enter `https://<nsx-manager-ip-address>` in your browser and log on to NSX Manager with your admin privileges. 
2.  Select **Fabric** \> **Nodes** \> **Edge Clusters**, and click **Add**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85016/154857794836008_en-US.png)

 
3.  Enter a name for the NSX Edge cluster. 
4.  \(Optional\) Enter a description for the NSX Edge cluster. 
5.  Select an Edge cluster profile from the drop-down list. 
6.  Click **Edit** and select Virtual Machine. 
7.  Select Edge Node from the **Member Type** drop-down list. 
8.  From the **Available** list, select the NSX Edge and move it to the **Selected** list.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85016/154857794837521_en-US.png)

 
9.  Click **OK**. 

