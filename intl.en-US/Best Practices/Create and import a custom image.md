# Create and import a custom image {#task_esq_phr_pgb .task}

This topic describes how to create a custom image and import it to Alibaba Cloud. If you want to create an instance that runs an operating system currently unavailable in Alibaba Cloud, you can create a custom image and import it to the ECS console. Then, you can use the custom image to create instances running the operating system.

-   VirtualBox is installed. You can download it from the [VirtualBox website](https://www.virtualbox.org/wiki/Downloads).
-   You have a stable Internet connection.
-   You have an Alibaba Cloud account. You can visit the Alibaba Cloud website to [register for a free account](https://account.alibabacloud.com/register/intl_register.htm?spm=a2c45.11132027.1143236.12.87287fecWQKaEV&oauth_callback=https://www.alibabacloud.com/).
-   An operating system ISO or binary file such as [Red Hat Enterprise Linux](https://developers.redhat.com/downloads/) is installed.
-   Alibaba Cloud [ossbrowser](../../../../reseller.en-US/Tools/ossbrowser/Quick start.md#) is installed.

1.  Create a new Virtual Machine \(VM\) on VirtualBox: 
    1.  Start VirtualBox and click **New**. 
    2.  Enter a name for the VM and select the correct OS type \(for example, Microsoft Windows\) and OS version \(for example, Windows 7 \(64-bit\)\). 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/122364/156885637139069_en-US.png)

    3.  Set the memory size. 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/122364/156885637139070_en-US.png)

    4.  Create a virtual hard disk. 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/122364/156885637139071_en-US.png)

    5.  Select **VHD \(Virtual Hard Disk\)** as the hard disk file type. Alibaba Cloud supports RAW, VHD, and qcow2 formats. 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/122364/156885637239072_en-US.png)

    6.  Select **Dynamically allocated** for the storage type. 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/122364/156885637239073_en-US.png)

    7.  Enter a name for the virtual hard disk and click **Create**. 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/122364/156885637239074_en-US.png)

    8.  Wait until the VHD file is created, and then double-click the newly created VM to launch it. 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/122364/156885637239075_en-US.png)

2.  Run the following command to install KVM virtualization platform drivers: 

    ```
    yum install qemu-kvm qemu-img libvirt
    ```

3.  Run the following command to disable the firewall of the VM: 

    ```
    service firewalld stop
    ```

4.  Upload the VHD file to OSS, and then use the ossbrowser to upload the VHD file to the region in which you want to create an instance. For more information, see [ossbrowser quick start](../../../../reseller.en-US/Tools/ossbrowser/Quick start.md#). 

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/122364/156885637239076_en-US.png)

5.  Import the custom image: 
    1.  Log on to the [ECS console](https://partners-intl.console.aliyun.com/#/ecs). 
    2.  Select the same region that you selected for uploading the VHD file to OSS, and then click **Import Image**. For information about how to allow ECS to access your OSS resources, see [Import custom images](../../../../reseller.en-US/Images/Custom image/Import images/Import custom images.md#section_nc3_yns_xdb). 

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/122364/156885637239077_en-US.png)

    3.  Set the relevant parameters, and then click **OK**. 

        **Note:** 

        -   You can log on to the OSS console to obtain the **OSS Object Address**. For more information, see [Download an object](../../../../reseller.en-US/Console User Guide/Upload、download and manage objects/Download an object.md#).
        -   After the custom image is imported, it appears in the list of images.
        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/122364/156885637239078_en-US.png)


