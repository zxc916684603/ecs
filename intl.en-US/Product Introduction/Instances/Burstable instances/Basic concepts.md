# Basic concepts {#concept_n52_3v2_5db .concept}

Burstable instances \(also called t5 instances\) can deal with unanticipated increase in CPU performance. Each t5 instance provides a baseline level of CPU computing performance and continuously acquires CPU credits at a specified rate based on instance types. A t5 instance consumes CPU credits to meet service requirements once it is started. When the instance runs with performance higher than the baseline CPU computing performance, it consumes more CPU credits to seamlessly increase CPU performance without affecting the instance environment or applications.

t5 instances include [t5 standard instances](reseller.en-US/Product Introduction/Instances/Burstable instances/t5 standard instances.md#) and [t5 unlimited instances](reseller.en-US/Product Introduction/Instances/Burstable instances/t5 unlimited instances.md#).

## Concepts {#section_wc4_lx5_ydb .section}

-   **Baseline CPU computing performance** 

    Each type of t5 instance provides a baseline level of CPU computing performance, which means that each vCPU core of an instance provides a maximum usage under normal workloads. For example, when the ecs.t5-lc1m2.small instance runs under normal workloads, the maximum CPU usage is 10%.

-   **CPU credit** 

    Each t5 instance acquires CPU credits at a fixed rate based on the baseline CPU computing performance. A CPU credit is the unit for measuring computing performance, which is related to the number of vCPU cores, CPU usage, and running time. For example:

    -   One CPU credit = One vCPU core running at 100% usage for 1 minute

    -   One CPU credit = One vCPU core running at 50% usage for 2 minutes

    -   One CPU credit = Two vCPU cores running at 25% usage for 2 minutes

        To support a vCPU core running at 100% usage for an hour, 60 CPU credits are required.

-   **Initial CPU credit** 

    Every time you create a t5 instance, each vCPU core of the instance immediately acquires 30 CPU credits, which are called initial CPU credits. Initial CPU credits are allocated only upon instance creation. Additionally, they are preferentially consumed.

-   **CPU credit acquisition rate** 

    t5 instances acquire CPU credits at 1-minute granularity. The CPU credit acquisition rate indicates CPU credits acquired by a t5 instance per unit time \(minute\). It is determined by the baseline CPU computing performance. The calculation formula is as follows:

    ```
    CPU credit acquisition rate = Baseline CPU computing performance x Number of vCPUs
    ```

    **Example**: Use the ecs.t5-c1m2.xlarge instance as an example. Its average baseline CPU computing performance is 15%, so the CPU credit acquisition rate is 0.6 CPU credit per minute, that is, 36 CPU credits per hour.

-   **CPU credit consumption** 

    After a t5 instance is started, it consumes CPU credits \(first initial CPU credits, then the accumulated CPU credits\). The formula for calculating the consumed CPU credits per minute is as follows:

    ```
    CPU credits consumed per minute = One CPU credit x Actual CPU computing performance
    ```

    **Example**: Use the ecs.t5-lc1m2.small instance as an example. It consumes 0.2 CPU credit when it runs at 20% CPU usage.

-   **Accumulated CPU credit** 

    When the CPU usage of a t5 instance is lower than the baseline CPU computing performance, the instance accumulates CPU credits because the CPU credit consumption rate is lower than the CPU credit acquisition rate. Otherwise, the instance consumes CPU credits. The CPU credit accumulation rate is determined by the difference between the actual CPU load and the baseline performance. It can be calculated using the following formula:

    ```
    CPU credit accumulated per minute = One CPU credit x (Baseline CPU computing performance - Actual CPU computing performance)
    ```

    CPU credits increase when the CPU credit acquisition rate is higher than the CPU credit consumption rate, and vice versa.

    You can view accumulated and consumed CPU credits on the [ECS console](reseller.en-US/Product Introduction/Instances/Burstable instances/Manage t5 instances.md#section_imz_wx5_ydb).


## Impact of instance stop on CPU credits {#section_xt5_fx5_ydb .section}

After you stop a t5 instance through the [ECS console](../../../../reseller.en-US/User Guide/Instances/Start or stop an instance.md#) or the [StopInstance](../../../../reseller.en-US/API Reference/Instances/StopInstance.md#) API, CPU credits change according to the billing method and network type, as shown in the following table.

|Network type|Instance billing method|CPU credit changes after instance stop|
|:-----------|:----------------------|:-------------------------------------|
|Classic network|Subscription or Pay-As-You-Go|The existing CPU credits are valid, and the credit accumulation continues.|
|VPC|Subscription|
|Pay-As-You-Go \(with [No fees for stopped instances \(VPC-Connected\)](../../../../reseller.en-US/Pricing/No fees for stopped instances (VPC-Connected).md#) disabled\)|
|Pay-As-You-Go \(with [No fees for stopped instances \(VPC-Connected\)](../../../../reseller.en-US/Pricing/No fees for stopped instances (VPC-Connected).md#) enabled\)|CPU credits accumulated before instance stop become invalid. The instance acquires initial CPU credits after it is restarted.|

The instance continues to accumulate CPU credits after it is restarted.

If a Pay-As-You-Go instance runs out of balance or a Subscription instance expires, the instance's CPU credits remain valid, but the instance no longer accumulates CPU credits. After you [Reactivate](../../../../reseller.en-US/User Guide/Instances/Reactivate an instance.md#) or [renew](../../../../reseller.en-US/Pricing/Renew instances/Renewal overview.md#) the instance, it automatically continues to accumulate CPU credits.

## Instance type {#section_c55_fx5_ydb .section}

t5 instances use Intel Xeon processors. The following table lists instance types. In this table:

-   **CPU credits/hour** indicates the total CPU credits allocated to all vCPU cores of a t5 instance per hour.
-   **Average baseline CPU computing performance** indicates the average baseline CPU computing performance of each vCPU core of a t5 instance.

|Instance type|vCPU|Initial CPU credits|CPU credits/hour|Average baseline CPU computing performance|Memory \(GiB\)|
|:------------|:---|:------------------|:---------------|:-----------------------------------------|:-------------|
|ecs.t5-lc2m1.nano|1|30|6|10%|0.5|
|ecs.t5-lc1m1.small|1|30|6|10%|1.0|
|ecs.t5-lc1m2.small|1|30|6|10%|2.0|
|ecs.t5-lc1m2.large|2|60|12|10%|4.0|
|ecs.t5-lc1m4.large|2|60|12|10%|8.0|
|ecs.t5-c1m1.large|2|60|18|15%|2.0|
|ecs.t5-c1m2.large|2|60|18|15%|4.0|
|ecs.t5-c1m4.large|2|60|18|15%|8.0|
|ecs.t5-c1m1.xlarge|4|120|36|15%|4.0|
|ecs.t5-c1m2.xlarge|4|120|36|15%|8.0|
|ecs.t5-c1m4.xlarge|4|120|36|15%|16.0|
|ecs.t5-c1m1.2xlarge|8|240|72|15%|8.0|
|ecs.t5-c1m2.2xlarge|8|240|72|15%|16.0|
|ecs.t5-c1m4.2xlarge|8|240|72|15%|32.0|
|ecs.t5-c1m1.4xlarge|16|480|144|15%|16.0|
|ecs.t5-c1m2.4xlarge|16|480|144|15%|32.0|

The following uses the ecs.t5-c1m1.xlarge instance as an example.

-   Each vCPU core provides the average baseline computing performance of 15%. Therefore, the total baseline computing performance of the instance is 60%. Details are as follows:

    -   When the instance uses only one vCPU core, this core provides the baseline computing performance of 60%.
    -   When the instance uses two vCPU cores, each core is allocated the baseline computing performance of 30%.
    -   When the instance uses three vCPU cores, each core is allocated the baseline computing performance of 20%.
    -   When the instance uses all four vCPU cores, each core is allocated the baseline computing performance of 15%.
-   An instance acquires 36 CPU credits per hour, which means that each vCPU core acquires nine CPU credits per hour.


## Billing method {#section_u55_fx5_ydb .section}

t5 instances support both the Pay-As-You-Go and Subscription billing methods. For differences between the billing methods, see [Billing method comparison](../../../../reseller.en-US/Pricing/Billing method comparison.md#).

