# Shrink disk {#concept_66372_zh .concept}

Currently, Elastic Compute Service \(ECS\) does not support system disk or data disk shrink. If you want to shrink your disk volumes, try [Alibaba Cloud Migration Tool](reseller.en-US/Best Practices/Cloud Migration tool for P2V and V2V/Cloud Migration tool for P2V and V2V.md#) instead.

Though Cloud Migration Tool is designed to balance the cloud-based and offline workloads of Alibaba Cloud users, you can use it to shrink ECS disk volumes.

The tool creates a custom image based on your ECS instance. During this process, it re-specifies the size of the disk to shrink it. Apart from replacing the target object with an ECS instance, the tools for cloud migration and disk volume shrinking are identical, in terms of [both operation and limitations](reseller.en-US/Best Practices/Cloud Migration tool for P2V and V2V/Migrate to Alibaba Cloud by using Cloud Migration tool.md#). Because the ECS instance is already virtual, it is more convenient to use and the chances of reporting errors is reduced.

However, using this tool may change some attributes of the ECS instance. For example, instance ID \(`InstanceId`\) and public IP. If your instance is a [VPC-Connected](../../../../reseller.en-US/Product Introduction/What is VPC?.md#) instance, you can reserve the public IP address by [converting public IP address to EIP address](../../../../reseller.en-US/User Guide/Instances/Change IP addresses/Convert public IP address to EIP address.md#). We recommend that users using [Alibaba Cloud Elastic IP \(EIP\)](../../../../reseller.en-US/Product Introduction/What is Elastic IP Address?.md#) and users with less dependency on public IP use this approach to shrink the disk.

## Prerequisites { .section}

-   When the disk is mounted on a Linux instance, you must first install rsync, a remote data synchronization tool.
    -   CentOS Instance: Run `yum install rsync –y`.
    -   Ubuntu Instance: Run `apt-get install rsync –y`.
    -   Debian Instance: Run `apt-get install rsync –y`.
    -   Other distributions: Please visit the official website to find the relevant installation documents.
-   You must [create an AccessKey](https://help.aliyun.com/document_detail/53045.html?spm=a2c4g.11186623.2.20.4b8e16f2nDULTx) in the console first, which is used to output it into the configuration file [user\_config.json](#step04).

    **Note:** To prevent data leakage due to excessive permissions for AccessKey, we recommend that you [create a RAM sub-account](https://help.aliyun.com/document_detail/28637.html?spm=a2c4g.11186623.2.22.58e616f24NQeIh) and use this account to [create an AccessKey](https://help.aliyun.com/document_detail/53045.html?spm=a2c4g.11186623.2.23.58e616f2wkk2Rt).

-   For other prerequisites and limitations, see [migrate to Alibaba Cloud by using Cloud Migration Tool](https://help.aliyun.com/document_detail/62394.html?spm=a2c4g.11186623.2.24.58e616f2xAieKQ).

## Procedure { .section}

1.  [Connect](../../../../reseller.en-US/User Guide/Connect to instances/Connect to a Linux instance by using a password.md#) to the target ECS instance by using the administrator/root account.
2.  [Download](http://p2v-tools.oss-cn-hangzhou.aliyuncs.com/Alibaba_Cloud_Migration_Tool.zip?spm=5176.7765564.2.3.6SzsdG&file=Alibaba_Cloud_Migration_Tool.zip) the Alibaba Cloud Migration Tool zip file.
3.  Unzip the Cloud Migration Tool. Enter the corresponding operating system and version of the client file directory to find the configuration file user\_config.json.
4.  See [customize user\_config.json](https://help.aliyun.com/document_detail/62394.html?spm=a2c4g.11186623.2.27.58e616f2BpOqvq#user_config) to complete the configuration.

    See the following figure for the configuration file in a Linux instance.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9835/153949444411775_en-US.png)

    The most important parameters to configure for shrinking a disk volume are as follows:

    -   [`system_disk_size`](https://help.aliyun.com/document_detail/62394.html?spm=a2c4g.11186623.2.29.58e616f2BCnBNC#SystemDiskSize): Set this parameter to the expected system disk size in GB. The value cannot be less than the actual size of the system disk.
    -   [`data_disks`](https://help.aliyun.com/document_detail/62394.html?spm=a2c4g.11186623.2.30.58e616f2u3F27y#SystemDiskSize): Set this parameter to the expected data disk size in GB. The value cannot be less than the actual size of the data disk.
    **Note:** 

    -   When a Linux instance comes with a data disk, the `data_disks` parameter is required even if you do not want to shrink the data disk volume. If it is not configured, Cloud Migration Tool copies data from the data disk to the system disk by default.
    -   When a Windows instance comes with a data disk, the `data_disks` parameter is optional if you do not want to shrink the size of the data disk.
5.  Run the program go2aliyun\_client.exe:
    -   Windows instance: Right-click go2aliyun\_client.exe and select **Run as administrator**.
    -   Linux instance:
        1.  Run `chmod +x go2aliyun_client` to give the client executable permissions.
        2.  Run `./ go2aliyun_client` to run the client.
6.  Wait for the running results:
    -   If `Goto Aliyun Finished!` is displayed, go to the [ECS console](https://ecs.console.aliyun.com/#/image/region/cn-hangzhou/imageList) and check the custom image after shrinking. If the custom image has been generated, you can release the original instance and use the custom image to [create an ECS instance](../../../../reseller.en-US/User Guide/Instances/Create an instance/Create an instance from a custom image.md#). After you create a new instance, the disk volume shrinking process is complete.
    -   If `Goto Aliyun Not Finished!` is displayed, check the log files in the same directory for [troubleshooting](https://help.aliyun.com/knowledge_detail/66373.html). After fixing any problems, run Cloud Migration Tool again to resume volume shrinking. The tool continues the most recent migration progress and does not start over.

## References { .section}

-   For a detailed introduction to Cloud Migration Tool, see [what is Alibaba Cloud Migration Tool](https://help.aliyun.com/document_detail/62349.html?spm=a2c4g.11186623.2.35.58e616f2nUUBzw).
-   For instructions on how to use Cloud Migration Tool, see [migrate to Alibaba Cloud by using Cloud Migration Tool](https://help.aliyun.com/document_detail/62394.html?spm=a2c4g.11186623.2.36.412916f2GwkBYG).

