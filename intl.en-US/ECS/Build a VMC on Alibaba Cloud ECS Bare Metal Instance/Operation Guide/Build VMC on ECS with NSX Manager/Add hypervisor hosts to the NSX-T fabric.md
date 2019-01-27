# Add hypervisor hosts to the NSX-T fabric {#task_rcj_cvs_ggb .task}

A fabric node is a node that has been registered with the NSX-T management plane and has NSX-T modules installed. For a hypervisor host to be part of the NSX-T overlay, you need to first add it to the NSX-T fabric.

1.  From a browser, log on to an NSX Manager at `https://<nsx-manager-ip-address>`.
2.  For each host that you want to add to the NSX-T fabric, first gather the following host information:
    -   Hostname
    -   Management IP address
    -   Username
    -   Password
    -   \(Optional\) \(ESXi\) SHA-256 SSL thumbprint. To retrieve the hypervisor thumbprint, use the ESXi CLI in the ESX host and run the command `openssl x509 -in /etc/vmware/ssl/rui.crt -fingerprint -sha256 -noout`.

1.   Select **Fabric** \> **Nodes** \> **Hosts,**and then click **ADD**.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85016/154859360636010_en-US.png)

 
2.  Enter a name for the host and IP address, select **ESXi** from the **Operating System** drop-down list, enter the username and password of the ESXi system, enter the optional thumbprint, and then click **ADD**. 

    **Note:** If you do not enter the host thumbprint, you are prompted to use the default thumbprint in the plain text format retrieved from the host.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85016/154859360736011_en-US.png)

    When a host is successfully added to the NSX-T fabric, the NSX Manager **Fabric** \> **Nodes** \> **Hosts** page displays NSX Installed in the **Deployment Status** field and Up in the **Manager Connectivity**field. The host remains a standalone host until you have made the fabric node into a transport node.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/85016/154859360736016_en-US.png)

3.  Add other hypervisor hosts to the NSX-T fabric. 

