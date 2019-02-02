# Join a VMC VM with an ECS instance {#task_my3_tvs_ggb .task}

This topic describes how to join a VMC VM with an Alibaba Cloud ECS instance. By enabling intranet communication between ECS instances and VMC VMs launched from the ESXi host, you can benefit from the gigabyte tier of shared bandwidth established in Alibaba Cloud.

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/#/home). 
2.  In the left-side navigation pane, click **Instances**. 
3.  In the upper-right corner of the page, select a region as needed, and then click **Create Instance**. 

    **Note:** In this example, **China \(Shanghai\)** is selected as the target region because the ESXi hosts are located in the same region.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83729/154886463736261_en-US.png)

    **Note:** In this topic, only conditional configurations are described. For more information, see [Create an instance by using the wizard](../../../../../intl.en-US/User Guide/Instances/Create an instance/Create an instance by using the wizard.md#).

4.  Set the parameters on the **Networking \(Required\)** page as follows: 
    1.  Use the VPC and VSwitch that you created previously in [Prepare network](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS bare metal instances/Preparations/Prepare network.md#). In this example, the vmware-on-xdragon VPC and the ecsvm VSwitch are used.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83729/154886463736262_en-US.png)

    2.  Enable the **Assign public IP** feature.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83729/154886463736263_en-US.png)

5.  Enter `https://nsx-manager-ip-address>` in your browser and log on to NSX Manager with your admin privileges. 
6.  In the left-side navigation pane, choose **Routing** \> **Routers** \> **tier1** \> **Services** \> **NAT**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83729/154886463736264_en-US.png)

7.  Add the NAT service for the tier-1 router as follows: 
    1.  Click **ADD**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83729/154886463736265_en-US.png)

    2.  On the New NAT Rule page, set **Action** to NO\_SNAT, set the **Source IP** to the IP address of the VMC VM, set the **Destination IP** to the private IP address of the ECS instance, and then click **SAVE**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83729/154886463736266_en-US.png)

8.  Add a static route for the tier-1 router as follows: 
    1.  In the left-side navigation pane, select **Routing** \> **Routers** \> **tier1** \> **Configuration**, and then obtain the IP address of the tier-1 router uplink \(100.64.32.1 in this example\).

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83729/154886463736267_en-US.png)

    2.  In the left-side navigation pane, select **Routing** \> **Routers** \> **tier0** \> **Routing** \> **Static Routers** \> **ADD**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83729/154886463836268_en-US.png)

    3.  On the Add Static Route page, set **Network** to the source IP address specified in step 7, set **Next Hop** to the IP address obtained from the previous step, and then click **ADD**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83729/154886463836269_en-US.png)

9.  Log on to the [Alibaba Cloud VPC console](https://vpc.console.aliyun.com/vpc/cn-shanghai/vpcs). 
10. In the left-side navigation pane, select **Route Tables** \> **Create Route Tables**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83729/154886463836270_en-US.png)

11. Find the VPC in which the ESXi hosts are located, and then click **Manage**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83729/154886463836271_en-US.png)

12. Click **Add Route Entry**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83729/154886463836272_en-US.png)

13. On the Add Route Entry page, set the required fields. 

    -   **Destination CIDR Block**: Enter the private IP address of your VMC VM.
    -   **Next Hops Type**: Select Secondary NetworkInterface.
    -   **Secondary NetworkInterface**: Select the eni-ext ENI.
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83729/154886463836273_en-US.png)

14. Connect to the VMC VM. 
15. Ping the ECS VM to verify the connection. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83729/154886463836275_en-US.png)


