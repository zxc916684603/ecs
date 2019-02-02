# Create an ESXi host image {#concept_p3w_tkz_ggb .concept}

This topic describes how to create an ESXi host image.

## Prerequisites {#section_wqj_hpz_ggb .section}

Your hardware and software have met the following requirements:

**Hardware requirements**

-   One client computer \(client\)
-   One server computer \(server\)

**Note:** For more information about the hardware requirements of the server, see VMware [ESXi Hardware Requirements](https://docs.vmware.com/en/VMware-vSphere/6.5/com.vmware.vsphere.install.doc/GUID-DEB8086A-306B-4239-BF76-E354679202FC.html?hWord=N4IghgNiBcIKYGcAeBLABANgHQFYQF8g).

**Software requirements**

**Note:** This topic uses the following software as an example.

-   Operating system: Windows 7 Enterprise Edition 64-Bit \(installed on the client\), and CentOS 7.2 64-Bit \(installed on the server\)
-   ESXi: VMware vSphere Hypervisor 6.5.0

## Before you begin {#section_u4z_wpz_ggb .section}

Before creating an ESXi host image, you need to prepare the environment.

1.  Register an Alibaba Cloud account. For more information, see [Sign up with Alibaba Cloud](https://www.alibabacloud.com/help/doc-detail/50482.htm?spm=a2c63.l28256.b99.2.588e5003OzZmJ9).
2.  Log on to the [ECS console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home), and then open a ticket to obtain the following drivers.

    |Driver|File name|
    |------|---------|
    |virtio-blk|vioblk-0.1-5vmw.650.0.0.4032367.x86\_64.vib|
    |Virtio-net|virtionet-1.0.0.0-16vmw.650.0.0.4598673.x86\_64.vib|

3.  Download [PuTTY](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html), and then connect to the physical server where the VM is installed.
4.  Disable SELinux.
    1.  In the CLI of the physical server, run the getenforce command to check the current status of SELinux.

        **Note:** 

        If the status is Enforcing, SELinux is enabled. If the status is Disabled, SELinux is disabled.

    2.  \(Optional\) To disable SELinux temporarily, run the setenforce 0 command.

        **Note:** 

        If you have temporarily disabled SELinux, it will be enabled automatically when Linux is restarted.

    3.  \(Optional\) To disable SELinux permanently, follow these steps:
        1.  Run the command vi /etc/selinux/config to edit the SELinux configuration file.
        2.  Press **Enter**, and move the cursor to the SELINUX=enforcing line.
        3.  Press the **i** key to enter the editing mode and change the line to SELINUX=disabled.
        4.  Press **Esc**, enter :wq, and then press **Enter** to save and close the SELinux configuration file.
        5.  Restart the system to validate the settings.

            **Note:** For more information, see [Introduction to SELinux](https://access.redhat.com/documentation/en-us/red_hat_enterprise_linux/5/html/deployment_guide/ch-selinux#s1-SELinux-resources) at the official Red Hat website.

5.  Run the following commands to enable port 5900 and port 5901 on the server where the TightVNC Viewer runs:

    ```
    
    sudo firewall-cmd --zone=public --add-port=5900/tcp --permanent
    sudo firewall-cmd --zone=public --add-port=5901/tcp --permanent
    sudo firewall-cmd --reload
    ```

6.  Run the command yum -y install firefox to install the Mozilla Firefox Web browser.
7.  Run the command yum -y groupinstall Fonts to install the language package.
8.  Install the TigerVNC Server program on the server and TightVNC Viewer program on the client. For more information, see [How do I install VNC Server on a Linux instance to implement GUI-based access](https://www.alibabacloud.com/help/faq-detail/41530.htm?spm=a2c63.q38357.a3.3.7fc83827eXz6bd).
9.  Run the egrep "\(vmx|svm\)" /proc/cpuinfo command to check whether the system supports 64-bit Virtual Machines \(VMs\).

    **Note:** 

    To support 64-bit VMs, the x64 CPU must support hardware virtualization \(Intel VT-x or AMD RVI\).

    If the command output includes vmx, it means that the system supports Intel CPU VMs. If the command output includes svm, it means that the system supports AMD CPU VMs. If no information is returned, it means that the system does not support virtualization.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84394/154886266235611_en-US.png)


## Procedure {#section_nz4_lsz_ggb .section}

To create an ESXi host image, follow these steps:

1.  Download the ESXi 6.5.0 image.
    1.  On the client, start TightVNC Viewer.
    2.  In the **Remote Host** field, enter Server IP address:5901, and then click **Connect**. The Welcome page is displayed when the connection is successful, as shown in the following figure.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84394/154886266235612_en-US.png)

    3.  Open the [logon page of VMware](https://my.vmware.com/en/web/vmware/) in your preferred browser. If you have a VMware account, enter your username and password and click **Log In**. If not, click **Register** to register a VMware account, and then log on.
    4.  Click **All Downloads**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84394/154886266336200_en-US.png)

    5.  On the **All Products** tab page, find VMware vSphere Hypervisor \(ESXi\) in the product list, and then click **View Download Components**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84394/154886266335614_en-US.png)

    6.  Click **Download**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84394/154886266335615_en-US.png)

    7.  On the Download Packages page, find VMware vSphere Hypervisor 6.5.0 Update 2 - Binaries, and then click **Manually Download**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84394/154886266335616_en-US.png)

        **Note:** 

        The ESXi host image to be downloaded is in iso format. However, it must be converted to RAW, VHD, or qcow2 format before it can be imported to Alibaba Cloud ECS instances.

