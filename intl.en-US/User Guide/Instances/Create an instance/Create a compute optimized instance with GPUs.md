# Create a compute optimized instance with GPUs {#concept_g5s_g2z_xdb .concept}

Compute optimized instances with GPUs \(or GPU instances for short\) are available in the gn4, gn5, gn5i, and gn6v instance families.

## Create an instance {#section_v1b_nxz_xdb .section}

To create a GPU instance, you must configure the following settings. For detailed steps, see [create an ECS instance](../../../../reseller.en-US/Quick Start for Entry-Level Users/Step 2. Create an instance.md#).

-   **Region**: Each instance type family is available only in certain regions:

    -   gn4: North China 2 \(Zone A\), East China 2 \(Zone B\), South China 1 \(Zone C\)
    -   gn5: North China 2 \(Zone C and E\), North China 5 \(Zone A\), East China 1 \(Zone G and F\), East China 2 \(Zone D, B, and E\), South China 1 \(Zone D\), Hong Kong \(Zone C and B\), Asia Pacific SE 1 \(Zone A and B\), Asia Pacific SE 2 \(Zone A\), Asia Pacific SE 3 \(Zone A\), Asia Pacific SE 5 \(Zone A\), US West 1 \(Zone A and B\), US East 1 \(Zone A and B\), and EU Central 1 \(Zone A\)

        **Note:** If you want to deploy NVIDIA GPU CLOUD \(NGC\) on a gn5 instance, see [deploy an NGC on a gn5 instance when selecting a region](../../../../reseller.en-US/Best Practices/GPU instances/Deploy an NGC on gn5 instances.md#).

    -   gn5i: North China 2 \(Zone C, E and A\), East China 1 \(Zone B\), East China 2 \(Zone D and B\), and South China 1 \(Zone A\)
    -   gn6v: East China 2 \(Zone F\)
    The preceding regions and zones are for reference purpose only. Please check the purchase page for the latest information about the availability of instance types.

-   **Image**:
    -   To install a GPU driver and a CUDA library, select one of the following options:
        -   Select **Public Image**. From the drop-down list, select a CentOS 64-bit image \(any version\), the Ubuntu 16.04 64-bit image, or the SUSE Linux Enterprise Server 12 SP2 64-bit image. Then, select **Auto-install GPU Driver**. Finally, select a CUDA library and GPU driver.

            **Note:** 

            -   You can select a GPU driver based on your business needs. For a new business system, we recommend that you select the latest GPU driver.
            -   If **Auto-install GPU Driver** is selected, **UserData** will be generated automatically. It is a shell script to install the CUDA library and the GPU driver automatically. You can view it when setting up the **Advanced** options in **System Configurations**. After the instance is created and started successfully for the first time, the cloud-init runs the script to install the GPU driver. For more information, see the note for the GPU installation script.
        -   Select **Marketplace Image**, search for NVIDIA, and select an image from the results. Currently, only CentOS 7.3 and Ubuntu 16.04 are supported.
    -   To use a GPU instance for deep learning, you can select an image pre-installed with the deep learning framework. Select **Marketplace Image**, search for Deep Learning, then select the desired image from the results. Currently, only CentOS 7.3 and Ubuntu 16.04 are supported.
    -   For other images, you must [download and install a GPU driver](#) after the instance is created.
-   **Instance Type**: Select **Heterogeneous Computing** \> **GPU Compute**, and select an instance type.
-   **Network**: Select **VPC**.
-   **Network Billing Method**: Select a bandwidth based on your needs.

    **Note:** If Windows 2008 R2 or earlier is running on the instance, you cannot use the [Management Terminal](reseller.en-US/User Guide/Connect to instances/Connect to an instance by using the Management Terminal.md#) in the ECS console to connect to the GPU instance after the GPU driver is effective. Therefore, you must select **Assign Public IP**, or [bind EIP](../../../../reseller.en-US/User Guide/Bind EIP to cloud resources.md#) after creating the instance.

-   **Log on Credentials**: Set a credential to log on to the instance.

    **Note:** We recommend that you do not select **Set Later**. This is because, to log on to the instance after it is created and before the GPU driver is installed, you have to reset the password or bind an SSH key pair, and then restart the instance to make the change take effect. The restart operation, however, causes the failure of driver installation.

-   **User Data**: If **Auto-install GPU Driver** is enabled, a script to install a CUDA library and a GPU driver is displayed here. Read the script and note carefully.

## Check the installation progress {#section_gbb_nxz_xdb .section}

If **Auto-install GPU Driver** is enabled, after the instance is created, you can [connect to the instance](reseller.en-US/User Guide/Connect to instances/Overview.md#), and read the log file `/root/nvidia_install.log` to check the installation progress.

**Note:** To avoid installation failure, do not operate GPU or install any other GPU-related software before the GPU driver is installed successfully.

## Download and install a GPU driver {#installDrive .section}

If the image is not pre-installed with a GPU driver, you must install one for the instance.

1.  Obtain the GPU driver package:
    1.  Go to the [NVIDIA official website](http://www.nvidia.com/Download/index.aspx?lang=cn).
    2.  Manually locate the appropriate driver for the instance, and click **Search**. Complete the following parameters and search for the driver.

        |Item|gn4|gn5|gn5i|gn6v|
        |:---|:--|:--|:---|:---|
        |Product Type|Tesla|Tesla|Tesla|Tesla|
        |Product Series|M-Class|P-Series|P-Series|V-Series|
        |Product|M40|Tesla P100|Tesla P4|Tesla V100|
        |Operating System|Select an OS version according to the image of your instance. If the server operating system is not displayed in the drop-down list, click **Show all Operating Systems** at the bottom of the drop-down list.![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9632/15429592905114_en-US.png)

|

    3.  Confirm the driver and click **DOWNLOAD**.
2.  Install the GPU driver:
    -   Windows: Double-click the installation file to install the driver.
    -   Linux:
        1.  Download and install the appropriate version of kernel-devel and kernel-header packages.
        2.  Run the following commands to verify that the packages are downloaded and installed successfully.

            ```
            sudo rpm -qa | grep $(uname -r)
            ```

            Take CentOS 7.3 as an example. If the following message returns, the packages are installed successfully.

            ```
            
            kernel-3.10.0-514.26.2.el7.x86_64
            kernel-headers-3.10.0-514.26.2.el7.x86_64
            kernel-tools-libs-3.10.0-514.26.2.el7.x86_64
            python-perf-3.10.0-514.26.2.el7.x86_64
            kernel-tools-3.10.0-514.26.2.el7.x86_64
            ```

        3.  Go to the download page of the driver on the NVIDIA website, click the **ADDITIONAL INFORMATION** tab, and follow the tips to install the driver.

            Take Linux 64-bit Ubuntu 14.04 as an example.

            ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9632/15429592905117_en-US.png)


## Install a GRID driver {#section_ubb_nxz_xdb .section}

If your gn5, gn5i or gn6v instance requires OpenGL, you must install a GRID driver. For more information, see [install a GRID driver on a gn5/gn5i/gn6v instance](../../../../reseller.en-US/Best Practices/GPU instances/Install a GRID driver on a gn5__gn5i__gn6v instance.md#).

## Note {#section_urs_qd1_ydb .section}

**For remote access**

For Windows 2008 R2 or earlier, if you want to connect to your instance by using the [Management Terminal](reseller.en-US/User Guide/Connect to instances/Connect to an instance by using the Management Terminal.md#) on the ECS console after the GPU driver is effective, the Management Terminal is non-operational. It shows either a black screen or the startup interface. If the instance can access the Internet, connect to the instance remotely by using other protocols, such as the Remote Desktop Protocol \(RDP\) developed by Microsoft.

RDP does not support DirectX, OpenGL, and other related applications. Therefore, you must install the VNC server and client, or other protocols that support these applications, such as PCOIP or XenDesktop HDX 3D.

**For the GPU driver installation script**

For the GPU auto installation script, note the following:

-   The script automatically downloads and installs a NVIDIA GPU driver and a CUDA library.
-   The installation takes 4.5 to 10 minutes, depending on the intranet bandwidth and the quantity of vCPU cores of the instance. To avoid installation failure, do not operate the GPU or install any GPU-related software until the GPU driver is installed successfully.
-   After the GPU is installed successfully, the instance restarts automatically to bring the driver into effect.
-   The script turns on the **Persistence Mode** of the driver and add this setup to the automatic startup script of the instance to make sure that this mode is turned on automatically when the instance is restarted. The GPU driver works in a more stabilized manner in this mode.
-   When [changing the operating system](reseller.en-US/User Guide/Instances/Change the operating system.md#), note the following:
    -   Replacing Ubuntu 16.04 64-bit or SUSE Linux Enterprise Server 12 SP2 64-bit with other distributions or versions causes failure of automatic installation of the GPU driver.
    -   Replacing one version of CentOS with another version does not cause installation failure of the GPU driver.
    -   Replacing the image with another image that does not support the automatic installation script causes failure of automatic installation of the GPU driver.
-   A log is generated during installation, and is saved to the /root/nvidia\_install.log. You can read the log to check the installation result of the driver. If the installation fails, you can view the causes.

