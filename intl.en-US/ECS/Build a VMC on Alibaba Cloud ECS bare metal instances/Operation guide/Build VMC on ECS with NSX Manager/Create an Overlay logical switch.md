# Create an Overlay logical switch {#task_gyp_ktg_4gb .task}

This topic describes how to create an overlay logical switch. A logical switch is used to connect virtual machines to hypervisor hosts so that the machines and hosts can use tunneling protocols for secure communication.

-   You have configured a transport zone.
-   You have connected the fabric nodes to the Management Plane Agent \(MPA\) and the Local Control Plane \(LCP\) of the NSX-T Data Center.
-   You have added the transport nodes to the transport zone.
-   You have added the hypervisor hosts to the NSX-T Data Center fabric, and have hosted the virtual machines on these hypervisor hosts.
-   You have verified that your NSX Controller cluster is stable.

1.  Enter `https://nsx-manager-ip-address` in your browser and log on to NSX Manager with your admin privileges. 
2.   Choose **Switching** \> **Switches**, and click **Add**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85004/154886426436086_en-US.png)

 
3.  Enter a name for the logical switch. 
4.  \(Optional\) Enter a description for the logical switch. 
5.  Select a transport zone for the logical switch. 

    **Note:** If the virtual machines attached to the logical switch are in the same transport zone, these VMs can communicate with each other.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85004/154886426436087_en-US.png)

6.  Select Use Default as the uplink teaming policy. 
7.  Set the **Admin Status** to Up. 
8.  Select a replication mode for the logical switch. 

    |Replication Mode|Description|
    |----------------|-----------|
    |Hierarchical Two-Tier|     -   The replicator is a host that replicates broadcast traffic, unknown unicast traffic, and multicast \(BUM\) traffic to other hosts within the same Virtual Network Identifier \(VNI\).
    -   Each host nominates one host tunnel endpoint in every VNI to be the replicator. This is done for each VNI.
 |
    |Head|Hosts create a copy of each BUM frame and send the copy to each tunnel endpoint in each VNI.|

    **Note:** The replication mode \(Hierarchical Two-Tier replication or Head replication\) is required for overlay logical switches, but not required for VLAN-based logical switches.

9.  \(Optional\) Specify a VLAN ID or ranges of VLAN IDs for VLAN tagging. To support guest VLAN tagging for VMs connected to this switch, you must specify VLAN ID ranges, which are also called trunk VLAN ID ranges. The logical port will filter packets based on the trunk VLAN ID ranges, and a guest VM can tag its packets with its own VLAN ID based on the trunk VLAN ID ranges.
10. \(Optional\) Click the **Switching Profiles** tab and select switching profiles. 
11. Click **Save**. 

