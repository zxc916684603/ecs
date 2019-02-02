# Create an NSX Edge transport node {#task_y4x_sl2_kgb .task}

A transport node is a node that is capable of participating in an NSX-T Data Center overlay or NSX-T Data Center VLAN networking. An NSX Edge can belong to one overlay transport zone and multiple VLAN transport zones. This topic describes how to add an NSX Edge as a transport node.

-   You have joined NSX Edge with the management plane.
-   You have configured transport zones.
-   You have configured an uplink profile, or you can use the default uplink profile for bare metal NSX Edge nodes.
-   You have configured an IP pool, or DHCP is available in the network deployment.
-   At least one unused physical NIC is available on the host or NSX Edge node.

1.  Enter `https://<nsx-manager-ip-address>` in your browser and log on to NSX Manager with your admin privileges. 
2.  Choose **Fabric** \> **Nodes** \> **Transport Nodes**, and then click **Add**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85013/154886420936057_en-US.png)

 
3.  Set the details of the transport node in the Add Transport Node dialog box. 
    1.  On the **General** tab page, enter a name for the transport node.
    2.  Select a node from the drop-down list.
    3.  Select the transport zones to which this transport node belongs. For this example, you can add the NSX Edge transport node to the overlay network and the VLAN network. The general settings of the NSX Edge node are shown in the following figure.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85013/154886420936067_en-US.png)

    4.  Click the **N-VDS**tab. On the **N-VDS** tab page, the N-VDS type is selected as Standard by default.
    5.  For a standard N-VDS, provide the following details:
        -   Select the N-VDS name from the drop-down list. The name must be the same as the N-VDS name of the transport zone that this node belongs to.
        -   Select the NIOC profile from the drop-down list.
        -   Select the uplink profile from the drop-down list.
        -   Select Use Static IP List from the **IP Assignment** drop-down list. The IP address list, the gateway, and the subnet mask are shown in the following figure.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85013/154886420936068_en-US.png)

        -   Select the physical NIC that you want to configure as uplink-1 port. The uplink-1 port is defined in the uplink profile.

            **Note:** The physical NIC must not be in use, for example, by a standard vSwitch or a vSphere distributed switch when you perform the preceding configuration. Otherwise, the transport node will remain in the partial success status, and the control plane connectivity of the NSX-T Data Center on the fabric node will fail to be established.

            In this example, to add the NSX Edge transport node to the overlay network and the VLAN network, select port fp-eth0 \(the physical uplink vmnic4 of the ext vSphere distributed switch\) for the VLAN uplink.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85013/154886420936070_en-US.png)

            Select port fp-eth1 for the overlay uplink \(the physical uplink vmnic2 of the vtep vSphere distributed switch\).

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85013/154886420936068_en-US.png)


