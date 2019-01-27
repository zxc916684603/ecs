# Create an Overlay logical switch {#task_gyp_ktg_4gb .task}

This topic describes how to create an overlay logical switch. A logical switch is used to connect virtual machines to hypervisor hosts so that the machines and hosts can use tunneling protocols for secure communication.

Prerequisites

-   A transport zone has been configured.
-   The fabric nodes to the Management Plane Agent \(MPA\) and the Local Control Plane \(LCP\) of the NSX-T Data Center have been connected.
-   The transport nodes have been added to the transport zone.
-   The hypervisor hosts have been added to the NSX-T Data Center fabric, and the virtual machines have been hosted on these hypervisor hosts.
-   Your NSX Controller cluster has been verified as stable.

1.  Enter `https://nsx-manager-ip-address` in your browser and log on to NSX Manager with your admin privileges. 
2.   Select **Switching** \> **Switches**, and click **Add**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85004/154857796336086_en-US.png)

 
3.  Enter a name for the logical switch. 
4.  \(Optional\) Enter a description for the logical switch. 
5.  Select a transport zone for the logical switch. 

    **说明：** If the virtual machines attached to the logical switch are in the same transport zone, these VMs can communicate with each other.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85004/154857796336087_en-US.png)

6.  Select Use Default as the uplink teaming policy. 
7.  Set the **Admin Status** to Up. 
8.  Select a replication mode for the logical switch. 

    |Replication Mode|Description|
    |----------------|-----------|
    |Hierarchical Two-Tier|     -   The replicator is a host that replicates broadcast traffic, unknown unicast traffic, and multicast \(BUM\) traffic to other hosts within the same Virtual Network Identifier \(VNI\).
    -   Each host nominates one host tunnel endpoint in every VNI to be the replicator. This is done for each VNI.
 |
    |Head|Hosts create a copy of each BUM frame and send the copy to each tunnel endpoint in each VNI.|

    **说明：** The replication mode \(Hierarchical Two-Tier replication or Head replication\) is required for overlay logical switches, but not required for VLAN-based logical switches.

9.  \(Optional\) Specify a VLAN ID or ranges of VLAN IDs for VLAN tagging. To support guest VLAN tagging for VMs connected to this switch, you must specify VLAN ID ranges, which are also called trunk VLAN ID ranges. The logical port will filter packets based on the trunk VLAN ID ranges, and a guest VM can tag its packets with its own VLAN ID based on the trunk VLAN ID ranges.
10. \(Optional\) Click the **Switching Profiles** tab and select switching profiles. 
11. Click **Save**. 

