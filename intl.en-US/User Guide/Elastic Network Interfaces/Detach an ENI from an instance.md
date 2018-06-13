# Detach an ENI from an instance {#concept_ulq_w3k_zdb .concept}

You can detach a secondary ENI, but not the primary ENI, from an instance.

## Limits {#section_i3d_z3k_zdb .section}

To detach a secondary ENI from an instance, you have the following limits:

-   The secondary ENI must be in the InUse status.
-   The instance must be in the Stopped or Running status.

## Prerequisites {#section_k3d_z3k_zdb .section}

Your ENI [is attached to an instance](intl.en-US/User Guide/Elastic Network Interfaces/Attach an ENI to an instance.md). Before you detach an ENI from an instance, the instance must be in the Stopped or Running status.

## Procedure {#section_l3d_z3k_zdb .section}

To detach a secondary ENI from an instance, follow these steps:

1.  Log on to the [ECS console](https://ecs.console.aliyun.com/?spm=a2c4g.11186623.2.9.FNEORG#/home).
2.  In the left-side navigation pane, select**Networks & Security** \> **Network Interfaces**.
3.  Select a region.
4.  Find an ENI in the InUse status, and in the Actions column, click **Detach**.
5.  In the Detach dialog box, confirm the information, and then click **OK**.

In the Network Interfaces page, refresh the table. When the selected ENI is in the Available status, it is successfully detached from the instance.

## Follow-up operations {#section_n3d_z3k_zdb .section}

After an ENI is detached from an instance, you can perform these operations:

-   [Attaching the ENI to another instance](intl.en-US/User Guide/Elastic Network Interfaces/Attach an ENI to an instance.md).
-   [Deleting the ENI](intl.en-US/User Guide/Elastic Network Interfaces/Delete an ENI.md).
-   [Modifying attributes of the ENI](intl.en-US/User Guide/Elastic Network Interfaces/Modify attributes of an ENI.md).

