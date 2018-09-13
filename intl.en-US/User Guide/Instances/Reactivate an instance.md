# Reactivate an instance {#concept_fm2_sxm_xdb .concept}

For a Pay-As-You-Go instance, in the event of payment failure within 15 days \(T+15\) after the due date \(T\), the instance is stopped due to overdue payment and becomes **Expired**. You must open a ticket to settle the payment and reactivate the instance within 30 days \(T+30\) after the due date \(T\). Otherwise, the instance is released and the data cannot be recovered.

**Note:** If you fail to reactivate the ECS instance within 30 days \(T+30\) after the due date \(T\), the instance is automatically released 30 days after the due date and the data cannot be recovered.

## Prerequisites {#section_vyy_bbn_xdb .section}

The Pay-As-You-Go instance is in the **Expired** status.

Submit a job statement to clear the bill.

## Procedure {#section_qll_q1n_xdb .section}

To reactivate an instance, follow these steps:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home).
2.  In the left-side navigation pane, click **Instances**.
3.  Select a region.
4.  Select the instance to be reactivated, and at the bottom of the instance list, select **More** \> **Reactivate**.
5.  Determine that you reactivate the instance immediately or later at a specified time.

If you choose to reactivate immediately, the selected instance returns to the **Running** status in about 10 minutes.

