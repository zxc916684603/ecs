# Modify vtep VDS configurations {#task_d3r_tx1_hgb .task}

This topic describes how to modify the configurations of the vtep vSphere Distributed Switch \(VDS\).

1.  You have created a vtep VDS.
2.  You have added a host for the vtep VDS.
3.  You have logged on to the Windows instance on which vCenter Server is installed.

1.  Log on to **vSphere Web Client**. 
2.  In the left-side navigation pane, click the distributed port group **vtep-DPortGroup**. 
3.   Click **Configure**, and then choose **Settings** \> **Properties**. On the Properties page, click **Edit**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84996/154886349935590_en-US.png)

 
4.  On the Edit Settings page, click **Security**. From the **Promiscuous mode** drop-down list, select Accept. From the **MAC address changes** drop-down list, select Accept. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84996/154886349935591_en-US.png)

    The parameters are described as follows.

    |Parameter|Description|
    |:--------|:----------|
    |Promiscuous mode|     -   Accept: If a guest adapter is in promiscuous mode, it will detect all frames passed on the vSphere standard switch. These frames are allowed under the VLAN policy for the port group to which the adapter is connected.
    -   Reject: If a guest adapter is in promiscuous mode, it has no effect on which frames are received by the adapter.
 |
    |MAC address changes|     -   Accept: Changing the MAC address from the guest OS has the intended effect. Frames to the new MAC address are received.
    -   Reject: If the guest OS changes the MAC address of the adapter to an address that is not included in the .vmx configuration file, all inbound frames will be dropped. If the guest OS changes the MAC address back to match the MAC address in the .vmx configuration file, inbound frames are passed again.
 |
    |Forged transmits|     -   Accept: No filtering is performed and all outbound frames are passed.
    -   Reject: Any outbound frame with a source MAC address that is different from the one currently set on the adapter is dropped.
 |

5.  Restart the host that provides network management utilities. 

