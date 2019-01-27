# Create a VLAN Logical Switch {#task_u35_mct_lgb .task}

This topic describes how to create a VLAN logical switch. A logical switch is used to connect virtual machines to hypervisor hosts so that the machines and hosts can use tunneling protocols for secure communication. Edge uplinks go out through VLAN logical switches.

-   A VLAN transport zone has been configured.
-   The fabric nodes to the Management Plane Agent \(MPA\) and the Local Control Plane \(LCP\) of the NSX-T Data Center have been connected.
-   The transport nodes have been added to the transport zone.
-   The hypervisor hosts have been added to the NSX-T Data Center fabric, and the virtual machines have been hosted on these hypervisor hosts.
-   Your NSX Controller cluster has been verified as stable.

1.  Enter `https://nsx-manager-ip-address` in your browser and log on to NSX Manager with your admin privileges. 
2.   Select **Switching** \> **Switches**, and click **Add**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85004/154857808036086_en-US.png)

 
3.  Specify a name for the logical switch. 
4.  \(Optional\) Enter a description for the logical switch. 
5.  Select the VLAN transport zone for the logical switch. 

    **说明：** If the virtual machines attached to the logical switch are in the same transport zone, these VMs can communicate with each other.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/119753/154857808038089_en-US.png)

6.  Select Use Default as the uplink teaming policy. 
7.  Set the **Admin Status** to Up. 
8.  Both replication modes are not required for the VLAN logical switch. 
9.  Specify the VLAN ID to 0 for VLAN tagging. To support guest VLAN tagging for VMs connected to this switch, you must specify VLAN ID ranges, which are also called trunk VLAN ID ranges. The logical port will filter packets based on the trunk VLAN ID ranges, and a guest VM can tag its packets with its own VLAN ID based on the trunk VLAN ID ranges.
10. \(Optional\) Click the **Switching Profiles** tab and select switching profiles. 
11. Click **Add**. 

