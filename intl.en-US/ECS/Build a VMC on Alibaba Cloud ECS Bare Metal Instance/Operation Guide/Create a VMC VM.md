# Create a VMC VM {#task_ojz_rvs_ggb .task}

This topics describes how to create a Virtual Machine \(VM\) on a hypervisor host.

1.  Enter the Internet IP address of the target Windows instance in your browser. 
2.  Start VMware vSphere Web Client. 
3.  Right-click the target host, and then click **New Virtual Machine** \> **New Virtual Machine**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83727/154857850936144_en-US.png)

4.  Select **Create a new virtual machine** and click **Next**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83727/154857851036146_en-US.png)

5.  On the **Select a name and folder** page, specify a name for the VM \(vm1, in this example\), select a data center to install the VM, and then click **Next**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83727/154857851036147_en-US.png)

6.  On the **Select a compute resource** page, select a host. In this example, the host with an IP address of 192.168.10.13 is selected. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83727/154857851036148_en-US.png)

7.  On the **Select storage** page, select a datastore to store the VM. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83727/154857851036149_en-US.png)

8.  On the **Select compatibility** page, select ESXi 6.5 and later from the drop-down list. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83727/154857851036150_en-US.png)

9.  On the **Select a guest OS** page, select **Linux** for the guest operating system family and **Red Hat Enterprise Linux 7 \(64-bit\)** for the guest operating system version. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83727/154857851036151_en-US.png)

10. On the **Customize hardware** page, specify the hardware configuration and allocate storage space as follows: 
    -   Select overlay-NVDS \(nsxLogicalSwitch\) for the network and then select **Connect At Power On**.
    -   Select Datastore ISO File from the drop-down list.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83727/154857851036152_en-US.png)

        Select the prepared CentOS-7-x86\_64-Minimal-1804.iso operating system installation file stored on the host storage disk.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83727/154857851036153_en-US.png)

    -   Select **Connect At Power On** for the CD/DVD drive, and then click **OK**.
11. On the **Ready to complete** page, review the VM configuration and click **Finish**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83727/154857851036156_en-US.png)

12. Right-click the target VMC VM, and then click **Power** \> **Power On**. 
13. Right-click the target VMC VM again, and then click **Open Console**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83727/154857851036159_en-US.png)

14. Start the operating system installation process in the console. 

    **Note:** After installing the operating system, you need to change the setting for the CD/DVD drive of the VM before rebooting the VM.

15. From the left-side navigation pane, right-click the newly created VM, and then click **Edit Settings**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83727/154857851036165_en-US.png)

16. On the **Virtual Hardware** tab page, select Client Device, clear the **Connect At Power On** option for the CD/DVD drive, and then click **OK**. 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/83727/154857851036166_en-US.png)

17. Reboot the VM to complete the operating system installation. 

