# Configure the cloud assistant client {#concept_wtg_32x_ydb .concept}

This topic describes how to install, update, and disable the cloud assistant client. The client is an agent that runs cloud assistant commands on ECS instances.

## Install the cloud assistant client by using the download link {#section_e5n_k2x_ydb .section}

**Note:** 

-   Instances created after December 1, 2017 by using public images are pre-installed with the cloud assistant client. If an ECS instance was created before December 1, 2017 and you want to use the cloud assistant service, you need to install the cloud assistant client manually.
-   For instances created by using custom images or Alibaba Cloud Marketplace images, you need to check your instance types and check whether the operating system of your instances supports the cloud assistant client before you install the client. For more information, see [Cloud assistant](../../../../../reseller.en-US/Deployment & Maintenance/Cloud assistant/Cloud assistant.md#).

**For Windows instances**

To install the cloud assistant client in a Windows instance, follow these steps:

1.  [Connect to a Windows instance](../../../../../reseller.en-US/Instances/Connect to instances/Connect to Windows instances/Connect to a Windows instance.md#).
2.  [Download the cloud assistant client](https://repo-aliyun-assist.oss-cn-beijing.aliyuncs.com/download/aliyun_agent_setup.exe).
3.  Double-click the downloaded client file and follow the prompts provided by the installation wizard to install the cloud assistant client.

**For Linux instances**

To install the cloud assistant client in a Linux instance, use one of the following procedures according to your operating system.

-   Procedure 1: Applicable to instances that run CentOS, RHEL, or SUSE Linux OSs. Download the RPM package to install the cloud assistant client. To do so, follow these steps:

    1.  [Connect to the target Linux instance by using a password](../../../../../reseller.en-US/Instances/Connect to instances/Connect to Linux instances/Connect to a Linux instance by using a password.md#).
    2.  Run the command `wget https://repo-aliyun-assist.oss-cn-beijing.aliyuncs.com/download/aliyun_assist.rpm` to download the RPM package of the cloud assistant client.
    3.  Run the `rpm -ivh aliyun_assist.rpm` command to install the cloud assistant client.
-   Procedure 2: Applicable to instances that run the Debian or Ubuntu OSs. Download the DEB package to install the cloud assistant client. To do so, follow these steps:

    1.  Connect to the target Linux instance.
    2.  Run the command `wget https://repo-aliyun-assist.oss-cn-beijing.aliyuncs.com/download/aliyun_assist.deb` to download the DEB package of the cloud assistant client.
    3.  Run the `dpkg -i aliyun_assist.deb` command to install the cloud assistant client.
-   Procedure 3: Download the source code to install the cloud assistant client.

    1.  Connect to the target Linux instance.
    2.  Run the command `git clone https://github.com/aliyun/aliyun_assist_client` to download the source code of the cloud assistant client.
    3.  Enter the source code directory.
    4.  Run the `cmake .` command to generate a compilation file.

        **Note:** If the `CMAKE_MINIMUM_REQUIRED` error occurs, go to the [CMake official website](https://cmake.org/download/) to download and install CMake v3.1 or a later version.

    5.  Run the `make` command to start compiling the code.
    6.  Run the `cmake_install.sh` command to install the cloud assistant client.

## Install the cloud assistant client by using the Alibaba Cloud CLI {#section_qkk_yt2_ngb .section}

**Prerequisites**

-   Alibaba CLI is installed.
-   You have obtained the region ID. For more information, see [Regions and Zones](../../../../../reseller.en-US/General Reference/Regions and Zones.md#).

**Procedure**

1.  Call the [DescribeCloudAssistantStatus](../../../../../reseller.en-US/API Reference/Cloud assistant/DescribeCloudAssistantStatus.md#) API action to check whether the cloud assistant client is installed on the target instance.

    ```
    aliyun ecs DescribeCloudAssistantStatus --RegionId TheRegionId --InstanceId.1 i-bp1g6zv0ce8ogXXXXXXp --output cols=CloudAssistantStatus
    ```

    If the response message `CloudAssistantStatus=true` is returned, it indicates that the cloud assistant client is installed on the target instance. Otherwise, proceed to the next step.

2.  Call the [InstallCloudAssistant](../../../../../reseller.en-US/API Reference/Cloud assistant/InstallCloudAssistant.md#) API action to install the cloud assistant client on the target instance.

    ```
    aliyun ecs InstallCloudAssistant --RegionId TheRegionId --InstanceId.1 i-bp1g6zv0ce8ogXXXXXXp
    ```


## Update the cloud assistant client {#section_r34_32x_ydb .section}

The cloud assistant client runs the update process once every hour to detect for updated resources. Depending on the operating system installed on your instance, the update process is located in the following directories:

-   Windows instance: C:\\ProgramData\\aliyun\\assist\\$\{version\}/aliyun\_assist\_update

-   Linux instance: /usr/local/share/aliyun-assist/$\{version\}/aliyun\_assist\_update


If the automatic update fails, you can [create commands](../../../../../reseller.en-US/Deployment & Maintenance/Cloud assistant/Use the cloud assistant/Create commands.md#) or call the [CreateCommand](../../../../../reseller.en-US/API Reference/Cloud assistant/CreateCommand.md#) API action to update the cloud assistant client at a scheduled time. For example, if you install the cloud assistant client by using the RPM package, you can run the following command to update the cloud assistant client:

```
wget https://repo-aliyun-assist.oss-cn-beijing.aliyuncs.com/download/aliyun_assist.rpm
rpm -U aliyun_assist.rpm
```

## Disable the update process of the cloud assistant client {#section_r3q_yps_52b .section}

The update process of the cloud assistant client is started automatically, but you can disable the update process as follows:

-   For Windows instances, run the `rename aliyun_assist_update` command in Command Prompt.

-   For Linux instances, run the `chmod a-x aliyun_assist_update` command.


## Disable the cloud assistant client {#section_rlc_n2x_ydb .section}

**For Windows instances**

1.  [Connect to the target Windows instance](../../../../../reseller.en-US/Instances/Connect to instances/Connect to Windows instances/Connect to a Windows instance.md#).
2.  Choose **Computer Management** \> **Services and Applications** \> **Services****AliyunService**.

    **Warning:** **AliyunService** is the name of the cloud assistant client when the client is in the **Running** state. If you disable **AliyunService**, the cloud assistant client is disabled. In this case, the instance may fail and cannot be changed to the **Stopped** state through the ECS console.

3.  Click **Stop the service**.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9582/15550618645250_en-US.png)


**For Linux instances**

1.  [Connect to the target Linux instance by using a password](../../../../../reseller.en-US/Instances/Connect to instances/Connect to Linux instances/Connect to a Linux instance by using a password.md#).
2.  Disable the cloud assistant client as follows:
    -   For instances running the Debian, CentOS, or Red Hat, run the following command:

        ```
        systemctl stop agentwatch
        
        ```

    -   For instances running other operating systems, run the following command:

        ```
        chkconfig agentwatch off
        ```


## What to do next {#section_aj4_32x_ydb .section}

You can visit the [GitHub repository aliyun\_assist\_client](https://github.com/aliyun/aliyun_assist_client) to explore the open source stack of the cloud assistant client.

You can also use the cloud assistant client in the following topics:

-   [Cloud assistant](reseller.en-US/Deployment & Maintenance/Cloud assistant/Cloud assistant.md#).
-   [InvokeCommand](../../../../../reseller.en-US/API Reference/Cloud assistant/InvokeCommand.md#).
-   [Automatically manage instances](../../../../../reseller.en-US/Deployment & Maintenance/Cloud assistant/Automatically manage instances.md#).

