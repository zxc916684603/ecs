# Create a host transport node {#task_tj1_mct_lgb .task}

A transport node is a node that is added to an NSX-T overlay network or NSX-T VLAN network. This topic describes how to create a host transport node through the NSX Manager GUI.

-   The host must be joined with the management plane, and **Manager connectivity** must be Up on the **Fabric** \> **Hosts** page.
-   A transport zone must be configured.
-   You can configure an uplink profile. If no uplink profile is configured, a default uplink profile is used.
-   An IP pool must be configured, or DHCP must be available in the network deployment.
-   At least one unused physical NIC must be available on the host node.

1.  Enter `https://<nsx-manager-ip-address>` in your browser and log on to NSX Manager with your admin privileges. 
2.   Select **Fabric** \> **Nodes** \> **Transport Nodes**, and then click **Add**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85013/154865199936057_en-US.png)

 
3.  Set the details of the transport node in the Add Transport Node dialog box. 
    1.  On the **General** tab page, enter a name for the transport node.
    2.  Select a node from the drop-down list.
    3.  Select the transport zones to which this transport node belongs.
        -   For this example, you can add the host transport node to the overlay network. The general settings of the host that provides network management utilities are shown in the following figure:

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85013/154865199936058_en-US.png)

        -   The general settings of the other host are shown in the following figure.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85013/154865200036061_en-US.png)

    4.  Click the **N-VDS**tab. On the **N-VDS** tab page, the N-VDS type is selected as Standard by default.
    5.  For a standard N-VDS, provide the following details:
        -   Select the N-VDS name from the drop-down list. The name must be the same as the N-VDS name of the transport zone that this node belongs to.
        -   Select the NIOC profile from the drop-down list.
        -   Select the uplink profile from the drop-down list.
        -   Select Use DHCP from the **IP Assignment** drop-down list
        -   Select the physical NIC that you want to configure as uplink-1 port. The uplink-1 port is defined in the uplink profile.

            **Note:** The physical NIC must not be in use, for example, by a standard vSwitch or a vSphere distributed switch when you perform the preceding configuration. Otherwise, the transport node will remain in the partial success status, and the control plane connectivity of the NSX-T Data Center on the fabric node will fail to be established.

            -   In this example, for the host that provides network management utilities, the N-VDS switch of the overlay network is configured with an uplink \(uplink-1\) mapped to vmnic2. Check the [ENI Mapping to Vmnic](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS Bare Metal Instances/Preparation/ENI Mapping to Vmnic.md#) and select vmnic2 and uplink-1 from the drop-down lists.

                ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85013/154865200036059_en-US.png)

            -   To add the other host transport node to the overlay network, configure the N-VDS switch with an uplink \(uplink-1\) mapped to vmnic1. Check the [ENI Mapping to Vmnic](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS Bare Metal Instances/Preparation/ENI Mapping to Vmnic.md#) and select vmnic1and uplink-1 from the drop-down lists.

                ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85013/154865200036062_en-US.png)


