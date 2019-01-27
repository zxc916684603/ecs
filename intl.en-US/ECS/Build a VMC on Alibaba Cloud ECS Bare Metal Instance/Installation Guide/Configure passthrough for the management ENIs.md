# Configure passthrough for the management ENIs {#task_mpb_1vs_ggb .task}

This topic describes how to check the relations among the ENI \(MAC address and IP address\), host PCI, and vmnic, and set the management ENI to the **Passthrough capable** mode.

1.  Check the [ENI Mapping to Vmnic](intl.en-US/ECS/Build a VMC on Alibaba Cloud ECS Bare Metal Instance/Preparation/ENI Mapping to Vmnic.md#) and find the vmnic and PCI device for each secondary management ENI. 
2.  Connect to your Windows instance on which vCenter Server is installed. Use the browser on the instance to access the private IP address of the host that provides network management utilities. 
3.  Enter the username and password \(the username and password you set when creating an ESXi image\) of the ESXi system to go to the ESXi management page. 
4.  Go to the PCI device page, locate and check the PCI Device values recorded, and then click **Toggle passthrough**. Set the three secondary management ENIs to the **Passthrough capable** mode. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83721/154857720537885_en-US.png)


