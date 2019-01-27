# Create transport zones {#task_yzm_5xs_lgb .task}

A transport zone is a container that defines the potential reach of transport nodes. This topic describes how to create a transport zone.

1.  Enter `https://<nsx-manager-ip-address>` in your browser and log on to NSX Manager with your admin privileges. 
2.  Select **Fabric** \> **Transport Zones**, and then click **Add**. 
3.  Set the details of the new transport zone. 
    -   Enter a name for the transport zone and optionally a description.
    -   Enter a name for the N-VDS.

        **说明：** N-VDS is a software switch that is created on a transport node. The purpose of N-VDS is to bind logical router uplinks and downlinks to physical NICs. For each transport zone that an NSX Edge belongs to, a single N-VDS is installed on the NSX Edge.

    -   Select an N-VDS mode. The options are Standard and Enhanced Datapath.
    -   Select a traffic type. The options are Overlay and VLAN.
        -   The overlay transport zone is used by both host transport nodes and NSX Edges. When a host or NSX Edge transport node is added to an overlay transport zone, an N-VDS is installed on the host or NSX Edge. Overlay is for internal NSX-T tunneling between transport nodes.
        -   The VLAN transport zone is used by the NSX Edge for its VLAN uplinks. When an NSX Edge is added to a VLAN transport zone, a VLAN N-VDS is installed on the NSX Edge. The VLAN is for uplinks external to NSX-T.
    -   Enter one or more uplink teaming policy names. These named teaming policies can be used by logical switches attached to the transport zone. If the logical switches do not find a matching named teaming policy, then the default uplink teaming policy is used.
    -   Click **Add** to create the transport zone. In this example, the following two transport zones are created to control the reach of Layer 2 networks in NSX-T.
        -   The transport zone named vtep-tz is created for the overlay traffic.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85013/154857788636054_en-US.png)

        -   The transport zone named ext-tz is created for the VLAN traffic.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85013/154857788636056_en-US.png)


