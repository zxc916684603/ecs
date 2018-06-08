# Cloud assistant {#concept_qg3_5dx_ydb .concept}

Cloud assistant is a lightweight and convenient maintenance ECS feature for automated and batched invocation of daily maintenance tasks.

By installing the cloud assistant client on ECS instances, you can run Bat/PowerShell \(for Windows instances\) scripts or Shell scripts \(for Linux  instances\) on one or more running ECS instances in the ECS console or by calling APIs. The invocation is exclusive to individual instances to complete tasks rapidly. You can also set command invocation to the periodical mode to keep the ECS instance at a specific status or run the command as a daemon for ECS instances. Cloud assistant does not initiate any operations. All operations are within your controllable range.

## Scenarios {#section_f5p_5dx_ydb .section}

You can use cloud assistant in the following scenarios.

-   Install, uninstall, or update applications for ECS instances that are in the `Running` status.
-   Update patches for ECS instances that are in the Running status.
-   Add configuration for ECS instances that are in the Running status.
-   Set daemon process for ECS instances that are in the  Running status.
-   Retrieve monitoring and log information for ECS instances that are in the Running status.
-   Other maintenance tasks that must be completed by running scripts.

## Terminology {#section_zfz_wdx_ydb .section}

|Term|Common name |Description|
|:---|:-----------|:----------|
|Cloud assistant|Cloud assistant|A convenient feature provided by Alibaba Cloud ECS for automated and batched invocation of daily maintenance tasks.|
|Cloud assistant client|Client|The client program that is installed on ECS instance. All operations to ECS instances are performed by using the client.|
|Command|Command|The specific command and operation to be invoked on ECS instances, such as a shell script.|
|One-time invocation|Invocation|One or more ECs in the specified If a command is invoked on an instance or multiple instances only once then, it is called as one-time invocation \(`Invocation`\).|
|Periodical invocation|Timed Invocation|When you invoke a command on an instance or multiple instances, you can specify the invocation sequence/period to run the command process periodically.|
|Invocation status|InvokeStatus|The relationship among command invocation status. The invocation status can be divided into three levels:-   **Overall invocation status:**The general invocation status for all the target ECS instances when invoking a daemon process.
-   **Instance invocation status:** The invocation status of command invocation that are batch processed on all the ECS instances.
-   **Invocation-record status:** The invocation status of a specific ECS instance when invoking a command.

|

## Limits {#section_n5p_5dx_ydb .section}

Cloud assistant has the following limits:

-   You must install and manage the cloud assistant as the administrator. Specifically, the Linux instance administrator is root and the Windows instance administrator is administrator.

-   You must manage the cloud assistant as an the administrator.

-   The size of the source Bat/PowerShell script or Shell script must be less than 16 KB.

-   Requirements on the status of the target ECS instances:

    -   ECS instances must be connected to the intranet.
    -   The ECS instance must be in the `Running` status.
    -   The network type of the ECS instance must be VPC.
-   Other limits for using cloud assistant:

    |Supported images|Supported regions|
    |:---------------|:----------------|
    |     -   Windows Server 2008/2012/2016
    -   Ubuntu 12/14/16
    -   Centos 5/6/7
    -   Debian 7/8/9
    -   RedHat 5/6/7
    -   SuSE Linux Enterprise Server 11/12
    -   Opensuse
    -   Aliyun Linux
    -   Freebag
    -   Coreos
 |     -   China East 1 \(Hangzhou\)
    -   China East 2 \(Shanghai\)
    -   China North 2 \(Beijing\)
    -   China North 3 \(Zhangjiakou\)
    -   China South 1 \(Shenzhen\)
    -   Hong Kong
    -   Asia Pacific SE 1 \(Singapore\)
    -   Asia Pacific SE 2 \(Sydney\)
    -   Asia Pacific SE 3 \(Kuala Lumpur\)
    -   US East 1 \(Virginia\)
    -   Germany 1 \(Frankfurt\)
 |


## Billing details {#section_v5p_5dx_ydb .section}

Cloud assistant features are free of charge.

## Invocation status {#section_cyj_ydx_ydb .section}

-   Specifically, the invocation status of a command consists of `Running`, `Stopped`,  `Finished`, and `Failed`.