2.  In the CLI of the physical server, run the following commands to install the qemu-img tool and the qemu-kvm tool:

    ```
    
    sudo yum install qemu-img
    sudo yum install qemu-kvm
    sudo ln -sv /usr/libexec/qemu-kvm /usr/bin/
    ```

    **Note:** The qemu-img tool is used to convert the iso image to a qcow2 image, while the qemu-kvm tool is used to manage virtualized server hardware.

3.  Run the following command to create a 40 G qcow2-format VM image named esxi-xdragon.qcow2:

    `qemu-img create -f qcow2 ./esxi-xdragon.qcow2 40G`

4.  Run the following command to start the VM and install the ESXi system:

    `sudo qemu-kvm -enable-kvm -name "generic" -cpu host -m 4096 -smp 4 -cdrom ./VMware-VMvisor-Installer-6.5.0.update02-8294253.x86_64.iso ./esxi-xdragon.qcow2 -net user -net nic,model=e1000,macaddr=52:54:00:A6:71:83 -netdev user,id=netdev1 -device virtio-net-pci,netdev=netdev1,id=device-net1,mac=52:54:00:A6:71:80 -vnc :0`

5.  On the client, start TightVNC Viewer.
6.  Enter Server IP address:5900 in the **Remote Host** field, and then click **Connect** to connect to the VM.

    **Note:** The ESXi system installation progress is displayed in the dialog box. You can configure the ESXi system as prompted.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84394/154886266336201_en-US.png)

7.  After the ESXi system is installed, click **Reboot** to restart the ESXi system.
8.  Enable ESXi Shell and SSH.
    1.  In the ESXi system, press **F2**, create your logon username and password as prompted, and press **Enter** to go to the System Customization window.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84394/154886266335617_en-US.png)

    2.  Select Troubleshooting Options, and then press **Enter** to go to the Troubleshooting Mode Options window.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84394/154886266335618_en-US.png)

    3.  Select Enable ESXi Shell, and then press **Enter** to set its value to ESXi Shell is Enabled.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84394/154886266335619_en-US.png)

    4.  Select Enable SSH, and then press **Enter** to set its value to SSH is Enabled.
    5.  Press **Esc** to close the ESXi system configuration window.
9.  Install the virtio-blk driver and the virtio-net driver.
    1.  In the window where TightVNC Viewer connects to port 5901 of the server, start the browser and log on to the [ECS console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home).
    2.  In the left-side navigation pane, click **Object Storage Service**.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84394/154886266335620_en-US.png)

    3.  In the **Bucket Name** search box, enter the name of the bucket that stores the virtio driver, and then click the bucket name to go to its management page.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84394/154886266335621_en-US.png)

    4.  Click the **Files**tab.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84394/154886266335622_en-US.png)

    5.  In the file list, click the name of the file to be downloaded.
    6.  On the displayed Preview page, copy the virtio driver download address from the **URL** text box.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84394/154886266335623_en-US.png)

    7.  In the window where TightVNC Viewer connects to port 5900 of the server, press **Alt+F1** to go to the ESXi Shell page, and then enter your username and password.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84394/154886266335624_en-US.png)

    8.  Run the following command to download the virtio-blk driver and the virtio-net driver to the /tmp folder:

        `wget -P /tmp download address`

    9.  Run the following commands to install the virtio-blk driver and the virtio-net driver:

        ```
        
        esxcli software vib remove -n vioblk
        esxcli software vib install -v /tmp/vioblk*.vib -f
        esxcli software vib remove -n virtionet
        esxcli software vib install -v /tmp/virtionet*.vib -f
        ```

    10. Restart the ESXi system, and then press **Alt+F1** to go to the ESXi Shell page.
    11. Run the following command to configure virtio-net queue pairs:`esxcli system module parameters set -p 'features=0x104399a3 queuePairs=16' -m virtionet;`
10. Run the reboot command to restart the ESXi system.
11. Press **Alt+F1** to return to the ESXi Shell page. Run the following command to modify the MAC address of the physical machine:

    `esxcli system settings advanced set -o /Net/FollowHardwareMac -i 1`

12. Restart the VM. The MAC address of the ESXi VMkernel \(VMK\) interface is changed accordingly.
13. Run the command vi /etc/vmware/esx.conf to open the esx.conf file.
14. Press the **i** key to enter the editing mode, and then find and delete the command line that starts with /system/uuid.
15. Press **Esc** to exit the editing mode, enter :wq, and press **Enter** to save and close the esx.conf file.
16. Run the /sbin/auto-backup.sh command so that the configuration can be saved after the ESXi system is restarted.
17. Press **Alt+F2** to exit ESXi Shell, and then exit the ESXi system.

## Upload the ESXi host image to OSS {#section_ucj_byz_ggb .section}

After creating an ESXi host image, you must upload the ESXi host image to OSS by following these steps:

1.  In the window where TightVNC Viewer connects to port 5901 of the server, start the browser and log on to the [ECS console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home).
2.  In the left-side navigation pane, click **Object Storage Service**.
3.  Create a bucket. For more information, see [Create a bucket](https://www.alibabacloud.com/help/doc-detail/31896.htm?spm=a2c63.l28256.b99.527.27885139gnx1CS).
4.  Import the ESXi host image. For more information, see [Import image to Alibaba Cloud](https://www.alibabacloud.com/help/doc-detail/92663.htm?spm=a2c63.l28256.b99.6.5ef823318pM7ma).

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/84394/154886266435625_en-US.png)


