# Create a VLAN logical switch {#task_u35_mct_lgb .task}

This topic describes how to create a VLAN logical switch. A logical switch is used to connect virtual machines to hypervisor hosts so that the machines and hosts can use tunneling protocols for secure communication. Edge uplinks go out through VLAN logical switches.

-   You have configured a VLAN transport zone.
-   You have connected the fabric nodes to the Management Plane Agent \(MPA\) and the Local Control Plane \(LCP\) of the NSX-T Data Center.
-   You have added the transport nodes to the transport zone.
-   You have added the hypervisor hosts to the NSX-T Data Center fabric, and have hosted the virtual machines on these hypervisor hosts.
-   You have verified that your NSX Controller cluster is stable.

1.  Enter `https://nsx-manager-ip-address` in your browser and log on to NSX Manager with your admin privileges. 
2.   Choose **Switching** \> **Switches**, and click **Add**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85004/154886428436086_en-US.png)

 
3.  Specify a name for the logical switch. 
4.  \(Optional\) Enter a description for the logical switch. 
5.  Select the VLAN transport zone for the logical switch. 

    **Note:** If the virtual machines attached to the logical switch are in the same transport zone, these VMs can communicate with each other.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/119753/154886428538089_en-US.png)

6.  Select Use Default as the uplink teaming policy. 
7.  Set the **Admin Status** to Up. 
8.  Both replication modes are not required for the VLAN logical switch. 
9.  Specify the VLAN ID to 0 for VLAN tagging. To support guest VLAN tagging for VMs connected to this switch, you must specify VLAN ID ranges, which are also called trunk VLAN ID ranges. The logical port will filter packets based on the trunk VLAN ID ranges, and a guest VM can tag its packets with its own VLAN ID based on the trunk VLAN ID ranges.
10. \(Optional\) Click the **Switching Profiles** tab and select switching profiles. 
11. Click **Add**. 

