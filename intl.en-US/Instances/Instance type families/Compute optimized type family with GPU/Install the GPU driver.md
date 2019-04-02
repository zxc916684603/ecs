# Install the GPU driver {#concept_ecy_qrz_wgb .concept}

This topic describes how to download and install the GPU driver manually. If the GPU driver is not automatically installed during instance creation, you must install it manually after the creation.

## Download the GPU driver {#installDrive .section}

1.  Go to [NVIDIA website](http://www.nvidia.com/Download/index.aspx?lang=en).
2.  Find the drivers for your NVIDIA products, and click **Search**. The following table shows relevant metrics.

    |Item|gn4|gn5|gn5i|gn6v|
    |:---|:--|:--|:---|:---|
    |Product type:|Tesla|Tesla|Tesla|Tesla|
    |Product series|M-Class|P-Series|P-Series|V-Series|
    |Product|M40|Tesla P100|Tesla P4|Tesla V100|
    |Operating system \(OS\)|Select a release according to the image of your instance.**Note:** 

    -   If your OS is not in the drop-down list. Click **Select All Operating Systems** at the bottom of the list.
    -   For Debian, select **Linux 64-bit**.
![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9632/15541988375114_en-US.png)

|

3.  Confirm the information is correct, then click **Download**.

## Install the GPU driver for a Linux instance {#section_esm_dc1_4gb .section}

1.  Download and install the kernel-devel and kernel-header packages based on your kernel version.

    **Note:** If version conflict exists between kernel-devel and your kernel, driver compilation errors will occur during driver rpm installation. You can run rpm –qa | grep kernel in your instance to check version consistency before installing the driver.

2.  Run the sudo rpm -qa | grep $\(uname -r\) command to verify that the kernel-devel and kernel-header packages are successfully installed.

    For example, if you are using CentOS 7.3 and the following information appears, this means that the installation is successfully completed.

    ```
    
    kernel-3.10.0-514.26.2.el7.x86_64
    kernel-headers-3.10.0-514.26.2.el7.x86_64
    kernel-tools-libs-3.10.0-514.26.2.el7.x86_64
    python-perf-3.10.0-514.26.2.el7.x86_64
    kernel-tools-3.10.0-514.26.2.el7.x86_64
    ```

3.  Install the GPU driver according to the description in the **ADDITIONAL INFORMATION** area of the GPU download page.

    Take Linux 64-bit Ubuntu 14.04 for example:

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9632/15541988375117_en-US.png)


## Install the GPU driver for a Windows instance {#section_o2j_hrs_qgb .section}

Double-click the executable file to install the driver as instructed.

**Note:** For Windows instances, the Windows RDP protocol does not support DirectX or OpenGL after the GPU driver is successfully installed. In this case, you need to install the VNC service and client or other protocols by yourself \(for example, PCOIP, and XenDeskop HDX 3D\).