-   Generally, the invocation status of a command includes **overall invocation status** , **instance invocation status** , and  **invocation-record status**. The relationships among various levels are shown in the following figure.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9581/5245_en-US.png)


**For one-time invocations**

-   **Overall invocation status**：
    -   When the invocation status of all instances are `Finished`, the overall invocation status is displayed as `Finished`.
    -   When the invocation status of some instances are `Finished` and those of some others are `Stopped`, the overall invocation status is displayed as. `Finished`
    -   When the invocation status of all instances are `Failed`, the overall invocation status is displayed as `Failed`.
    -   When the invocation status of all instances are `Stopped`, the overall invocation status is displayed as `Stopped`.
    -   When the invocation statuses of all or some instances are `Running`, the overall invocation status is displayed as  `Running`.
    -   When the invocation statuses of some instances are `Failed`, the overall invocation status is displayed as `PartialFailed`.

        Take three ECS instances as an example. The following picture shows the relationships between the overall invocation status and the instance invocation status during a one-time invocation on multiple instances.

        ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/9581/5246_en-US.png)

-   **Instance invocation status**: The command is invoked only once in a one-time invocation, so the instance invocation status and the invocation-record status are identical.
-   **Invocation-record status:**：
    -   `Running`: Indicates that the command is being executed.
    -   `Stopped`: Indicates that the command invocation has been manually stopped by the user.
    -   `Finished`: Indicates that the command invocation has been completed smoothly. But invocation completion does not indicate invocation success. You can confirm whether the invocation is successful based on the actual `Output`of the command process.
    -   `Failed`: Indicates that the command process has timed out \(`Timeout`\) and failed.

**For periodical invocations**

-   **Overall invocation status**: The overall invocation status is always `Running` unless you stop all the scheduled invocation for all instances.
-   **Instance invocation status**: The instance invocation status is always `Running` unless you stop the current invocation.
-   **Invocation-record status:**：
    -   `Running`: The command is being executed.
    -   `Stopped`: You have stopped the command invocation.
    -   `Finished`: The command invocation is complete. However, invocation completion does not guarantee invocation success. You can confirm whether the invocation is successful or not based on the actual `Output` of the command process.
    -   `Failed`: The command process is timed out \(`Timeout`\) and fails.

## How to use cloud assistant {#section_ivp_5dx_ydb .section}

You must install cloud assistant client on your ECS instance beforehand to use cloud assistant.

Currently the cloud assistant is not available on the console. You can use it by APIs. For more information, see [Auto manage instances](https://www.alibabacloud.com/help/doc-detail/64741.htm).

## References {#section_jvp_5dx_ydb .section}

-   [EN-US\_TP\_9582.md\#](intl.en-US/Product Introduction/Cloud assistant/Cloud assistant client.md#)
-   Cloud assistant APIs:
    -   [CreateCommand](../intl.en-US/API Reference/Cloud assistant/CreateCommand.md#): CreateCommand
    -   [InvokeCommand](../intl.en-US/API Reference/Cloud assistant/InvokeCommand.md#): InvokeCommand The instance has executed the created commands.
    -   [../DNA0011860945/EN-US\_TP\_9962.md\#](../intl.en-US/API Reference/Cloud assistant/DescribeInvocations.md#): DescribeInvocations
    -   [../DNA0011860945/EN-US\_TP\_9963.md\#](../intl.en-US/API Reference/Cloud assistant/DescribeInvocationResultsDescribeinvocationresults.md#): DescribeInvocationResults
    -   [../DNA0011860945/EN-US\_TP\_9959.md\#](../intl.en-US/API Reference/Cloud assistant/Stopinvention.md#): StopInvocation
    -   [../DNA0011860945/EN-US\_TP\_9964.md\#](../intl.en-US/API Reference/Cloud assistant/ModifyCommand.md#): ModifyCommand
    -   [DescribeCommands](../intl.en-US/API Reference/Cloud assistant/DescribeCommands.md#): DescribeCommands
    -   [../DNA0011860945/EN-US\_TP\_9960.md\#](../intl.en-US/API Reference/Cloud assistant/DeleteCommand.md#): DeleteCommand

