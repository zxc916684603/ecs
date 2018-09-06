# Query execution results and status {#concept_jf4_btt_q2b .concept}

There is no difference between running a cloud assistant command on the console and running a command while logged into the instance. In both cases, a command can be run successfully only after all of the command's conditions are satisfied. Cloud assistant commands executed at the same time can provide different command execution results and statuses if the following errors occur: lack of relevant dependencies, network disruptions, command semantic errors, script debugging errors, or abnormal instance statuses. We recommend that you review the command execution results and status after running a command to ensure the target operation has completed properly.

## Prerequisites {#section_nmt_qyt_q2b .section}

The command must be run at least once.

## Check the results of the command execution {#ViewCommandResult .section}

To view command execution result on the ECS Console, you must take the following steps:

1.  Log on to the ECS Console[ECS console](https://ecs.console.aliyun.com/) .
2.  In the left-side navigation bar, select **Cloud Assistant**.
3.  Select a region.
4.  In the **Execution Record** area, search for the execution record of the necessary command execution, and select **View Results** from **Actions**.
5.  In the pop-up window, select an execution record and click ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/17026/15362285198508_en-US.png) to expand the command execution record.

You can also use the ECS API [DescribeInvocationResults](../intl.en-US/API Reference/Cloud assistant/DescribeInvocationResults.md#) to view command results.

## View command execution status {#ViewCommandStatus .section}

To view command execution status in the ECS Console, you must take the following steps:

1.  Log on to the ECS Console [ECS console](https://ecs.console.aliyun.com/) .
2.  In the left-side navigation bar, select **Cloud Assistant**.
3.  Select a region.
4.  In the **Execution Record** area, search for the execution record of the necessary command execution, and then in the **Execution Status** bar view the command execution status.

    ![](http://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/assets/img/17026/15362285198525_en-US.png)


You can also use the ECS API [DescribeInvocations](../intl.en-US/API Reference/Cloud assistant/DescribeInvocations.md#) to view command execution status.

