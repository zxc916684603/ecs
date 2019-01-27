# Create an uplink profile {#task_n2k_jct_lgb .task}

An uplink profile defines policies for the links from hypervisor hosts to NSX-T logical switches, or from NSX Edge nodes to top-of-rack \(ToR\) switches.

-   Familiarize yourself with NSX Edge networking.
-   Each uplink in the uplink profile must correspond to an up and available physical link on your hypervisor host or on the NSX Edge node.

1.  Enter `https://<nsx-manager-ip-address>` in your browser and log on to NSX Manager with your admin privileges. 
2.  Select **Fabric** \> **Profiles** \> **Uplink Profiles**, and then click **Add**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85013/154857787036051_en-US.png)

 
3.  Set the uplink profile details. 

    -   Enter an uplink profile name.
    -   Enter an optional uplink profile description.
    -   In the **Teaming** section, click **Add** and enter the details. The teaming policy determines how the N-VDS uses its uplink for redundancy and traffic load balancing. In this example, the Failover Order teaming policy mode is set to configure the teaming policy. An active uplink is specified along with an optional list of standby uplinks. If the active uplink fails, the next uplink in the standby list replaces the active uplink. No actual load balancing is performed with this option. In this example, an active uplink named uplink-1is specified.
    -   Set the transport VLAN value to 0.
    -   Specify the MTU value less or equal to 1500.
    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85013/154857787036052_en-US.png)


